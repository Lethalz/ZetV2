2407241609
	Status: #Exam #CCNP
		Tags: [[CCNP 350-401]] [[Networking]]

# Cisco IOS Debug


# Cisco IOS Debug Commands

## My Understanding
[Space for your own notes and understanding of the topic]

## Fundamentals

Debugging in Cisco IOS is a powerful tool for troubleshooting network issues by providing detailed real-time information about various processes and protocols.

- Cause the Router/Switch to generate Syslog messages in response to various network events
- debug messages are displayed/sent wherever debugging (level 7) logging is enabled.
	- `show logging` to confirm
- If connecting via VTY(SSH) you will need to use the `terminal monitor` command to view them.

Key Concepts:
1. Debug commands generate significant output and can impact device performance
2. Debugging should be used judiciously, especially on production networks
3. Conditional debugging allows for more targeted troubleshooting
4. Debug output is sent to all active terminal lines by default
5. One or more conditions must be met for a debug message to be displayed.

Types of Debugging:
1. General debugging: Enables debugging for all instances of a feature
2. Conditional debugging: Allows debugging based on specified conditions

```ad-warning
title: Performance Impact
collapse: closed
icon: exclamation-triangle

Debugging can significantly impact device performance. Use with caution, especially on production networks.

Before Debugging, look at your CPU load with the `show processes cpu` command. Verify that you have ample CPU before debug.

Cisco recommends disabling console logging (`no logging console`) and only enable when needed.

And, disable all debugs when done `undebug all`


```

```ad-hint
title:Study Hack
Use `debug` when study to see things you wouldn't normally, like ospf adjacency forming.

```
## Feynman Method Explanation

Imagine you're trying to figure out why your car isn't running smoothly. You could lift the hood and watch everything happening in the engine - that's like general debugging. It shows you everything, but it's overwhelming and slows down the car.

Now, imagine you could put a special camera just on the fuel injector because you suspect that's the problem. That's like conditional debugging - you're focusing on one specific part to get detailed information without slowing down the whole car as much.

In networking, debugging is like lifting the hood on your network devices. General debugging shows you everything happening, which can be overwhelming and slow down the device. Conditional debugging is like that focused camera, allowing you to see detailed information about specific processes without impacting the entire device as much.

## Relevant Commands

Enable debugging:
```
debug [feature]
```

Disable specific debug:
```
no debug [feature | condition #]
```
or
```
undebug [feature | condition #]
```

Disable all debugging:
```
no debug all
```
or
```
undebug all
```

View active debugs:
```
show debug
```

Example: Debug OSPF adjacencies:
```
debug ip ospf adj
```

Example: Debug IP packets:
```
debug ip packet
```

Conditional Debugging:
```
debug condition [condition]
```

Remove all debug conditions:
```
no debug condition all
```

```ad-tip
title: Using the 'detail' Keyword
collapse: closed
icon: lightbulb

Many debug commands support a 'detail' keyword for more comprehensive output. For example: 
debug ip packet detail
```

## Conditional Debugging Examples

Debug OSPF for a specific interface:
```
debug condition interface GigabitEthernet0/1
debug ip ospf adj
```

Debug IP packets for a specific source IP:
```
debug condition ip 192.168.1.1
debug ip packet
```


```ad-tip
title: Removing debug conditions
collapse: open
The undebug all command disables debugs but does not remove the debug conditions.
	- The conditions will be applied to future debugs
	  
Use the `undebug condition all` or `no debug condition all` to actually remove the conditions for the next debug
	- Can specify `undebug condition [feature]`

```



## Using ACL's to condition Debug Output

![[Pasted image 20240724165230.png]]

```ad-note
title: ACL flexibility 
ACLs are not only used to allow or block traffic but also to obtain/identify other traffic as shown here!


```
## Related RFCs

While there are no specific RFCs for Cisco IOS debugging, understanding the protocols you're debugging is crucial. Some relevant RFCs include:

1. [RFC 2328 - OSPF Version 2](https://datatracker.ietf.org/doc/html/rfc2328)
   - Useful for understanding OSPF behavior when debugging OSPF

2. [RFC 791 - Internet Protocol](https://datatracker.ietf.org/doc/html/rfc791)
   - Provides details on IP packet structure, helpful when debugging IP packets

## Cisco Documentation and Whitepapers

1. [Cisco IOS Debug Command Reference](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/debug/command/db-cr-book.html)
   - Comprehensive reference for all debug commands in Cisco IOS

2. [Troubleshooting and Debugging IP RIP](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13730-ripdb.html)
   - While focused on RIP, provides good examples of using debug commands

3. [How To Use Debug Commands on Cisco IOS](https://www.ciscopress.com/articles/article.asp?p=2999386&seqNum=2)
   - Detailed guide on using debug commands effectively

4. [Cisco Nexus 7000 Series NX-OS Troubleshooting Guide](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/sw/6_x/nx-os/troubleshooting/guide/cisco_nexus7000_troubleshooting_guide/TS_Debug.html)
   - While for NX-OS, provides good practices applicable to IOS as well

```ad-info
title: Logging Best Practice
collapse: closed
icon: book

When using debug commands, it's often helpful to enable logging to a buffer or external syslog server to capture output for later analysis.
```






## Conclusion

Debugging in Cisco IOS is a powerful but potentially disruptive tool. General debugging provides comprehensive information but can significantly impact device performance. Conditional debugging offers a more targeted approach, allowing for specific troubleshooting with less performance impact. Always use debugging judiciously, especially in production environments, and be prepared to quickly disable debugging if it causes performance issues.

---
# Reference
Syslog Levels

|     |               |                                                                                                                                                                                                            |
| --- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0   | Emergency     | A "panic" condition affecting multiple applications, servers, or sites. System is unusable. Notify all technical staff on call.                                                                            |
| 1   | Alert         | A condition requiring immediate correction, for example, the loss of a backup ISP connection. Notify staff who can fix the problem.                                                                        |
| 2   | Critical      | A condition requiring immediate correction or indicating a failure in a primary system, for example, a loss of a primary ISP connection. Fix CRITICAL issues before ALERT-level problems.                  |
| 3   | Error         | Non-urgent failures. Notify developers or administrators as errors must be resolved within a given time.                                                                                                   |
| 4   | Warning       | Warning messages are not errors, but they indicate that an error will occur if required action is not taken. An example is a file system that is 85% full. Each item must be resolved within a given time. |
| 5   | Notice        | Events that are unusual but are not error conditions. These items might be summarized in an email to developers or administrators to spot potential problems. No immediate action is required.             |
| 6   | Informational | Normal operational messages. These may be harvested for network maintenance functions like reporting and throughput measurement. No action is required.                                                    |
| 7   | Debug         | Information useful to developers for debugging an application. This information is not useful during operations.                                                                                           |
|     |               |                                                                                                                                                                                                            |
|     |               |                                                                                                                                                                                                            |
https://www.youtube.com/watch?v=Zyv_P6SjWQY&list=PLxbwE86jKRgOb2uny1CYEzyRy_mc-lE39&index=25