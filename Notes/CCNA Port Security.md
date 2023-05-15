2305151320
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# CCNA Port Security


# Port Security

**Port Security** enables an admin to specifiy which MAC address or addresses can send traffic in to an individual switch port.
	- Can be used to lock a port down to particular host or hosts

It is easy to spoof a MAC address 

However can also congiure a switch port to allow only a specified number or source MAC addresses to send traffic in to the port

This allows us to prevent users to add WAPs or other shared devices that would add multiple users to a single port


## Configuration

``` 
(config)#int F0/1
(config)#switchport port-security

```

- Configured at the interface level
- By default it only allows 1 MAC address
- If more than one host tries to transmit the port will 'shut down'
- The current mac address can be discconnected and changed.

## Verification

```
show port-security interface f0/2
```


<img src = 'https://i.gyazo.com/8ba5565b7aca7ddd240604a29333c9b7.png'>



# Violation actions

1. Shutdown(Default) - the interface is palced into the error-disabled state, blocking all traffic
2. Protect - traffic from unauthorised addresses is dropped, traffic from allowed is forwarded
3. Restrict - traffic from unautorised address is dropped, logged and the ciolation counter incremented, traddic from allowed address is forwarded


# Configuration

```
(config)#int f0/2
(config-if)#switchport port-security violation protect
(config-if)#switchport port-security violation restrict
```



## Error-Disabled
- Port is down
- Remove the mac address
- then do a shutdown then no shutdown
- specifiy a time interval (automaticcaly)

Example of time interval:

```
(config)# errdisable recovery cause psecure-violation
(config)# errdisable recovery interval 600
```



# Locking ports to Hosts with Port Security


- Maximum number of MAC addresses allowed is 1 by default
- But what if there's a daisy-chained phone (phone with a Pc in the back)

```
(config)#interface f0/2
(config-if)#switchport port-security maximum 2
```

Verification:

`show port-security int f0/2`



- You can staic configure the MAC address on port

```
interface f0/10
switchport port-security
switchport port-security mac-address 1111.2222.3333
switchport port-security maximum 1
```



## Scalable 'sticky' MAC

<img src = 'https://i.gyazo.com/fd4f47e5039dc586785de61fb334bddf.png'>

## Verification 

`show port-security address`
`show port-security`













---
# Reference