# MacOS Troubleshooting<a name="macos-troubleshooting"></a>

The following are problems you might have when using MacOS\-based clients to connect to a Client VPN endpoint\.

**Topics**
+ [Tunnelblick](#macos-troubleshooting-tunnelblick)
+ [OpenVPN](#macos-troubleshooting-openvpn)

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

### Cipher Algorithm 'AES\-256\-GCM' Not Found<a name="tunnelblick-cipher"></a>

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

### Connection Hangs and Resets<a name="tunnelblick-connection-reset"></a>

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
The client certificate has been revoked\. The connection hangs after trying to authenticate and is eventually reset from the server side\.

**Solution**  
Request a new configuration file from your Client VPN administrator\.

### Invalid Certificate<a name="tunnelblick-invalid-certificate"></a>

**Problem**  
The connection fails and returns the following error in the logs\.

```
VERIFY ERROR: depth=1, error=unable to get issuer certificate: C=US, O=Let's Encrypt, CN=Let's Encrypt Authority X3
OpenSSL: error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed
TLS_ERROR: BIO read tls_read_plaintext error
TLS Error: TLS object -> incoming plaintext read error
TLS Error: TLS handshake failed
Fatal TLS error (check_tls_errors_co), restarting
SIGUSR1[soft,tls-error] received, process restarting
```

**Cause**  
The issuer certificate is not valid in the \.ovpn configuration file\.

**Solution**  
Open the Client VPN configuration file \(the \.ovpn file\) in a text editor, and add the following certificate to the file\.

```
-----BEGIN CERTIFICATE-----
MIIDSjCCAjKgAwIBAgIQRK+wgNajJ7qJMDmGLvhAazANBgkqhkiG9w0BAQUFADA/
MSQwIgYDVQQKExtEaWdpdGFsIFNpZ25hdHVyZSBUcnVzdCBDby4xFzAVBgNVBAMT
DkRTVCBSb290IENBIFgzMB4XDTAwMDkzMDIxMTIxOVoXDTIxMDkzMDE0MDExNVow
PzEkMCIGA1UEChMbRGlnaXRhbCBTaWduYXR1cmUgVHJ1c3QgQ28uMRcwFQYDVQQD
Ew5EU1QgUm9vdCBDQSBYMzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEB
AN+v6ZdQCINXtMxiZfaQguzH0yxrMMpb7NnDfcdAwRgUi+DoM3ZJKuM/IUmTrE4O
rz5Iy2Xu/NMhD2XSKtkyj4zl93ewEnu1lcCJo6m67XMuegwGMoOifooUMM0RoOEq
OLl5CjH9UL2AZd+3UWODyOKIYepLYYHsUmu5ouJLGiifSKOeDNoJjj4XLh7dIN9b
xiqKqy69cK3FCxolkHRyxXtqqzTWMIn/5WgTe1QLyNau7Fqckh49ZLOMxt+/yUFw
7BZy1SbsOFU5Q9D8/RhcQPGX69Wam40dutolucbY38EVAjqr2m7xPi71XAicPNaD
aeQQmxkqtilX4+U9m5/wAl0CAwEAAaNCMEAwDwYDVR0TAQH/BAUwAwEB/zAOBgNV
HQ8BAf8EBAMCAQYwHQYDVR0OBBYEFMSnsaR7LHH62+FLkHX/xBVghYkQMA0GCSqG
SIb3DQEBBQUAA4IBAQCjGiybFwBcqR7uKGY3Or+Dxz9LwwmglSBd49lZRNI+DT69
ikugdB/OEIKcdBodfpga3csTS7MgROSR6cz8faXbauX+5v3gTt23ADq1cEmv8uXr
AvHRAosZy5Q6XkjEGB5YGV8eAlrwDPGxrancWYaLbumR9YbK+rlmM6pZW87ipxZz
R8srzJmwN0jP41ZL9c8PDHIyh8bwRLtTcm1D9SZImlJnt1ir/md2cXjbDaJWFBM5
JDGFoqgCWjBH4d1QB7wCCZAA62RjYJsWvIjJEubSfZGL+T0yjWW06XyxV3bqxbYo
Ob8VZRzI9neWagqNdwvYkQsEjgfbKbYK7p2CNTUQ
-----END CERTIFICATE-----
```

### Extended Key Usage \(EKU\)<a name="tunnelblick-eku"></a>

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
Ensure that you are using correct client certificate and key\. If necessary, verify with your Client VPN administrator\. This error might occur if you're using the server certificate and not the client certificate to connect to the Client VPN endpoint\.

### Expired Certificate<a name="tunnelblick-certificate-expired"></a>

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

### Cannot Resolve DNS<a name="macos-openvpn-dns"></a>

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