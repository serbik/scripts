#!/bin/bash

# Variables



# Load 8021Q module
sudo modprobe 8021q

# Select physical interface
echo "What is your physical interface to use? (e.g. eth0 or enp0s31f6)"
read intf



# Creates specified VLAN
echo "VLAN ID to create?"
read vlanid

sudo ip link add link $intf name $intf.$vlanid type vlan id $vlanid

# Create bridge interface for specified VLAN
sudo ip link add br0.$vlanid type bridge

# Add VLAN interface to bridge
sudo brctl addif br0.$vlanid $intf.$vlanid


# Bring up the VLAN interface
sudo ip link set $intf.$vlanid up

# Bring up the bridge
sudo ip link set br0.$vlanid up
