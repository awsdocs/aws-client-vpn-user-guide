# Common problems<a name="common-troubleshooting"></a>

The following are common problems that you might have when using a client to connect to a Client VPN endpoint\.

## TLS key negotiation failed<a name="common-troubleshooting-tls"></a>

**Problem**  
The TLS negotiation fails with the following error\.

```
TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
TLS Error: TLS handshake failed
```

**Cause**  
The cause of this problem might be one of the following:
+ Firewall rules are blocking UDP or TCP traffic\.
+ You're using the incorrect client key and certificate in your configuration \(\.ovpn\) file\.
+ The client certificate revocation list \(CRL\) has expired\. 

**Solution**  
Check to see if the firewall rules on your computer are blocking inbound or outbound TCP or UDP traffic on ports 443 or 1194\. Ask your Client VPN administrator to verify the following information:
+ That the firewall rules for the Client VPN endpoint do not block TCP or UDP traffic on ports 443 or 1194\.
+ That the configuration file contains the correct client key and certificate\. For more information, see [Export Client Configuration](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-export) in the *AWS Client VPN Administrator Guide*\.
+ That the CRL is still valid\. For more information, see [Clients Unable to Connect to a Client VPN Endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/troubleshooting.html#client-cannot-connect) in the *AWS Client VPN Administrator Guide*\.