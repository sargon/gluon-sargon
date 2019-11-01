# DDHCPD BATMAN-ADV integration

Integration of ddhcpd into batman-adv networks. The contained script manages
the configuration of gateway and dns server dhcp options, so client can be
configured with these informations. 

Knowing the IP address of a gateway can be a hassle in batman-adv networks.

## Configuration

Make sure your gateways use the same MAC address for their batman interface and
the primary batman interface (which may also be a bridge) all the time.
You need to install [mesh-announce](https://github.com/ffnord/mesh-announce) on
your gateways, so DDHCPD can query the gateway address that should be announced
over DHCP via `respondd` from the chosen gateway.
