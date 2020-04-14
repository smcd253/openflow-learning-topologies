# EE555 - Broadband Network Architecture - Final Project
**An implementation of Openflow using Mininet and Pox**

## Compilation Instructions
* Step 1: Start your Mininet Ubuntu VM and log in
*Login: mininet*
*Password: mininet*
    * Step 1a: Run `ifconfig` to get your URL for SSHing into the VM from your host machine.
    * Step 1b: Run `sudo dhclient` to enable the NAT forwarding port on your VM to connect to the internet.

* Step 2: Establish 2 separate connections to the VM 
```bash
# Connection 1: Mininet Console
ssh -X mininet@<your VM url>

# Connection 2: Controller Console
ssh mininet@<your VM url>
```

* Step 3 (Controller Console): Run The controller script in the controller console
```bash
cd pox
./pox.py log.level --DEBUG misc.controller_1
```

* Step 4 (Mininet Console): Run mininet in the mininet console
```bash
sudo mn --custom topology_1.py --topo mytopo --mac --controller remote
```

* Step 5 (Mininet Console): Establish connection between all nodes in the 
```bash
pingall
iperf
```

* Step 6 (Mininet Console): Open xterm for all nodes and run tcp dump
**h2**
```bash
 tcpdump -XX -n -i h2-eth0
```

**h3**
```bash
 tcpdump -XX -n -i h3-eth0
```

**h1**
```bash
ping -c1 10.0.0.2
```