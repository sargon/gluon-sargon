# DDHCPD

## Integration of DDHCPD in gluon

Add the feed https://github.com/sargon/gluon-sargon to your `modules` config,
add the package `ddhcpd` to your `site.mk` and add a section in your `site.conf`:

    ddhcpd = {
      enabled = true,
      range = "10.187.124.0/22",
      block_size = 2,
      block_timeout = 300,
      dhcp_lease_time = 300,
      spare_leases = 2,
      tentative_timeout = 15,
    },

Set enabled to `false` if you don't want DDHCPD to be enabled by default on your
nodes.

Choose a free IP-range that is not used by the DHCP-servers of your gateways
that the DDHCPD can use to assign to clients.

## Configuration

Make sure your gateways use the same MAC address for their batman interface and
the primary batman interface (which may also be a bridge) all the time.
You need to install [mesh-announce](https://github.com/ffnord/mesh-announce) on
your gateways, so DDHCPD can query the gateway address that should be announced
over DHCP via `respondd` from the chosen gateway.

#### disable DDHCPD with one shell call:

     ssh <router ip> 'uci set ddhcpd.enabled="0"; uci commit ddhcpd && /etc/init.d/ddhcpd restart; echo done'

All other values can be changed via `uci set` also, but all settings except
`enabled` are reset to the default value set in your `site.conf` on reboot.

## More

More detailed documentation regarding DDHCPD itself can be found at
https://github.com/sargon/ddhcpd/blob/master/README
