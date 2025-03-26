# DHCP Exclusion Range Configuration

This repository contains a sample DHCP server configuration with exclusion ranges to prevent certain IP addresses from being assigned to clients.

## Step 1: Edit DHCP Configuration File

 Open the DHCP configuration file for editing:
 
  #vim /etc/dhcp/dhcpd.conf

## Step 2: Example Configuration for Exclusion Range

  You can define multiple range statements to exclude specific IP addresses within the subnet.
  
  Example 1: Exclude 192.168.1.51 to 192.168.1.70
  
  This example configures an exclusion between 192.168.1.51 and 192.168.1.70:

    # DHCP Server Configuration file.

    # See /usr/share/doc/dhcps/dhcpd.conf.example
    # See dhcpd.conf(5) man page

     authoritative;
    
    # Specify network address and subnet mask
    subnet 192.168.1.0 netmask 255.255.255.0 {

    # Specify the range of lease IP addresses
    range 192.168.1.50 192.168.1.50;
    range 192.168.1.71 192.168.1.150;

    # Exclude IP addresses (Example: 192.168.1.51 to 192.168.1.70)
    # Exclude 192.168.1.51 to 192.168.1.70
    # Exclude 192.168.1.211 to 192.168.1.230

    # Specify default gateway
    option routers 192.168.1.1;

    # DNS servers for name resolution
    option domain-name-servers 8.8.8.8, 8.8.4.4;

    # Specify broadcast address
    option broadcast-address 192.168.1.255;

    # Default lease time
    default-lease-time 600;

    # Max lease time
    max-lease-time 7200;
    }


Step 3: Restart DHCP Service

After making changes to the configuration file, restart the DHCP service:

#systemctl restart dhcpd



✔ Explanation:

Excluded IP Addresses: Any addresses between the defined range statements will be excluded from assignment.

Example 1: IPs 192.168.1.211 to 192.168.1.230 are excluded.

Example 2: IPa 192.168.1.51 to 192.168.1.60 and 192.168.1.211 to 192.168.1.230 are excluded.

This allows better control over IP allocation and avoids conflicts with static IP addresses or reserved devices.
