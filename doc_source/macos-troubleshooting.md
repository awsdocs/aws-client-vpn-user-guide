# macOS troubleshooting<a name="macos-troubleshooting"></a>

The following sections contain information about logging and problems that you might have when using macOS clients\. Please ensure that you are running the latest version of these clients\. 

**Topics**
+ [AWS provided client](#macos-troubleshooting-client-vpn-connect)
+ [Tunnelblick](#macos-troubleshooting-tunnelblick)
+ [OpenVPN](#macos-troubleshooting-openvpn)

## AWS provided client<a name="macos-troubleshooting-client-vpn-connect"></a>

The AWS provided client creates event logs and stores them in the following location on your computer\.

```
/Users/username/.config/AWSVPNClient/logs
```

The following types of logs are available:
+ **Application logs**: Contain information about the application\. These logs are prefixed with 'aws\_vpn\_client\_'\.
+ **OpenVPN logs**: Contain information about OpenVPN processes\. These logs are prefixed with 'ovpn\_aws\_vpn\_client\_'\.

The AWS provided client uses the client daemon to perform root operations\. The daemon logs are stored in the following locations on your computer\.

```
/tmp/AcvcHelperErrLog.txt
/tmp/AcvcHelperOutLog.txt
```

The AWS provided client stores the configuration files in the following location on your computer\.

```
/Users/username/.config/AWSVPNClient/OpenVpnConfigs
```

**Topics**
+ [Client cannot connect](#macos-troubleshooting-client-vpn-cannot-connect)
+ [Client is stuck in a reconnecting state](#macos-troubleshooting-client-vpn-stuck)
+ [Client cannot create profile](#macos-troubleshooting-client-vpn-cannot-create-profile)

### Client cannot connect<a name="macos-troubleshooting-client-vpn-cannot-connect"></a>

**Problem**  
The AWS provided client cannot connect to the Client VPN endpoint\.

**Cause**  
The cause of this problem might be one of the following:
+ Another OpenVPN process is already running on your computer, which prevents the client from connecting\.
+ Your configuration \(\.ovpn\) file is not valid\.

**Solution**  
Check to see if there are other OpenVPN applications running on your computer\. If there are, stop or quit these processes and try connecting to the Client VPN endpoint again\. Check the OpenVPN logs for errors, and ask your Client VPN administrator to verify the following information:
+ That the configuration file contains the correct client key and certificate\. For more information, see [Export Client Configuration](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-export) in the *AWS Client VPN Administrator Guide*\.
+ That the CRL is still valid\. For more information, see [Clients Unable to Connect to a Client VPN Endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/troubleshooting.html#client-cannot-connect) in the *AWS Client VPN Administrator Guide*\.

### Client is stuck in a reconnecting state<a name="macos-troubleshooting-client-vpn-stuck"></a>

**Problem**  
The AWS provided client is trying to connect to the Client VPN endpoint, but is stuck in a reconnecting state\.

**Cause**  
The cause of this problem might be one of the following:
+ Your computer is not connected to the internet\.
+ The DNS hostname does not resolve to an IP address\.
+ An OpenVPN process is indefinitely trying to connect to the endpoint\.
+ The Certificate Revocation List (CRL) which was configured on that Client VPN endpoint expired.

**Solution**  
1. Verify that your computer is connected to the internet\. 
2. Ask your Client VPN administrator to verify that the `remote` directive in the configuration file resolves to a valid IP address\. 
3. You can also disconnect the VPN session by choosing **Disconnect** in the AWS VPN Client window, and try connecting again\.
4. Check the [CrlDaysToExpiry](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/monitoring-cloudwatch.html) metric in CloudWatch. If this is your case generate a new CRL from the same CA that was used to generate the certificates for all Clients and import it to the Client VPN endpoint.

### Client cannot create profile<a name="macos-troubleshooting-client-vpn-cannot-create-profile"></a>

**Problem**  
You get the following error when you try to create a profile using the AWS provided client\.

```
The config should have either cert and key or auth-user-pass specified.
```

**Cause**  
If the Client VPN endpoint uses mutual authentication, the configuration \(\.ovpn\) file does not contain the client certificate and key\.

**Solution**  
Ensure that your Client VPN administrator adds the client certificate and key to the configuration file\. For more information, see [Export Client Configuration](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-export) in the *AWS Client VPN Administrator Guide*\.

## Tunnelblick<a name="macos-troubleshooting-tunnelblick"></a>

The following troubleshooting information was tested on version 3\.7\.8 \(build 5180\) of the Tunnelblick software on macOS High Sierra 10\.13\.6\.

The configuration file for private configurations is stored in the following location on your computer\.

```
/Users/username/Library/Application Support/Tunnelblick/Configurations
```

The configuration file for shared configurations is stored in the following location on your computer\.

```
/Library/Application Support/Tunnelblick/Shared
```

The connection logs are stored in the following location on your computer\.

```
/Library/Application Support/Tunnelblick/Logs
```

To increase the log verbosity, open the Tunnelblick application, choose **Settings**, and adjust the value for **VPN log level**\.

### Cipher algorithm 'AES\-256\-GCM' not found<a name="tunnelblick-cipher"></a>

**Problem**  
The connection fails and returns the following error in the logs\.

```
2019-04-11 09:37:14 Cipher algorithm 'AES-256-GCM' not found
2019-04-11 09:37:14 Exiting due to fatal error
```

**Cause**  
The application is using an OpenVPN version that doesn't support cipher algorithm AES\-256\-GCM\.

**Solution**  
Choose a compatible OpenVPN version by doing the following:

1. Open the Tunnelblick application\.

1. Choose **Settings**\.

1. For **OpenVPN version**, choose **2\.4\.6 \- OpenSSL version is v1\.0\.2q**\.

### Connection stops responding and resets<a name="tunnelblick-connection-reset"></a>

**Problem**  
The connection fails and returns the following error in the logs\.

```
MANAGEMENT: >STATE:1559117927,WAIT,,,,,,
MANAGEMENT: >STATE:1559117928,AUTH,,,,,,
TLS: Initial packet from [AF_INET]3.217.107.5:443, sid=df19e70f a992cda3
VERIFY OK: depth=1, CN=server-certificate
VERIFY KU OK
Validating certificate extended key usage
Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server       Authentication
VERIFY EKU OK
VERIFY OK: depth=0, CN=server-cvpn
Connection reset, restarting [0]
SIGUSR1[soft,connection-reset] received, process restarting
```

**Cause**  
The client certificate has been revoked\. The connection stops responding after trying to authenticate and is eventually reset from the server side\.

**Solution**  
Request a new configuration file from your Client VPN administrator\.

### Extended key usage \(EKU\)<a name="tunnelblick-eku"></a>

**Problem**  
The connection fails and returns the following error in the logs\.

```
TLS: Initial packet from [AF_INET]50.19.205.135:443, sid=29f2c917 4856ad34
VERIFY OK: depth=2, O=Digital Signature Trust Co., CN=DST Root CA X3
VERIFY OK: depth=1, C=US, O=Let's Encrypt, CN=Let's Encrypt Authority X3
VERIFY KU OK
Validating certificate extended key usage
 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
VERIFY EKU OK
VERIFY OK: depth=0, CN=cvpn-lab.myrandomnotes.com (http://cvpn-lab.myrandomnotes.com/)
Connection reset, restarting [0]
SIGUSR1[soft,connection-reset] received, process restarting
MANAGEMENT: >STATE:1559138717,RECONNECTING,connection-reset,,,,,
```

**Cause**  
The server authentication succeeded\. However, the client authentication fails because the client certificate has the extended key usage \(EKU\) field enabled for server authentication\.

**Solution**  
Verify that you are using correct client certificate and key\. If necessary, verify with your Client VPN administrator\. This error might occur if you're using the server certificate and not the client certificate to connect to the Client VPN endpoint\.

### Expired certificate<a name="tunnelblick-certificate-expired"></a>

**Problem**  
The server authentication succeeds but the client authentication fails with the following error\.

```
WARNING: “Connection reset, restarting [0] , SIGUSR1[soft,connection-reset] received, process restarting”
```

**Cause**  
The client certificate validity has expired\.

**Solution**  
Request a new client certificate from your Client VPN administrator\.

## OpenVPN<a name="macos-troubleshooting-openvpn"></a>

The following troubleshooting information was tested on version 2\.7\.1\.100 of the OpenVPN Connect Client software on macOS High Sierra 10\.13\.6\.

The configuration file is stored in the following location on your computer\.

```
/Library/Application Support/OpenVPN/profile
```

The connection logs are stored in the following location on your computer\.

```
Library/Application Support/OpenVPN/log/connection_name.log
```

### Cannot resolve DNS<a name="macos-openvpn-dns"></a>

**Problem**  
The connection fails with the following error\.

```
Mon Jul 15 13:07:17 2019 Transport Error: DNS resolve error on 'cvpn-endpoint-1234.prod.clientvpn.us-east-1.amazonaws.com' for UDP session: Host not found (authoritative)
Mon Jul 15 13:07:17 2019 Client terminated, restarting in 2000 ms...
Mon Jul 15 13:07:18 2019 CONNECTION_TIMEOUT [FATAL-ERR]
Mon Jul 15 13:07:18 2019 DISCONNECTED
Mon Jul 15 13:07:18 2019 >FATAL:CONNECTION_TIMEOUT
```

**Cause**  
OpenVPN Connect is unable to resolve the Client VPN DNS name\.

**Solution**  
See the solution for [Unable to Resolve Client VPN Endpoint DNS Name](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/troubleshooting.html#resolve-host-name) in the *AWS Client VPN Administrator Guide*\.
