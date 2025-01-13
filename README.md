<h1>Exploring the OSI Model Through Wireshark</h1>


<h2>Description</h2>
The OSI (Open Systems Interconnection) model is a foundational concept in networking, dividing the communication process into seven distinct layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application. Each layer plays a unique role, from handling the physical transmission of data to enabling communication between software applications.

This repository explores the OSI model through practical analysis using Wireshark, a powerful tool for capturing and inspecting network traffic. By examining data at each layer, we can better understand how devices communicate over a network and how protocols function in real-world scenarios.

The goal of this project is to make the OSI model more tangible and relatable by showing how it works in practice. Whether you're learning the basics of networking, troubleshooting performance issues, or studying cybersecurity, using Wireshark to analyze the OSI layers can deepen your understanding of network behavior and provide valuable insights into communication processes.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Wireshark</b> 


<h2>Environments Used </h2>

- <b>macOS</b>

<h2>Walk-through:</h2>
<br>
<br>
<p align="left">
<b> Type the name of a university or website in your browser, ensuring that it uses the http protocol rather than https. For this example, I chose http://www.utexas.edu:80. Make sure you include http:// and :80 in the URL to guarantee the traffic is sent over HTTP on port 80, even if the site ultimately redirects to HTTPS. Do NOT press Enter yet; simply type the URL into the browser's address bar and pause for now.

Feel free to choose your own website for testing. Keep in mind that many modern websites will redirect HTTP requests to HTTPS locations, which is completely normal and a useful behavior to observe in your analysis..<b/>
<br>
<br>


<b> 1. Start Wireshark and select the network interface you want to use for capturing traffic. In this example, I selected the Wi-Fi interface eth0. Make sure to choose the appropriate interface based on your device’s configuration and the network you’re connected to.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/d1lNaZV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 2. Start capturing packets by clicking the blue shark fin icon located on the left-hand side of the Wireshark window. Once the capture begins, quickly switch to your browser and press Enter on the URL you typed earlier. After submitting the URL, wait a few seconds to allow the traffic to be captured, then return to Wireshark and stop the capture by clicking the red square in the left-hand corner next to the blue start icon.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/dOkoO2E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/fpXezxL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />


<b> 3. Your Wireshark capture should show packets numbered 1, 2, 3, and so on, indicating that traffic is being captured as expected.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/n6bSzZe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<b> 4. In the filter bar, type http and press Enter. If you wish to clear the filter later, simply delete the text in the filter area and press Enter again. If the site doesn't support HTTP, you might only see one or two HTTP packets, with the rest of the traffic being TLS-related, indicating the site has switched to HTTPS.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/2yKQFs4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 5. Double-click on the first HTTP packet that shows a "GET" in the info column. This will open the packet details, where you can observe the layers involved in the packet transmission. While the OSI model typically consists of seven layers, Wireshark combines the last three layers (Session, Presentation, and Application) into one for simplicity in packet analysis.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/iXbLpTX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 6. Expand the Hypertext Transfer Protocol (HTTP) layer, which is part of the Application Layer, to examine the captured GET request. In this example, the request is made to www.utexas.edu, using the HTTP/1.1 protocol. The key components of the request include the host (Host: www.utexas.edu), the type of content the client can accept, and various headers like User-Agent to identify the browser.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/OZUji1z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 7. Expand the Transmission Control Protocol (TCP) layer to inspect the details of the captured segment at the Transport Layer. In this example, the segment is sent from source port 49490 to destination port 80 (HTTP). The sequence and acknowledgment numbers provide information on the state of the TCP connection, with a sequence number of 1 and an acknowledgment number of 1. The segment length is 435 bytes, and it includes flags PSH (Push Function) and ACK (Acknowledgment). The TCP segment also provides window size information, indicating how much data the receiver is willing to accept.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/Z5cqG8Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 8. Expand the Internet Protocol Version 6 (IPv6) layer to examine the details of the network segment. In this example, the source address is 2603:8080:3e01:9616:a599:8195:331b:f58 and the destination address is 2620:12a:8000::4. It's important to note that the network layer can handle both IPv4 and IPv6 addresses, but in this case, the capture is using IPv6.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/NTfUTh6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<b> 9. Expand the Ethernet II layer to analyze the frame's data at the Data Link Layer. In this example, the source MAC address is 3c:22:fb:89:c3:51 (Apple) and the destination MAC address is 88:de:7c:8c:3d:6c (AskeyCompute). The "Type" field indicates the upper-layer protocol, which in this case is IPv6 (indicated by the value 0x86dd). This layer is responsible for delivering the frame to the correct device on the local network based on MAC addresses, and here, the frame is carrying an IPv6 packet.<b/> 
<br>
<br>
  <img src="https://i.imgur.com/8nsxQmi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<b> 10. Expand the Physical Layer to analyze the details of the captured frame. This frame, numbered 40, has a total length of 521 bytes (4168 bits) and was captured on the en0 interface. The encapsulation type is Ethernet, and it arrived on June 6, 2024, at 22:38:30 CDT. The frame contains multiple protocols, including Ethernet, IPv6, TCP, and HTTP, and is part of the overall communication captured in this session. This layer represents the transmission of raw data across the physical medium (wireless or wired) and includes timing information such as the arrival time, time delta, and other metrics relevant for analyzing network performance..<b/> 
<br>
<br>
  <img src="https://i.imgur.com/zSQVw9J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
