# Linux troubleshooting<a name="linux-troubleshooting"></a>

The following sections contain information about logging, and about problems that you might have when using Linux\-based clients\. Please ensure that you are running the latest version of these clients\. 

**Topics**
+ [AWS provided client](#aws-provided-client)
+ [OpenVPN \(command line\)](#open-vpn-command-line)
+ [OpenVPN through Network Manager \(GUI\)](#open-vpn-network-manager-gui)

## AWS provided client<a name="aws-provided-client"></a>

The AWS provided client stores log files and configuration files in the following location on your system:

```
/home/username/.config/AWSVPNClient/
```

The AWS provided client daemon process stores log files in the following location on your system:

```
/var/log/aws-vpn-client/username/
```

**Problem**  
Under some circumstances after a VPN connection is established, DNS queries will still go to the default system nameserver, instead of the nameservers that are configured for the ClientVPN endpoint\.

**Cause**  
The AWS VPN Client interacts with **systemd\-resolved**, a service available on Linux systems, which serves as a central piece of DNS management\. It is used to configure DNS servers that are pushed from the ClientVPN endpoint\. The problem occurs because **systemd\-resolved** doesn't set the highest priority to DNS servers that are provided by the ClientVPN endpoint\. Instead, it appends the servers to the existing list of DNS servers that are configured on the local system\. As a result, the original DNS servers might still have the highest priority, and therefore be used to resolve DNS queries\. 

**Solution**

1. Add the following directive in the first line of the OpenVPN config file, to make sure that all DNS queries are sent into the VPN tunnel\.

   ```
   dhcp-option DOMAIN-ROUTE .
   ```

1. Use the stub resolver provided by **systemd\-resolved**\. To do this, symlink `/etc/resolv.conf` to `/run/systemd/resolve/stub-resolv.conf` by running the following command on the system\.

   ```
   sudo ln -sf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
   ```

1. \(Optional\) If you do not want **systemd\-resolved** to proxy DNS queries, and instead would like the queries to be sent to the real DNS nameservers directly, symlink `/etc/resolv.conf` to `/run/systemd/resolve/resolv.conf` instead\.

   ```
   sudo ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
   ```

   You might want to do this procedure in order to bypass the **systemd\-resolved** configuration, for example for DNS answer caching, per\-interface DNS configuration, DNSSec enforcement, and so on\. This option is especially useful when you have a need to override a public DNS record with a private record when connected to VPN\. For example, you might have a private DNS resolver in your private VPC with a record for www\.example\.com, which resolves to a private IP\. This option could be used to override the public record of www\.example\.com, which resolves to a public IP\.

## OpenVPN \(command line\)<a name="open-vpn-command-line"></a>

**Problem**  
The connection does not function correctly because DNS resolution is not working\.

**Cause**  
The DNS server is not configured on the Client VPN endpoint, or it is not being honored by the client software\.

**Solution**  
Use the following steps to check that the DNS server is configured and working correctly\.

1. Ensure that a DNS server entry is present in the logs\. In the following example, the DNS server `192.168.0.2` \(configured in the Client VPN endpoint\) is returned in the last line\.

   ```
   Mon Apr 15 21:26:55 2019 us=274574 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
   WRRMon Apr 15 21:26:55 2019 us=276082 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 192.168.0.2,route-gateway 10.0.0.97,topology subnet,ping 1,ping-restart 20,auth-token,ifconfig 10.0.0.98 255.255.255.224,peer-id 0
   ```

   If there is no DNS server specified, ask your Client VPN administrator to modify the Client VPN endpoint and ensure that a DNS server \(for example, the VPC DNS server\) has been specified for the Client VPN endpoint\. For more information, see [Client VPN Endpoints](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html) in the *AWS Client VPN Administrator Guide*\.

1. Ensure that the `resolvconf` package is installed by running the following command\.

   ```
   sudo apt list resolvconf
   ```

   The output should return the following\.

   ```
   Listing... Done
   resolvconf/bionic-updates,now 1.79ubuntu10.18.04.3 all [installed]
   ```

   If it's not installed, install it using the following command\.

   ```
   sudo apt install resolvconf
   ```

1. Open the Client VPN configuration file \(the \.ovpn file\) in a text editor and add the following lines\.

   ```
   script-security 2
   up /etc/openvpn/update-resolv-conf
   down /etc/openvpn/update-resolv-conf
   ```

   Check the logs to verify that the `resolvconf` script has been invoked\. The logs should contain a line similar to the following\.

   ```
   Mon Apr 15 21:33:52 2019 us=795388 /etc/openvpn/update-resolv-conf tun0 1500 1552 10.0.0.98 255.255.255.224 init
   dhcp-option DNS 192.168.0.2
   ```

## OpenVPN through Network Manager \(GUI\)<a name="open-vpn-network-manager-gui"></a>

**Problem**  
When using the Network Manager OpenVPN client, the connection fails with the following error\.

```
Apr 15 17:11:07  OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on Sep  5 2018
Apr 15 17:11:07  library versions: OpenSSL 1.1.0g  2 Nov 2017, LZO 2.08
Apr 15 17:11:07  RESOLVE: Cannot resolve host address: cvpn-endpoint-1234.prod.clientvpn.us-east-1.amazonaws.com:443 (Name or service not known)
Apr 15 17:11:07  RESOLVE: Cannot resolve host
Apr 15 17:11:07  Could not determine IPv4/IPv6 protocol
```

**Cause**  
The `remote-random-hostname` flag is not honored, and the client cannot connect using the `network-manager-gnome` package\.

**Solution**  
See the solution for [Unable to Resolve Client VPN Endpoint DNS Name](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/troubleshooting.html#resolve-host-name) in the *AWS Client VPN Administrator Guide*\.
