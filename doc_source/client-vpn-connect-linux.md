# AWS Client VPN for Linux<a name="client-vpn-connect-linux"></a>

The following procedures show how to install the AWS provided client for Linux, and to establish a VPN connection using the AWS provided client\. The AWS provided client for Linux does not support automatic updates\.

**Topics**
+ [Requirements](#client-vpn-connect-linux-req)
+ [Installation](#client-vpn-connect-linux-install)
+ [Connecting](#client-vpn-connect-linux-connecting)
+ [Release notes](#client-vpn-connect-linux-release-notes)

## Requirements<a name="client-vpn-connect-linux-req"></a>

To use the AWS provided client for Linux, the following is required:
+ Ubuntu 18\.04 LTS or Ubuntu 20\.04 LTS \(AMD64 only\)

The client reserves TCP port 8096 on your computer\. For Client VPN endpoints that use SAML\-based federated authentication \(single sign\-on\) the client reserves TCP port 35001\.

Before you begin, ensure that your Client VPN administrator has [created a Client VPN endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-create) and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-export)\.

## Installation<a name="client-vpn-connect-linux-install"></a>

There are multiple methods that can be used to install the AWS provided client for Linux\. Use one of the methods provided in the following options\. Before you begin, ensure that you've read the [requirements](#client-vpn-connect-linux-req)\.

**Option 1 \-\- Install via package repository**

1. Add the AWS VPN Client public key to your Ubuntu OS\.

   ```
   wget -q -O - https://d20adtppz83p9s.cloudfront.net/GTK/latest/debian-repo/awsvpnclient_public_key.asc | sudo apt-key add -
   ```

1. Use the applicable command to add the repository to your Ubuntu OS, depending on your Ubuntu version:

   Ubuntu 18\.04

   ```
   echo "deb [arch=amd64] https://d20adtppz83p9s.cloudfront.net/GTK/latest/debian-repo ubuntu-18.04 main" | sudo tee /etc/apt/sources.list.d/aws-vpn-client.list
   ```

   Ubuntu 20\.04

   ```
   echo "deb [arch=amd64] https://d20adtppz83p9s.cloudfront.net/GTK/latest/debian-repo ubuntu-20.04 main" | sudo tee /etc/apt/sources.list.d/aws-vpn-client.list
   ```

1. Use the following command to update the repositories on your system\.

   ```
   sudo apt-get update
   ```

1. Use the following command to install the AWS provided client for Linux\.

   ```
   sudo apt-get install awsvpnclient
   ```

**Option 2 \-\- Install using the \.deb package file**

1. Download the \.deb file from [AWS Client VPN download ](https://d20adtppz83p9s.cloudfront.net/GTK/latest/awsvpnclient_amd64.deb) or by using the following command\.

   ```
   curl https://d20adtppz83p9s.cloudfront.net/GTK/latest/awsvpnclient_amd64.deb -o awsvpnclient_amd64.deb
   ```

1. Install the AWS provided client for Linux using the `dpkg` utility\.

   ```
   sudo dpkg -i awsvpnclient_amd64.deb
   ```

**Option 3 \-\- Install the \.deb package using Ubuntu Software Center**

1. Download the \.deb package file from [AWS Client VPN download ](https://d20adtppz83p9s.cloudfront.net/GTK/latest/awsvpnclient_amd64.deb)\.

1.  After downloading the \.deb package file, use the Ubuntu Software Center to install the package\. Follow the steps for installing from a standalone \.deb package using Ubuntu Software Center, as described on the [Ubuntu Wiki](https://wiki.ubuntu.com/SoftwareCenter#from_a_standalone_.deb_package)\. 

## Connecting<a name="client-vpn-connect-linux-connecting"></a>

The AWS provided client is also referred to as the *AWS VPN Client* in the following steps\.

**To connect using the AWS provided client for Linux**

1. Open the **AWS VPN Client** app\.

1. Choose **File**, **Manage Profiles**\.

1. Choose **Add Profile**\.  
![\[Linux add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-linux-profiles.png)

1. For **Display Name**, enter a name for the profile\.

1. For **VPN Configuration File**, browse to the configuration file that you received from your Client VPN administrator\. Choose **Open**\.

1. Choose **Add Profile**\.  
![\[Linux add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-linux-add-profile2.png)

1. In the **AWS VPN Client** window, ensure that your profile is selected, and then choose **Connect**\. If the Client VPN endpoint has been configured to use credential\-based authentication, you'll be prompted to enter a user name and password\.  
![\[Linux add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-linux-connect.png)

1. To view statistics for your connection, choose **Connection**, **Show Details**\.  
![\[macOS show details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-linux-details.png)

1. To disconnect, in the **AWS VPN Client** window, choose **Disconnect**\.   
![\[Linux disconnect\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-linux-disconnect.png)

## Release notes<a name="client-vpn-connect-linux-release-notes"></a>

To view the release notes and download links for the current and previous versions of AWS Client VPN for Linux, see [Release notes for Linux](release-notes.md#release-notes-linux)\.