# Monitor networks and transfer files

## ping - Send an ICMP ECHO_REQUEST to network hosts
- The ping command sends a special network packet called an ICMP ECHO_REQUEST to a specified host. Most network devices receiving this packet will reply to it, allowing the network connection to be verified.
- Usage: `ping <host>`
- Example:
    - `ping google.com`

## traceroute - Print the route packets trace to a network host
- The traceroute program lists all the “hops” network traffic takes to get from the local system to a specified host.
- Usage: `traceroute <host>`
- For routers that provided identifying information, we see their hostnames, IP addresses, and performance data, which includes three samples of round-trip time from the local system to the router. For routers that do not provide identifying information, we
see asterisks.
- Example:
    - `traceroute linux.org`

## dig - Domain Information Groper
- It is used for retrieving information about DNS name servers.
- Usage: `dig [server] [name] [type]`
- Examples:
    - `dig linux.org`
    - `dig linux.org MX`
    - `dig linux.org ANY`

## ip - Show/manipulate routing, devices, policy routing, and tunnels
- The ip program is a multipurpose network configuration tool that makes use of the full range of networking features available in modern Linux kernels.
- It replaces the earlier and now deprecated `ifconfig` program.
- [IP command guide](https://phoenixnap.com/kb/linux-ip-command-examples)
- Example:
    - `ip a`

## ifconfig

## iwconfig

## netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
- The netstat program is used to examine various network settings and statistics.
- Using the `-ie` option, we can examine the network interfaces in our system.
- Using the `-r` option will display the kernel’s network routing table.

## ftp - Internet file transfer program

## wget - Non-interactive network downloader

## ssh - OpenSSH SSH client (remote login program)

## scp