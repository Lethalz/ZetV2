2412111011
	Status: #idea 
		Tags: [[Wireless]] [[WIfi]]


# WiFi Network Architecture Guide

## Core Components Overview
There are three fundamental components in a WiFi network architecture:
1. Clients (Stations)
2. Access Points
3. Controllers

## 1. Clients (Stations)

### Primary Function
- Serve as endpoints for data communication
- Cannot pass WiFi data through to other clients

### Client Differentiating Factors

#### Power Source Options
- Battery-powered devices
- AC-powered devices

#### Antenna Configuration
- Multiple antenna support
- Correlation between antenna quantity and WiFi speed
- Note: More antennas generally result in improved performance

## 2. Access Points (APs)

### Types
1. Lightweight APs
   - Centrally managed
   - Requires controller integration
   
2. Autonomous APs
   - Individually managed
   - Standalone configuration

### AP Differentiating Factors

#### Radio Capabilities
- Transceiver types
  - 2.4 GHz support
  - 5 GHz support
- Number of radios

#### Physical Characteristics
- Indoor vs. Outdoor design
- Antenna quantities and types
- Enhanced features (proprietary)

## 3. Controllers (WLC)

### Primary Functions
- Centralized management of access points
- Client access control
- Network policy enforcement

### Controller Differentiating Factors

#### Capacity and Scale
- Maximum supported WiFi clients
- AP management capacity

#### Deployment Options
- Physical appliance
- Cloud-based solution

#### Interface Options
- Types of uplink interfaces
- Quantity of supported connections

### Features
- Available management capabilities
- Security controls
- Performance optimization tools

## Best Practices
1. Match client density with appropriate AP coverage
2. Consider environmental factors when choosing indoor/outdoor APs
3. Scale controller capacity to network size
4. Plan for future expansion in initial design

## Reference Documentation
- [802.11 Standards Overview](https://standards.ieee.org/ieee/802.11/7028/)
- [Cisco Wireless Controller Configuration Guide](https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/config-guide/b_wl_16_10_cg.html)
---
# Reference