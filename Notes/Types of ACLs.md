2305151536
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Types of ACLs


![[f1352d922848e5f65c91aceb830ca54f.png]]
**Range:**
- Standard ACL Range : 1-99
- Extended ACL RangeL: 100-199

**ACL improved ranges:**
Standard: 1-99,1300-1999
Extended: 100-199,2000-2699

**Standard ACLs  

With these types of ACL, an administrator can permit or deny packets based on their **source IP address ONLY**. 
These ACLs **do not check** the packets for **any other criteria** and therefore the destination is not usually checked.
Example:
<img src = 'https://i.gyazo.com/9151f2aa775796cf31f1c6f9dc47f2ba.png'>

The default wildcard mask for a standard ACL is 0.0.0.0 meaning an individual host address

>[!note]
>Do not forget to enter the wildcard when specifying an IP subnet. or it will default to a /32



**Extended ACLs  (more granular)**

Extended Access Control Lists check the traffic against several criteria that has been set by the administrator. With these ACLs, you have more control over the traffic that you want to filter. Some of the criteria may include:


Example:
<img src = 'https://i.gyazo.com/b5ac72e4eb9fe8a2165dd706ee7fe7c4.png'>

There is no Defualt wildcard mask for an extended ACL



**Named ACLs**

You can reference ACLs by number or by a name
Named ACLs begin with the command `ip access-list` instead of `access-list`

![[b9a16751b4d902c78aa0fb44e204719d.png]]

<img src = 'https://i.gyazo.com/b6b7c6842ea55930815475116dde6381.png'>


>[!notice] 
>It gives it ,its own prompt like configuring an interface.
>

---
# Reference