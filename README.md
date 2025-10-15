# PCAP Programming Example

This project demonstrates how to capture and analyze network packets using the `libpcap` library in C. The provided C source code (`pcap_programming.c`) captures live network traffic on a specified network interface, applies a filter for TCP packets, and then parses and prints the Ethernet, IP, and TCP header information for each captured packet.

## Features

- Opens a live packet capture session on a specified network interface (`ens33` by default).
- Filters the captured packets to only process TCP packets.
- Parses Ethernet, IP, and TCP headers for each packet.
- Prints detailed header information, including:
  - Source and destination MAC addresses
  - Source and destination IP addresses
  - Source and destination TCP ports

## How It Works

1. **Ethernet Header Parsing:**  
   The program starts by interpreting the raw packet data as an Ethernet frame, extracting and printing the source and destination MAC addresses.

2. **IP Header Parsing:**  
   If the packet is an IP packet (EtherType 0x0800), the code parses the IP header to retrieve and display the source and destination IP addresses.

3. **TCP Header Parsing:**  
   If the IP protocol is TCP, the program further parses the TCP header to extract and print the source and destination port numbers.

4. **Packet Filtering:**  
   The program uses a BPF (Berkeley Packet Filter) expression to capture only TCP packets, reducing unnecessary processing.

## Requirements

- `libpcap` development headers and library.
- A network interface named `ens33` (or modify the source code to use your interface).
- C compiler (e.g., gcc).

## Notes

- Make sure your user has the necessary permissions to capture packets on the specified network interface.
- You may need to change `"ens33"` in the source code to the name of your network interface (e.g., `"eth0"`, `"wlan0"`).
- This is a basic example for educational purposes and does not handle all error cases or packet types.

