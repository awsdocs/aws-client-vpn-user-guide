# AWS Client VPN for Windows<a name="client-vpn-connect-windows"></a>

The following procedure shows how to establish a VPN connection using the AWS provided client for Windows\. You can download and install the client at [AWS Client VPN download](https://aws.amazon.com/vpn/client-vpn-download/)\. The AWS provided client does not support automatic updates\.

**Topics**
+ [Requirements](#client-vpn-connect-windows-req)
+ [Connecting](#client-vpn-connect-windows-connecting)
+ [Release notes](#client-vpn-connect-windows-release-notes)

## Requirements<a name="client-vpn-connect-windows-req"></a>

To use the AWS provided client for Windows, the following are required:
+ Windows 10 64\-bit operating system, x64 processor
+ \.NET Framework 4\.7\.2 or higher

The client reserves TCP port 8096 on your computer\. For Client VPN endpoints that use SAML\-based federated authentication \(single sign\-on\), the client reserves TCP port 35001\.

Before you begin, ensure that your Client VPN administrator has [created a Client VPN endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-create) and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoint-export.html)\.

## Connecting<a name="client-vpn-connect-windows-connecting"></a>

Before you begin, ensure that you've read the [requirements](#client-vpn-connect-windows-req)\. The AWS provided client is also referred to as *AWS VPN Client* in the following steps\.

**To connect using the AWS provided client for Windows**

1. Open the **AWS VPN Client** app\.

1. Choose **File**, **Manage Profiles**\.  
![\[Windows manage profiles\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-win-profiles.png)

1. Choose **Add Profile**\.  
![\[Windows add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-win-add-profile.PNG)

1. For **Display Name**, enter a name for the profile\.

1. For **VPN Configuration File**, browse to and then select the configuration file that you received from your Client VPN administrator, and choose **Add Profile**\.

1. In the **AWS VPN Client** window, ensure that your profile is selected, and then choose **Connect**\. If the Client VPN endpoint has been configured to use credential\-based authentication, you'll be prompted to enter a user name and password\.

1. To view statistics for your connection, choose **Connection**, **Show Details**\.  
![\[Windows add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-win-details.png)

1. To disconnect, in the **AWS VPN Client** window, choose **Disconnect**\. Alternatively, choose the client icon on the Windows taskbar, and then choose **Disconnect**\.  
![\[Windows add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-win-disconnect.png)

## Release notes<a name="client-vpn-connect-windows-release-notes"></a>

The following table contains the release notes and download links for the current and previous versions of AWS Client VPN for Windows\.


| Version | Changes | Date | Download link and SHA256 | 
| --- | --- | --- | --- | 
| 3\.5\.0 | Minor bug fixes and enhancements\. | April 3, 2023 | [Download version 3\.5\.0](https://d20adtppz83p9s.cloudfront.net/WPF/3.5.0/AWS_VPN_Client.msi) 8b3cca1159a6cedd15936150743f6019f22eaf6aa180b4f86adc380a5f5cf7cc  | 
| 3\.4\.0 | Rolled back the changes from version 3\.3\.0\. | March 28, 2023 | No longer supported | 
| 3\.3\.0 | Minor bug fixes and enhancements\. | March 17, 2023 | No longer supported | 
| 3\.2\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | January 23, 2023 | [Download version 3\.2\.0](https://d20adtppz83p9s.cloudfront.net/WPF/3.2.0/AWS_VPN_Client.msi) 18fc90b91b14d9adb3922e1a34eb546338c6db2d1ddbf5ac201e83f012a42d8c | 
| 3\.1\.0 | Improved security posture\. | May 23, 2022 | [Download version 3\.1\.0](https://d20adtppz83p9s.cloudfront.net/WPF/3.1.0/AWS_VPN_Client.msi) 74ad66c5062d484173581deaa9bd6a6698ebd369a833f77710d417f4e4fcfe25 | 
| 3\.0\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | March 3, 2022 | No longer supported | 
| 2\.0\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | January 20, 2022 | No longer supported | 
| 1\.3\.7 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | November 8, 2021 | No longer supported | 
| 1\.3\.6 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | September 20, 2021 | No longer supported | 
| 1\.3\.5 | Patch to delete large windows log files\. | August 16, 2021 | No longer supported | 
| 1\.3\.4 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | August 4, 2021 | No longer supported | 
| 1\.3\.3 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | July 1, 2021 | No longer supported | 
| 1\.3\.2 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | May 12, 2021 | No longer supported | 
| 1\.3\.1 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | April 5, 2021 | No longer supported | 
| 1\.3\.0 | Added support features such as error reporting, sending diagnostic logs, and analytics\. | March 8, 2021 | No longer supported | 
| 1\.2\.7 | [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html) | February 25, 2021 | No longer supported | 
| 1\.2\.6 | Minor bug fixes and enhancements\. | October 26, 2020 | No longer supported | 
| 1\.2\.5 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | October 8, 2020 | No longer supported | 
| 1\.2\.4 | Minor bug fixes and enhancements\. | September 1, 2020 | No longer supported | 
| 1\.2\.3 | Roll back changes in version 1\.2\.2\. | August 20, 2020 | No longer supported | 
| 1\.2\.1 | Minor bug fixes and enhancements\. | July 1, 2020 | No longer supported | 
| 1\.2\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | May 19, 2020 | No longer supported | 
| 1\.1\.1 | Minor bug fixes and enhancements\. | April 21, 2020 | No longer supported | 
| 1\.1\.0 |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-connect-windows.html)  | March 9, 2020 | No longer supported | 
| 1\.0\.0 | The initial release\. | February 4, 2020 | No longer supported | 