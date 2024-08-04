# Wireshark - Analyze Your First Packet 



<h2>Solutions</h2>
1. Identify the source and destination IP addresses involved in this web browsing session.
* On the title bar, type <mark>`ip.addr == 142.250.1.139`</mark> to filter for traffic associated with a specific IP address. Select the first packet that contains `TCP` on the info field. `addr` means either the source or the destination IP. 

![Screenshot 2024-08-03 at 10 16 06 PM](https://github.com/user-attachments/assets/ebd1c5fa-63b1-4cf0-8a5f-a33a134cf8a7)

* On the title bar, type `ip.src == 142.250.1.139` to filter for traffic associated with a specific IP address. `src` means it is where the packet comes from.
  
![Screenshot 2024-08-03 at 10 16 18 PM](https://github.com/user-attachments/assets/6902df01-4976-4e07-9cb0-c46497710d52)

* On the title bar, type `ip.dst == 142.250.1.139` to filter for traffic associated with a specific IP address. `dst` means it is where the packet goes to.
  
![Screenshot 2024-08-03 at 10 16 25 PM](https://github.com/user-attachments/assets/8d04a66f-5345-4159-b6ee-f81055f0eb16)

* On the title bar, type `eth.addr == 42:01:ac:15:e0:02` to filter for traffic associated with a specific Ethernet MAC address. `addr` means either the source or the destination IP. 

![Screenshot 2024-08-03 at 10 16 34 PM](https://github.com/user-attachments/assets/15e0fe8e-c5ea-4d6f-b9c5-9cc484360045)

2. Examine the protocols that are used when the user makes the connection to the website.
* The TCP destination port of this TCP packet is 80 when `ip.addr == 142.250.1.139` which contains the initial web request to an HTPP website that will typically be listening on TCP port 80.

![Screenshot 2024-08-03 at 10 16 41 PM](https://github.com/user-attachments/assets/c77ee603-1fd5-4c48-8266-5d2075bc5d90)

* The protocol destination port is TCP when Etherenet address was `42:01:ac:15:e0:02`. Source address is `172.21.224.2` and the destination address is `35.235.244.34`. 

![Screenshot 2024-08-03 at 10 16 47 PM](https://github.com/user-attachments/assets/ab7c4336-a70f-4e97-8193-36e191d9e417)

3. Analyze the data packet to identify the type of information sent and received by the systems that connect to each other when the network data is captured.
* On the title bar, type `tcp.port == 80` to filter for traffic associated with a specific port number. `tcp.port == 80` means only the tcp port is 80 will be shown. 
  
![Screenshot 2024-08-03 at 10 16 56 PM](https://github.com/user-attachments/assets/dc75a8bf-a867-4dc7-a891-a75737f0f551)

* When the filter `tcp.port == 80` sets in play, the time to live is 64.
* `Time to Live`: A field in the Internet Protocol (IP) header that indicates the maximum amount of time an IP packet is allowed to exist in the network before it is discarded if it has not reached its destination. TTL is used to prevent packets from circulating indefinitely in the network, which could happen in the case of routing loops. It can be used as a basic security measure to limit how far packets can propagate through the network.
  
![Screenshot 2024-08-03 at 10 17 05 PM](https://github.com/user-attachments/assets/501d03d2-9536-43f0-9654-1e4a16bc7764)

* When the filter `tcp.port == 80` sets in play, the Frame Number is 37 and Frame Length is 54 bytes.
* `Frame Number`: This is essentially the sequence number of a packet within a particular capture. It helps you identify and refer to packets more easily. In your case, a frame number of 37 means it's the 37th packet captured since the beginning of the capture session. This number is assigned sequentially as packets are captured, starting with the number 1 for the first packet.

* `Frame Length`: This indicates the size of the packet, including all headers and payload, measured in bytes. The frame length of 54 bytes means the total size of the packet is 54 bytes. This size includes everything from the lowest layer (physical layer) up to the highest layer present in the packet that Wireshark can decode. It's useful for understanding the size of the data being transmitted and can help in various analyses, such as identifying potential issues with packet sizes that might indicate fragmentation or other problems.
*
* ![Screenshot 2024-08-03 at 10 17 14 PM](https://github.com/user-attachments/assets/5e4185fd-a520-434b-b673-dad29bdd0d77)
