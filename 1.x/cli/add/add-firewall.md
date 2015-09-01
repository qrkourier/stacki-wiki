## add firewall

### Usage

`stack add firewall [action=string] [chain=string] [network=string] [output-network=string] [protocol=string] [rulename=string] [service=string] [table=string]`

### Description

Add a global firewall rule for the all hosts in the cluster.

### Parameters
* `[action=string]`

   The iptables 'action' this rule should be applied to (e.g.,
	ACCEPT, REJECT, DROP).
* `[chain=string]`

   The iptables 'chain' this rule should be applied to (e.g.,
	INPUT, OUTPUT, FORWARD).
* `[network=string]`

   The network this rule should be applied to. This is a named network
        (e.g., 'private') and must be one listed by the command
        'rocks list network'.
	To have this firewall rule apply to all networks, specify the
	keyword 'all'.
* `[output-network=string]`

   The output network this rule should be applied to. This is a named
	network (e.g., 'private') and must be one listed by the command
        'rocks list network'.
* `[protocol=string]`

   The protocol associated with the rule. For example, "tcp" or "udp".
	To have this firewall rule apply to all protocols, specify the
	keyword 'all'.
* `[rulename=string]`

   The rule name for the rule to add. This is the handle by
	which the admin can remove or override the rule.
* `[service=string]`

   The service identifier, port number or port range. For example
	"www", 8080 or 0:1024.
	To have this firewall rule apply to all services, specify the
	keyword 'all'.
* `[table=string]`

   The table to add the rule to. Valid values are 'filter',
	'nat', 'mangle', and 'raw'. If this parameter is not
	specified, it defaults to 'filter'

### Examples

* `stack add firewall network=public service="ssh" protocol="tcp" action="ACCEPT" chain="INPUT" flags="-m state --state NEW" table="filter" rulename="accept_public_ssh"`

   Accept TCP packets for the ssh service on the public network on
	the INPUT chain in the "filter" table and apply the "-m state --state NEW"
	flags to the rule.
	If 'eth1' is associated with the public network, this will be
	translated as the following iptables rule:
	"-A INPUT -i eth1 -p tcp --dport ssh -m state --state NEW -j ACCEPT"

* `stack add firewall network=private service="all" protocol="all" action="ACCEPT" chain="INPUT"`

   Accept all protocols and all services on the private network on the
	INPUT chain.
	If 'eth0' is the private network, then this will be translated as
	the following iptables rule:
	"-A INPUT -i eth0 -j ACCEPT"


