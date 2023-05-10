<img src = 'https://i.gyazo.com/858756f1723ba1f263e64333e064acfd.png'>

The first command in this list is to exclude some ip addresses for static allocation.

Then we create the pool of IP addresses DHCP can pull and give it a name '10.10.10.0_Clients' **This is just a name not an actual IP address or CMD**

It takes us into DHCP config mode and this is where we specifiy the network address range with the `network 10.10.10.0 255.255.255.0`

Then we set the default-router and then the DHCP Name server

## Verification

`R1#show ip dhcp pool

To see the ip address already given out and who they were given to we can use `show ip dhcp binding`


`