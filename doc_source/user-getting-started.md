# Getting Started with Client VPN<a name="user-getting-started"></a>

Before you can establish a VPN session, your Client VPN administrator must create and configure a Client VPN endpoint\. Your administrator controls which networks and resources you can access when you establish a VPN session\. You then use a VPN client application to connect to a Client VPN endpoint and establish a secure VPN connection\.

**Topics**
+ [Prerequisites](#install-prereq)
+ [Step 1: Get a VPN Client Application](#install-client)
+ [Step 2: Get the Client VPN Endpoint Configuration File](#get-config-file)
+ [Step 3: Connect to the VPN](#import-connect)

## Prerequisites<a name="install-prereq"></a>

To establish a VPN connection, you must have the following:
+ Access to the internet
+ A supported device

## Step 1: Get a VPN Client Application<a name="install-client"></a>

You can connect to a Client VPN endpoint and establish a VPN connection using the AWS\-provided client or another OpenVPN\-based client application\. 

The AWS\-provided client is supported on Windows and macOS\. You can download the client at [AWS Client VPN download](https://aws.amazon.com/vpn/client-vpn-download/)\.

Alternatively, download and install an OpenVPN client application on the device from which you intend to establish the VPN connection\.

## Step 2: Get the Client VPN Endpoint Configuration File<a name="get-config-file"></a>

You must get the Client VPN endpoint configuration file from your administrator\. The configuration file includes the information about the Client VPN endpoint and the certificates required to establish a VPN connection\.

## Step 3: Connect to the VPN<a name="import-connect"></a>

Import the Client VPN endpoint configuration file to the AWS\-provided client or your OpenVPN client application and connect to the VPN\. For steps to connect to a VPN, see the following topics:
+ [Connect Using the AWS\-Provided Client](connect-aws-client-vpn-connect.md)
+ [Connect Using an OpenVPN Client](connect.md)

For Client VPN endpoints that use Active Directory authentication, you will be prompted to enter your user name and password\. If multi\-factor authentication \(MFA\) has been enabled for the directory, you will also be prompted to enter your MFA code\.