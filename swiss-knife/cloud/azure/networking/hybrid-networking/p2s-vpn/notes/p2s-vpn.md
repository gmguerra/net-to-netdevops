# Point-to-Site VPN

A P2S VPN connection allows a secure connection to the VNet from an individual client computer via Internet. It's established by starting it from the VPN client computer. Telecommuters who want to connect to a VNet from a remote location. P2S VPNs are used when only a few clients would need to connect to a VNet. 

Supported platform: 
- OpenVPN: multiplatform VPN provide. A private IP from Azure will be give, and client will be treated the same as an Azure resource. SSL/TLS based VPN protocol. Can penetrate firewalls as it would only use TCP 443. Android, IOS, Windows, Linux and MAC are supported. 
- SSTP (Secure Socket Tunneling Protocol): Proprietary VPN protocol based on TLS 443. Integrated in Windows 7 and later. 
- IKEv2: IPsec based solution. MacOS can make use of this.

Authentication methods:
- Entra ID if set on Azure. Native authentication allowing users connect to Azure using Entra ID credentials. Requires the use of the Azure VPN Client, only supported for OpenVPN protocol and Windows. Conditional access and MFA are supported. To allow an user to use the VPN, you'll need to allowhim to use the app "OpenVPN"
- On premise identity stores (on-premises Active Directory Domain Services Authentication) would require a VPN connection and a Radius server to authenticate users. Allows users connect to Azure using their org domain credentials. RADIUS server can be deployed either on-premises or in Azure. 