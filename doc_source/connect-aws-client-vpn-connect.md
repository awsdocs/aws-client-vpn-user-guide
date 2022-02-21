# Connect using an AWS provided client<a name="connect-aws-client-vpn-connect"></a>

You can connect to a Client VPN endpoint using the AWS provided client\. The AWS provided client is supported on Windows, macOS, Ubuntu 18\.04 LTS and Ubuntu 20\.04 LTS\.

**Topics**
+ [AWS Client VPN for Windows](client-vpn-connect-windows.md)
+ [AWS Client VPN for macOS](client-vpn-connect-macos.md)
+ [AWS Client VPN for Linux](client-vpn-connect-linux.md)

**OpenVPN directives**

The AWS provided client supports the following OpenVPN directives:
+ auth\-user\-pass
+ ca
+ cert
+ cipher
+ client
+ connect\-retry
+ cryptoapicert \(Windows only\)
+ dev
+ key
+ nobind
+ persist\-key
+ persist\-tun
+ proto
+ remote
+ remote\-cert\-tls
+ remote\-random\-hostname
+ reneg\-sec
+ resolv\-retry
+ static\-challenge
+ tun\-mtu
+ tun\-mtu\-extra
+ verb