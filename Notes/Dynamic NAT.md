2305161443
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Dynamic NAT

Unlike with static NAT, where you had to manually define a static mapping between a private and public address, **dynamic NAT** does the mapping of a local address to a global address happens dynamically. This means that the router dynamically picks an address from the global address pool that is not currently assigned. The dynamic entry stays in the NAT translations table as long as the traffic is exchanged. The entry times out after a period of inactivity and the global IP address can be used for new translations.

>[!note] 
>You would need 30 public IPs for 30 hosts, If a 31st host tries to communicate outside it will fail because there are no more ips to be translated, this is where [[PAT]] comes in
>

This is used when you are setting up NAT for hosts , because they normally do not need to be pinged directly from the outside like a web-sever.

With dynamic NAT, you need to specify two sets of addresses on your Cisco router:

-   the inside addresses that will be translated
-   a pool of global addresses

To configure dynamic NAT, the following steps are required:

1. configure the router’s inside interface using the _ip nat inside_ command  
2. configure the router’s outside interface using the _ip nat outside_ command  
3. configure an ACL that has a list of the inside source addresses that will be translated  
4. configure a pool of global IP addresses using the _ip nat pool NAME FIRST_IP_ADDRESS LAST_IP_ADDRESS netmask SUBNET_MASK_ command  
5. enable dynamic NAT with the _ip nat inside source list ACL_NUMBER pool NAME_ global configuration command

Consider the following example:

[![Dynamic NAT example](https://study-ccna.com/wp-content/uploads/2016/01/dynamic_nat_process.jpg)](https://study-ccna.com/wp-content/uploads/2016/01/dynamic_nat_process.jpg)

Host A requests a web resource from a internet server S1. Host A uses its private IP address when sending the request to router R1. Router R1 receives the request, changes the private IP address to one of the available global addresses in the pool and sends the request to S1. S1 responds to R1. R1 receives the response, looks up in its NAT table and changes the destination IP address to the private IP address of Host A.

# Configuration

1. First we need to configure the router’s inside and outside NAT interfaces:
```

R1(config)#int f0/0
R1(config-if)#ip nat inside
R1(config-if)#int f0/1
R1(config-if)#ip nat outside
```

2. We need to configure the pool of global (public) IP addresses available on the outside interface:

`R1(config)#ip nat pool STUDY-CCNA_POOL 155.4.12.1 155.4.12.3 netmask 255.255.255.0`

The pool configured above consists of 3 addresses: 155.4.12.1, 155.4.12.2, and 155.4.12.3.

3. Create an access list which references the internal IP addresses we want to translate

`R1(config)#access-list 1 permit 10.0.0.0 0.0.0.255`

4. Lastly, we need to enable dynamic NAT:

`R1(config)#ip nat inside source list 1 pool STUDY-CCNA_POOL`

The command above tells the router to translate all addresses specified in the _access list 1_ to the pool of global addresses named _MY POOL_.

You can list all NAT translations using the _show ip nat translations_ command.

Firstly, Do a `debug ip nat` on the main router

Generate some traffic **from the PC to the server** :

`C:\>ping 155.4.12.5`
```

Pinging 155.4.12.5 with 32 bytes of data:

Reply from 155.4.12.5: bytes=32 time<1ms TTL=127
Reply from 155.4.12.5: bytes=32 time=3ms TTL=127
Reply from 155.4.12.5: bytes=32 time=1ms TTL=127
Reply from 155.4.12.5: bytes=32 time<1ms TTL=127


Ping statistics for 155.4.12.5:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 3ms, Average = 1ms
```
Then enter the `show ip nat translations` command quickly enough before the translation has timed out:
```

R1#show ip nat translations
Pro  Inside global     Inside local       Outside local      Outside global
icmp 155.4.12.1:16     10.0.0.100:16      155.4.12.5:16      155.4.12.5:16
```

In the output above you can see that the translation has been made between the Host A’s private IP address (_Inside local, 10.0.0.100_) to the first available public IP address from the pool (_Inside global, 155.4.12.1_) and it is connecting to the server on the outside (_Outside local and Outside global, 155.4.12.5_) .

>[!Note]
You can remove all NAT translations from the table by using the _clear ip nat translation  add a star at the end to delete all dynamic translations command.

---
# Reference