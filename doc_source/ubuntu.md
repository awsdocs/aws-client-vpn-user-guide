# Ubuntu<a name="ubuntu"></a>

The following procedures show how to establish a VPN connection using Ubuntu\-based VPN clients\.

Before you begin, ensure that your Client VPN administrator has created a Client VPN endpoint and provided you with the [Client VPN endpoint configuration file](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-getting-started.html#cvpn-getting-started-config)\.

For troubleshooting information, see [Ubuntu Troubleshooting](ubuntu-troubleshooting.md)\.

## OpenVPN \- Network Manager<a name="ubuntu-network-manager-openvpn"></a>

The following procedure shows how to establish a VPN connection using the OpenVPN application through the Network Manager GUI on an Ubuntu computer\.

**To establish a VPN connection**

1. Install the network manager module using the following command\.

   ```
   sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-openvpn network-manager-openvpn-gnome
   ```

1. Go to **Settings**, **Network**\.

1. Choose the plus symbol \(**\+**\) next to **VPN**, and then choose **Import from file\.\.\.**\.

1. Navigate to the configuration file that you received from your VPN administrator and choose **Open**\.

## OpenVPN<a name="ubuntu-openvpn"></a>

The following procedure shows how to establish a VPN connection using the OpenVPN application on an Ubuntu computer\.

**To establish a VPN connection**

1. Install OpenVPN using the following command\.

   ```
   sudo apt-get install openvpn
   ```

1. Start the connection by loading the configuration file that you received from your VPN administrator\.

   ```
   sudo openvpn --config /path/to/config/file
   ```