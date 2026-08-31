**Windows Server Network Configuration Validation**

Windows Server networking lab configuring static IPv4 and DNS settings, then validating local, external, route, and DNS connectivity.

Windows Server 2016 and Windows Server 2022 networking are important parts of maintaining reliable business operations and enterprise IT. Servers often support applications, authentication, DNS, and other services that employees and systems depend on. Because of that, network settings and configuration—such as the IP address, subnet mask, default gateway, and DNS settings—need to be accurate and validated. IT departments perform this work so servers can communicate consistently with local and external resources.

This lab demonstrates a structured Windows Server network configuration and validation process. I configured static IPv4 and DNS settings, reviewed the active network adapter, verified the applied configuration, and tested gateway connectivity, external connectivity, route visibility, and DNS resolution. In business and enterprise environments, this type of validation and confirmation helps reduce configuration errors, supports uptime and reliability, and gives technicians measurable evidence when validating or troubleshooting server connectivity.

**Objectives**

- Configure a static IPv4 address, subnet mask, default gateway, and DNS settings on Windows Server.
- Review the network adapter and confirm the expected interface configuration.
- Validate the active network configuration using `ipconfig /all`.
- Test local gateway and external network connectivity using ping and tracert.
- Verify DNS name resolution using `nslookup` and compare the result with the configured DNS settings.

**Static IP Configuration**

- A manual IPv4 address of `192.168.1.10` is assigned to the Windows Server.
- The subnet mask is set to `255.255.255.0`, defining the local IPv4 network.
- The default gateway is configured as `192.168.1.1` for communication beyond the local subnet.

![Static IP Configuration](images/01Edit%20IP%20settings.png)

**DNS Configuration**

- The server is configured with a preferred IPv4 DNS address of `127.0.0.1`.
- `127.0.0.1` is the IPv4 loopback address, directing DNS requests to the local server.
- The configuration supports local DNS resolution through the DNS service running on the Windows Server.

![DNS Configuration](images/02Edit%20DNS%20settings.png)

**Network Adapter Review**

- Windows confirms the IPv4 DNS server as `127.0.0.1`.
- The virtual network adapter reports a link speed of `1000/1000 Mbps`.
- Adapter properties provide a graphical review of the active network configuration.

![Network Adapter Review](images/03Network%20adapter%20details.png)

**Configuration Validation**

- `ipconfig /all` confirms the active IPv4 address as `192.168.1.10` with a `255.255.255.0` subnet mask.
- The configured default gateway is confirmed as `192.168.1.1`.
- DNS configuration includes the local loopback addresses `::1` and `127.0.0.1`, validating the applied server settings.

![Configuration Validation](images/04Command%20prompt%20ipconfig%20all.png)

**Gateway Connectivity**

- `ping 192.168.1.1` tests communication between the Windows Server and its default gateway.
- All four ICMP requests receive successful replies.
- The test reports `0%` packet loss, confirming local gateway connectivity.

![Gateway Connectivity](images/05Command%20prompt%20ping.png)

**External Connectivity**

- `ping google.com` resolves the hostname to an external IP address and tests communication with the destination.
- All four ICMP requests receive successful replies.
- The test reports `0%` packet loss, confirming successful external connectivity during the test.

![External Connectivity](images/06Command%20prompt%20ping%20google.png)

**Route Visibility**

- `tracert google.com` displays the network path between the Windows Server and the external destination.
- The first hop is the local default gateway at `192.168.1.1`.
- The trace completes successfully, showing traffic progressing through multiple network hops to the destination.

![Route Visibility](images/07tracert%20google.png)

**DNS Resolution**

- `nslookup google.com` directly tests DNS name resolution from the Windows Server.
- The query experiences an initial DNS timeout while querying the IPv6 loopback address `::1`.
- DNS ultimately returns a non-authoritative answer with IPv4 and IPv6 addresses for `google.com`, confirming successful resolution.

![DNS Resolution](images/08nslookup%20google.png)

**Lessons Learned**
- Windows Server networking should be configured and then validated to confirm that the intended settings are actually active.
- Static IPv4, subnet mask, default gateway, and DNS settings each play a different role in reliable server communication.
- `ipconfig /all` provides a useful command-line method for confirming the active network configuration after changes are made.
- `ping`, `tracert`, and `nslookup` answer different troubleshooting questions and help isolate connectivity and name-resolution issues.
- A structured validation process gives technicians measurable evidence before deciding whether additional troubleshooting or escalation is needed.

**Summary**

My lab demonstrates a structured Windows Server network configuration and validation process. I configured static IPv4 and DNS settings, reviewed the network adapter, and confirmed the applied configuration. I then tested gateway connectivity, external connectivity, route visibility, and DNS resolution. The documented results show that the server was able to communicate with the local gateway, reach external resources, follow a valid network path, and resolve hostnames through DNS.

The objectives I set out for this lab were achieved through configuration, command-line validation, and connectivity testing. In business and enterprise environments, this type of methodical validation process helps support server uptime, reliability, and consistent communication between systems. It also gives IT departments clear and measurable evidence when confirming changes, identifying network issues, and determining whether additional troubleshooting or escalation is needed.

**Navigation**

[`Back to GitHub Profile`](https://www.github.com/cbueker-it)
