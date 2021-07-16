# Connect using a Windows client application<a name="windows"></a>

The following procedures show how to establish a VPN connection using Windows\-based VPN clients\.

Before you begin, ensure that your Client VPN administrator has [created a Client VPN endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-create) and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoints.html#cvpn-working-endpoint-export)\.

For troubleshooting information, see [Windows troubleshooting](windows-troubleshooting.md)\.

## OpenVPN using a certificate from the Windows Certificate System Store<a name="windows-openvpn-cryptoapicert"></a>

You can configure the OpenVPN client to use a certificate and private key from the Windows Certificate System Store\. This option is useful when you use a smart card as part of your Client VPN connection\. For information about the OpenVPN client cryptoapicert option, see [Reference Manual for OpenVPN ](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-4/) on the OpenVPN website\.

**Note**  
The certificate must be stored on the local computer\.

**To use the cryptoapicert option with OpenVPN**

1. Create a \.pfx file that contains the client certificate and the private key\.

1. Import the \.pfx file to your personal certificate store, on your local computer\. For more information, see [How to: View certificates with the MMC snap\-in](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in#to-view-certificates-for-the-local-device) on the Microsoft website\.

1. Verify that your account has permissions to read the local computer certificate\. You can use the Microsoft Management Console to modify the permissions\. For more information, see [Rights to see the local computer certificates store](https://social.technet.microsoft.com/Forums/windowsserver/en-US/743d793c-ca94-45b3-88c6-375097eaafc0/rights-to-see-the-local-computer-certificates-store?forum=winserversecurity) on the Microsoft Technet website\.

1. Update the OpenVPN configuration file and specify the certificate by using either the certificate subject, or the certificate thumbprint\.

   The following is an example of specifying the certificate by using a subject\.

   ```
   cryptoapicert “SUBJ:Jane Doe”
   ```

   The following is an example of specifying the certificate by using a thumbprint\. You can find the thumbprint by using the Microsoft Management Console\. For more information, see [How to: Retrieve the Thumbprint of a Certificate](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate) on the Microsoft Technet website\.

   ```
   cryptoapicert “THUMB:a5 42 00 42 01"
   ```

After you complete the configuration, you use OpenVPN to establish a connection\.

## OpenVPN GUI<a name="windows-openvpn-gui"></a>

The following procedure shows how to establish a VPN connection using the OpenVPN GUI client application on a Windows computer\.

**Note**  
For information about the OpenVPN client application, see [Community Downloads](https://openvpn.net/community-downloads/) on the OpenVPN website\.

**To establish a VPN connection**

1. Start the OpenVPN client application\.

1. On the Windows taskbar, choose **Show/Hide icons**, right\-click **OpenVPN GUI**, and choose **Import file**\.  
![\[Windows step 2\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/windows_01.png)

1. In the Open dialog box, select the configuration file that you received from your Client VPN administrator and choose **Open**\.

1. On the Windows taskbar, choose **Show/Hide icons**, right\-click **OpenVPN GUI**, and choose **Connect**\.  
![\[Windows step 4\]](http://docs.aws.amazon.com/vpn/latest/clientvpn-user/images/windows_02.png)

## OpenVPN Connect Client<a name="windows-openvpn-connect"></a>

The following procedure shows how to establish a VPN connection using the OpenVPN Connect Client application on a Windows computer\.

**Note**  
For more information, see [Connecting to Access Server with Windows](https://openvpn.net/vpn-server-resources/connecting-to-access-server-with-windows/) on the OpenVPN website\.

**To establish a VPN connection**

1. Start the OpenVPN Connect Client application\.

1. On the Windows taskbar, choose **Show/Hide icons**, right\-click **OpenVPN**, and choose **Import profile**\.

1. Choose **Import from File** and select the configuration file that you received from your Client VPN administrator\.

1. To begin the connection, choose the connection profile\.