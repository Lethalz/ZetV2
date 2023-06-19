2306182134
	Status: #idea 
		Tags: [[CCNA]] [[Networking]]

# STP reddit explanation

Here are your three critical facts of Spanning-Tree:

1. STP is evil.
    

- STP wants to cut off half of your bandwidth.
    

1. STP is necessary.
    

- STP exists to protect your network from loops.
    
- Being protected from loops is worth the cost of dealing with evil.
    
- Stability & Predictability is more important than speed.
    

1. Disabling STP is almost always the wrong solution.
    

- Leaving STP enabled, but not letting it flow across specific interfaces can be an acceptable solution.
    

---

Always try to build triangles with your switches.  
Try not to build squares.

Switch A is your STP root bridge.  
Switch B is your alternate root.  
Switch C should, as part of a good design, be directly, physically connected to A and B.

Connecting C to A and Switch D to B and then connecting C to D creates a square and not a triangle.  
This can work. This will work. But this is a less desirable configuration, and should be avoided where possible.

---

Valid STP priorities are 0 to 65536.  
Very few switches will let you use value "0".  
Most, if not all will let you use 4096.  
You will be tempted to make your root bridge 4096. Don't.

Keep 4096 in your pocket for a rainy day. Just in case.  
Someday you might need to move your root to a new switch as part of an upgrade process.  
Having 4096 available will make that process easier.

So set your root to 8192 for all VLANs, like this:

```
spanning-tree mode rapid-pvst  
spanning-tree extend system-id  
spanning-tree vlan 1-4094 priority 8192  
```

You want your intended alternate root to be the next lowest value, which is 8192+4096=12288

```
spanning-tree mode rapid-pvst  
spanning-tree extend system-id  
spanning-tree vlan 1-4094 priority 12288  
```

Now you want to set every single switch that is directly, physically connected (using a triangle) to your A and B to the next lowest value (12288+4096=16384).

```
spanning-tree mode rapid-pvst  
spanning-tree extend system-id  
spanning-tree vlan 1-4094 priority 16384  
```

Now you want every single switch that is connected to one of your 16384 devices to use the next lowest value (16384+4096=20480)

```
spanning-tree mode rapid-pvst  
spanning-tree extend system-id  
spanning-tree vlan 1-4094 priority 20480  
```

Your goal here is to try to keep YOUR switch topology set to lower STP values than the default out-of-box value which is 32768.  
This way, if (when?) some knucklehead pulls a brand new STP-enabled device out of the box and plugs it into your network, your entire network should have a lower STP priority, thus preventing any kind of a topology change.

Your next goal is to ENFORCE a PREDICTABLE failure & reconvergence of your topology in the event one or more switches fail.

If one of your 16384 devices fail, there is a very clear path for all of those 20480 devices to find their way to the root.  
If the root is 8192, but the entire rest of the network is 32768 (default) the reconvergence takes longer.

---

BPDUGuard is love. BPDUGuard is life. BPDUGuard is not a lie - it is cake.

BPDUGuard is an edge security feature that defends the edge of your network from all forms of foreign, unplanned Spanning-Tree change.

Any STP implementation that is not using BPDUGuard at the user-edge is, IMO, wrong.

```
spanning-tree portfast default  
spanning-tree portfast bpduguard default  
```

BPDUGuard will defend your network from the broadcast-storms that occur when a user plugs both ports of a non-STP-aware Linksys switch into your managed LAN. The dumb Linksys doesn't understand STP. He will not participate in any loop-detection. But he will pass your LAN device's BPDU discovery frames right on through just like a standard broadcast, and they will be detected by your same managed LAN device. Your switch will ask itself, "Why am I suddenly able to hear myself talking?" and the immediate response will be to `err-disable`shutdown the switchport(s) involved in the loop. This frustrates the user who can't figure out why their Linksys switch isn't working. But it also defends the rest of your network from the broadcast-storm event.

---

Rapid Per VLAN Spanning-Tree (RPVST) is (IMO / IME) the prefered STP mode up to around 250 or so VLANs.  
Once you exceed that level, it's time for Multiple Spanning-Tree (MST).
---
# Reference
[About STP : r/networking](https://www.reddit.com/r/networking/comments/7rguqi/comment/dswzzen/)