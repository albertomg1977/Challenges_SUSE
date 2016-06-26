ARQUITECTURE:

I have a laptop (host1), and one physical server (host2), I use host2 to create the virtual servers.

host1 has two ethernets, eth0 to connect to internet, and eth1 to connect to host2.

host2 has three ethernets , eth0 (without use) , eth1 ( ethernet which I use for internet), and eth2 (to connect my laptop to host2).

FILES:

commands_bridge -> commands to create a linux bridge in host2 and the virtual server.
commands_openvswich -> commands to create a swich with openvswich in host2 and the virtual server.
bridge.tcpdump  -> capture tcpdump of a ping from my laptop to the virtual server when it is using the bridge.
openvswich.tcpdump -> capture tcpdump of a ping from my laptop to the virtual server server when it is using the virtual swich.
virtualserver_bridge.xml -> xml file to create the virtual server which use the bridge created in the physical host.
virtualserver_openvswitch.xml ->  xml file to create the virtual server which use the virtual swich created in the physical host.

The XML files which are used to create the servers are the same, except to the interface's part.

Bridge:

   <interface type='bridge'>
      <mac address='52:54:00:25:bc:2b'/>
      <source bridge='br_test'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>


Openvswich:

    <interface type='bridge'>
      <mac address='52:54:00:25:bc:2b'/>
      <source bridge='ovsbr0'/>
      <virtualport type='openvswitch'/>
      <model type='rtl8139'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>



