# Least-Common-Denominator Networking

Leverage DNS and/or Ethane

### Motivation

1. Latency
2. Fault Tolerance

#### Example: Sensor Andrew connected door actuated using a phone

Currently: 
Phone app -> Internet -> SA Server -> Internet -> Door

Can we do: Phone app -> SA Server -> Door if they lie on the same physical subnet (physical subnet: independent branch of network based on physical connection.)

### Problems

1. Who is on my subnet?
2. Best reachable route between 2 devices
3. Auto-redirection of application packets (should the device handle this or the network)
4. Contacting a device directly (F****** NATs!)

#### Why do apps love connecting to the cloud?

### Application-supported redirection

1. Application handshakes with cloud
2. Cloud informs app about directly reachable devices.
3. Application uses direct ID

#### Problems

1. Door changes address

	*Q: How do the server and app identify this and find the new address?*
	A: Door informs server of new address. Server propogates update to interested Apps (PUSH notification?).
	
	*Q: How does door identify itself as the same door? Can we reuse existing naming schemes?*
	A: Possibly use MAC-ID or create new device ID (bad bad idea)
	
2. Door dies
3. Authentication that door is real door in app
4. Authentication that app is real app at door

### Network-supported redirection


### Dealing with commercial networking (getting around BGP)

#### Is this still a problem with IPv6?