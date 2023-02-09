# AWS Client VPN for macOS<a name="client-vpn-connect-macos"></a>

The following procedure shows how to establish a VPN connection using the AWS provided client for macOS\. You can download and install the client at [AWS Client VPN download](https://aws.amazon.com/vpn/client-vpn-download/)\. The AWS provided client does not support automatic updates\.

**Topics**
+ [Requirements](#client-vpn-connect-macos-req)
+ [Connecting](#client-vpn-connect-macos-connecting)
+ [Release notes](#client-vpn-connect-macos-release-notes)

## Requirements<a name="client-vpn-connect-macos-req"></a>

To use the AWS provided client for macOS, the following is required:
+ 64\-bit macOS Mojave \(10\.14\), Catalina \(10\.15\), Big Sur \(11\.0\) or Monterey \(12\.0\)

The client reserves TCP port 8096 on your computer\. For Client VPN endpoints that use SAML\-based federated authentication \(single sign\-on\) the client reserves TCP port 35001\.

Before you begin, ensure that your Client VPN administrator has [created a Client VPN endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-create) and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoint-export.html)\.

## Connecting<a name="client-vpn-connect-macos-connecting"></a>

Before you begin, ensure that you've read the [requirements](#client-vpn-connect-macos-req)\. The AWS provided client is also referred to as the *AWS VPN Client* in the following steps\.

**To connect using the AWS provided client for macOS**

1. Open the **AWS VPN Client** app\.

1. Choose **File**, **Manage Profiles**\.  
![\[macOS manage profiles\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-profiles.png)

1. Choose **Add Profile**\.

1. For **Display Name**, enter a name for the profile\.  
![\[macOS add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-add-profile.png)

1. For **VPN Configuration File**, browse to the configuration file that you received from your Client VPN administrator\. Choose **Open**\.

1. Choose **Add Profile**\.

1. In the **AWS VPN Client** window, ensure that your profile is selected and then choose **Connect**\. If the Client VPN endpoint has been configured to use credential\-based authentication, you'll be prompted to enter a user name and password\.

1. To view statistics for your connection, choose **Connection**, **Show Details**\.  
![\[macOS show details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-details.png)

1. To disconnect, in the **AWS VPN Client** window, choose **Disconnect**\. Alternatively, choose the client icon on the menu bar, and then choose **Disconnect *<your\-profile\-name>***\.  
![\[macOS disconnect\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-disconnect.png)

## Release notes<a name="client-vpn-connect-macos-release-notes"></a>

The following table contains the release notes and download links for the current and previous versions of AWS Client VPN for macOS\.


| Version | Changes | Date | Download link | 
| --- | --- | --- | --- | 
| 3\.2\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | January 23, 2023 | [Download version 3\.2\.0](https://d20adtppz83p9s.cloudfront.net/OSX/3.2.0/AWS_VPN_Client.pkg)sha256: cb09c0a6dabfa98d30ef389977395228f5e89e260e2df8364be81ec0ef9ac6a4 | 
| 3\.1\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | May 23, 2022 | [Download version 3\.1\.0](https://d20adtppz83p9s.cloudfront.net/OSX/3.1.0/AWS_VPN_Client.pkg)sha256: d88a4b5c9c0f9e64cef52ab508c65aff23913f712589c1f994b0578db985baf9 | 
| 3\.0\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | March 3, 2022 | No longer supported\. | 
| 2\.0\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | January 20, 2022 | No longer supported\. | 
| 1\.4\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | November 9, 2021 | No longer supported\. | 
| 1\.3\.5 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | September 20, 2021 | No longer supported\. | 
| 1\.3\.4 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | August 4, 2021 | No longer supported\. | 
| 1\.3\.3 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | July 1, 2021 | No longer supported\. | 
| 1\.3\.2 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | May 12, 2021 | No longer supported\. | 
| 1\.3\.1 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | April 5, 2021 | No longer supported\. | 
| 1\.3\.0 | Added support features such as error reporting, sending diagnostic logs, and analytics\. | March 8, 2021 | No longer supported\. | 
| 1\.2\.5 | Minor bug fixes and enhancements\. | February 25, 2021 | No longer supported\. | 
| 1\.2\.4 | Minor bug fixes and enhancements\. | October 26, 2020 | No longer supported\. | 
| 1\.2\.3 | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | October 8, 2020 | No longer supported\. | 
| 1\.2\.2 | Minor bug fixes and enhancements\. | August 12, 2020 | No longer supported\. | 
| 1\.2\.1 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | July 1, 2020 | No longer supported\. | 
| 1\.2\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | May 19, 2020 | No longer supported\. | 
| 1\.1\.2 | Minor bug fixes and enhancements\. | April 21, 2020 | No longer supported\. | 
| 1\.1\.1 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | April 2, 2020 | No longer supported\. | 
| 1\.1\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-macos.html)  | March 9, 2020 | No longer supported\. | 
| 1\.0\.0 | The initial release\. | February 4, 2020 | No longer supported\. | 