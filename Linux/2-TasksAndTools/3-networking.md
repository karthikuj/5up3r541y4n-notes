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
- You can deactivate or activate interfaces using `down` or `up`.
- [IP command guide](https://phoenixnap.com/kb/linux-ip-command-examples)
- Example:
    - `ip a`
    - `ip link set dev eth0 up`
    - `ip link set dev eth0 down`

## ifconfig
- Deprecated but still used by many, `ifconfig` command is used to configure the kernel-resident network interfaces.
- Usage: `ifconfig [...OPTIONS] [INTERFACE]`
- You can activate or deactivate interfaces using `up` or `down` options.
- Examples:
    - `ifconfig`
    - `ifconfig wlan0`
    - `ifconfig wlan0 down`
    - `ifconfig wlan0 up`

## iwconfig
- Like `ifconfig`, `iwconfig` is also used to configure the kernel-resident network interfaces. But it is dedicated to wireless networking interfaces only.
- It is used to set the parameters of the network interface that are particular to the wireless operation like SSID, frequency etc.
- Usage: `iwconfig [INTERFACE] [OPTIONS]`
- You can set operating mode of the device using `mode` option. The modes can be Ad-Hoc, Managed, Master, Repeater, Secondary, and Monitor.
- Examples:
    - `iwconfig`
    - `iwconfig wlan0 mode Monitor`
    - `iwconfig wlan0 mode Managed`


## netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
- The netstat program is used to examine various network settings and statistics.
- Using the `-ie` option, we can examine the network interfaces in our system.
- Using the `-r` option will display the kernel’s network routing table.

## ftp - File Transfer Protocol
- It is used to transfer files over a network.
- It is not secure as it sends account names and passwords in clear text.
- By default it runs on port 21.
- Usage: `ftp [fileserver]`
- You can use `cd` inside FTP prompt to change the directory and `lcd` inside FTP prompt to change the local directory.
- Use `get` to download files to local system and `put` command to upload files to the server.
- To download multiple files from the server use the `mget` command.
- Example:
    - `ftp ftp.ubuntu.com`

## wget - Non-interactive network downloader
- It is used to download content from both web and FTP sites.
- Usage: `wget [OPTIONS] [URI]`
- Example:
    - `wget https://karthikuj.github.io/images/7uring.png`

## ssh - Secure SHell
- It is a remote login and administration program.
- Before SSH, Telnet was used for the same purpose but it wasn't secure because the communication was in plaintext.
- By default in runs on port 22.
- Usage: `ssh [username@][server]`
- You can also execute a single command on the system instead of opening a shell session like this - `ssh tim@avicii.com ls`
- it is possible to launch and run an X client program (a graphical application) on a remote system and have its display appear on the local system, like so - `ssh -X remote-sys` and in the shell session that opens just start a GUI application such as `xload`. On some systems, you may need to use the `-Y` option rather than the `-X` option to do this.

## scp - Secure Copy
- It is used to securely copy files between remote hosts and local hosts
- Usage:
    - `scp source destination`
    - `scp [username@][server:]path [username@][server:]path`
- Examples:
    - `scp remote-sys:document.txt .`
    - `scp bob@remote-sys:document.txt .`