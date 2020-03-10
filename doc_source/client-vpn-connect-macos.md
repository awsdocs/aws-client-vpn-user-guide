# macOS<a name="client-vpn-connect-macos"></a>

The following procedure shows how to establish a VPN connection using the AWS\-provided client for macOS\. You can download and install the client at [AWS Client VPN download](https://aws.amazon.com/vpn/client-vpn-download/)\.

For troubleshooting information, see [Troubleshooting Your Client VPN Connection](troubleshooting.md)\.

## Requirements<a name="client-vpn-connect-macos-req"></a>

To use the AWS\-provided client for macOS, the following is required:
+ macOS High Sierra \(10\.13\) or Mojave \(10\.14\)

The client reserves TCP port 8096 on your computer\.

Before you begin, ensure that your Client VPN administrator has created a Client VPN endpoint and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-getting-started.html#cvpn-getting-started-config)\.

## Connecting<a name="client-vpn-connect-macos-connecting"></a>

Before you begin, ensure that you've read the [requirements](#client-vpn-connect-macos-req)\. The AWS\-provided client is also referred to as *AWS VPN Client* in the following steps\.

**To connect using the AWS\-provided client for macOS**

1. Open the **AWS VPN Client** app\.

1. Choose **File**, **Manage Profiles**\.  
![\[macOS manage profiles\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-profiles.png)

1. Choose **Add Profile**\.

1. For **Display Name**, enter a name for the profile\.  
![\[macOS add profile\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-add-profile.png)

1. For **VPN Configuration File**, browse to the configuration file that you received from your Client VPN administrator\. Choose **Open**\.

1. Choose **Add Profile**\.

1. In the **AWS VPN Client** window, ensure that your profile is selected and then choose **Connect**\.

1. To view statistics for your connection, choose **Connection**, **Show Details**\.  
![\[macOS show details\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-details.png)

1. To disconnect, in the **AWS VPN Client** window, choose **Disconnect**\. Alternatively, choose the client icon on the menu bar, and then choose **Disconnect *<your\-profile\-name>***\.  
![\[macOS disconnect\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/client-vpn-mac-disconnect.png)