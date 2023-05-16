2305151641
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# ACL Operations


>[!important]
>ACL's applied to an interface do not apply to traffic which originates from the router itself.
>
# Access Groups

ACLs are applied at the level of interface with the Access-Group command
ACLs can be applied in the inbound or outbound direction
You can have a maximum of one ACL per interface per direction


You can have both an inbound and an outbound ACL on the same interface, but **not** 2 inbound or outbound ACLs

An interface can have no ACL applied, an inbound ACL only, an outbound ACL only, or ACLs in both directions


## Configuration

<img src ='https://i.gyazo.com/e41612743adf3019ad57de292fdc43f3.png'>

## Validation

<img src ='https://i.gyazo.com/b29683842af37ca9498c1b48790b4161.png'>


## Access Control Entry Order

- The access control list is read from the top to the bottom 
- As soon as a rule matches the packet. the rule is applied and not processed any further
```
(config)#access-list 1 deny host 10.10.10.10
(config)#access-list 1 permit 10.10.10.0 0.0.0.255
```
- This will deny 10.10.10.10 but permit the rest of the  10.0/24 network
- Other way around...
```
(config)#access-list 1 permit 10.10.10.0 0.0.0.255
(config)#access-list 1 deny host 10.10.10.10
```
- you can't tell it to deny the host after telling it "yeah, you can go ahead and allow everyone in the 10.0 network"
- then say "nvm dont allow that dude"



## Injecting ACEs (Access Control Entries) in an existing ACL

- ACEs are numbered in increments of 10

<img src= 'https://i.gyazo.com/8e373c41bac6a2845de0647f89e56e5b.png'>

- Which is perfect because now we have a system to identify the order of the ACEs
- We can now inject ACEs into an existing ACL 

<img src = 'https://i.gyazo.com/ebd4197bd966f6ec71020cb67b064a7b.png'>

## Implicit Deny All

- deny any any is implicit (inherent) at the bottom of ACLs
- If an ACL is not applied to the interface all traffic is allowed 

`(config)#access-list 1 permit 10.10.10.0 0.0.0.255`
everything in this subnet would be permitted but there would be a implicit Deny all under it (implied)
`(config)#access-list 1 deny any`



# Explicit Deny All

some orgs put an explicit with the 'other option' `log`
to log illegal traffic
That implicit deny is still beneath
`(config)#access-list 1 permit 10.10.10.0 0.0.0.255`
`(config)#access-list 1 deny any log`

## Explicit Permit All

If you want to counter the implicit deny. put a explicit permit right above it so the below rule is obsolete because of the [[ACL Operations#Access Control Entry Order | Access Control Entry Order]] 

`(config)#access-list 1 permit 10.10.10.0 0.0.0.255`
`(config)#access-list 1 permit any log`






---
# Reference