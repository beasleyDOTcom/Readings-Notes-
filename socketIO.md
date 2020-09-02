# socket.io

## What is the benefit of transforming data into packets?
Reason 1: Transmission of data results in errors or
lost data. Breaking the data into small packets
makes error detection easier.
Reason 2: Most networks use shared media. To
ensure fair access to all users, a network cannot
allow one user to deny access to others.
resource: http://cs.gettysburg.edu/~jfink/courses/cs322slides/2-12.pdf
## UDP is often refereed to as a connectionless protocol. Why is this?
Because it allows "data to be exchanged without setting up a link between processes. Each unit of data, with all the necessary information to route it to the intended destination, is transferred independent of other data packets and can travel over different paths to reach the final destination. Some data packets might be lost in transmission or might arrive out of sequence to other data packets."

UDP is a connectionless protocol. It is known as a datagram protocol because it is analogous to sending a letter where you don't acknowledge receipt.
resource: https://docs.oracle.com/cd/E19620-01/805-4041/6j3r8iu2f/index.html#:~:text=Some%20data%20packets%20might%20be,you%20don't%20acknowledge%20receipt.
## Can a socket server application have multiple socket connections? 
yes, but they all have to be on the same port if that's your question.
## Can a socket connection application be connected to multiple socket servers?
yes. 

## Can an application be both a socket server and a socket connection?
No, I don't think so.
## Document the following Vocabulary Terms
Term
## OSI Model
The Open Systems Interconnection (OSI) model describes seven layers that computer systems use to communicate over a network. It was the first standard model for network communications, adopted by all major computer and telecommunication companies in the early 1980s

The modern Internet is not based on OSI, but on the simpler TCP/IP model. However, the OSI 7-layer model is still widely used, as it helps visualize and communicate how networks operate, and helps isolate and troubleshoot networking problems.

OSI was introduced in 1983 by representatives of the major computer and telecom companies, and was adopted by ISO as an international standard in 1984.

OSI Model Explained: The OSI 7 Layers
OSI 7 layers

We’ll describe OSI layers “top down” from the application layer that directly serves the end user, down to the physical layer.

7. Application Layer

The application layer is used by end-user software such as web browsers and email clients. It provides protocols that allow software to send and receive information and present meaningful data to users. A few examples of application layer protocols are the Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), Post Office Protocol (POP), Simple Mail Transfer Protocol (SMTP), and Domain Name System (DNS).

6. Presentation Layer

The presentation layer prepares data for the application layer. It defines how two devices should encode, encrypt, and compress data so it is received correctly on the other end. The presentation layer takes any data transmitted by the application layer and prepares it for transmission over the session layer.

5. Session Layer

The session layer creates communication channels, called sessions, between devices. It is responsible for opening sessions, ensuring they remain open and functional while data is being transferred, and closing them when communication ends. The session layer can also set checkpoints during a data transfer—if the session is interrupted, devices can resume data transfer from the last checkpoint.

4. Transport Layer

The transport layer takes data transferred in the session layer and breaks it into “segments” on the transmitting end. It is responsible for reassembling the segments on the receiving end, turning it back into data that can be used by the session layer. The transport layer carries out flow control, sending data at a rate that matches the connection speed of the receiving device, and error control, checking if data was received incorrectly and if not, requesting it again.

3. Network Layer

The network layer has two main functions. One is breaking up segments into network packets, and reassembling the packets on the receiving end. The other is routing packets by discovering the best path across a physical network. The network layer uses network addresses (typically Internet Protocol addresses) to route packets to a destination node.

2. Data Link Layer

The data link layer establishes and terminates a connection between two physically-connected nodes on a network. It breaks up packets into frames and sends them from source to destination. This layer is composed of two parts—Logical Link Control (LLC), which identifies network protocols, performs error checking and synchronizes frames, and Media Access Control (MAC) which uses MAC addresses to connect devices and define permissions to transmit and receive data.

1. Physical Layer

The physical layer is responsible for the physical cable or wireless connection between network nodes. It defines the connector, the electrical cable or wireless technology connecting the devices, and is responsible for transmission of the raw data, which is simply a series of 0s and 1s, while taking care of bit rate control.

Advantages of OSI Model
The OSI model helps users and operators of computer networks:

Determine the required hardware and software to build their network.
Understand and communicate the process followed by components communicating across a network. 
Perform troubleshooting, by identifying which network layer is causing an issue and focusing efforts on that layer.
The OSI model helps network device manufacturers and networking software vendors:

Create devices and software that can communicate with products from any other vendor, allowing open interoperability
Define which parts of the network their products should work with.
Communicate to users at which network layers their product operates – for example, only at the application layer, or across the stack.
resource: https://www.imperva.com/learn/application-security/osi-model/#:~:text=What%20Is%20the%20OSI%20Model,companies%20in%20the%20early%201980s
## TCP Model
Support for a flexible architecture
Adding more system to a network is easy.
In TCP/IP, the network remains intact until the source, and destination machines were functioning properly.
TCP is a connection-oriented protocol.
TCP offers reliability and ensures that data which arrives out of sequence should put back into order.
TCP allows you to implement flow control, so sender never overpowers a receiver with data.
Four Layers of TCP/IP

TCP/IP Conceptual Layers
The functionality of the TCP/IP model is divided into four layers, and each includes specific protocols.

TCP/IP is a layered server architecture system in which each layer is defined according to a specific function to perform. All these four layers work collaboratively to transmit the data from one layer to another.

Application Layer
Transport Layer
Internet Layer
Network Interface


Application Layer
Application layer interacts with an application program, which is the highest level of OSI model. The application layer is the OSI layer, which is closest to the end-user. It means the OSI application layer allows users to interact with other software application.

Application layer interacts with software applications to implement a communicating component. The interpretation of data by the application program is always outside the scope of the OSI model.

Example of the application layer is an application such as file transfer, email, remote login, etc.

The function of the Application Layers are:
Application-layer helps you to identify communication partners, determining resource availability, and synchronizing communication.
It allows users to log on to a remote host
This layer provides various e-mail services
This application offers distributed database sources and access for global information about various objects and services.
Transport Layer
Transport layer builds on the network layer in order to provide data transport from a process on a source system machine to a process on a destination system. It is hosted using single or multiple networks, and also maintains the quality of service functions.

It determines how much data should be sent where and at what rate. This layer builds on the message which are received from the application layer. It helps ensure that data units are delivered error-free and in sequence.

Transport layer helps you to control the reliability of a link through flow control, error control, and segmentation or de-segmentation.

The transport layer also offers an acknowledgment of the successful data transmission and sends the next data in case no errors occurred. TCP is the best-known example of the transport layer.

Important functions of Transport Layers:
It divides the message received from the session layer into segments and numbers them to make a sequence.
Transport layer makes sure that the message is delivered to the correct process on the destination machine.
It also makes sure that the entire message arrives without any error else it should be retransmitted.
Internet Layer
An internet layer is a second layer of the TCP/IP model. It is also known as a network layer. The main work of this layer is to send the packets from any network, and any computer still they reach the destination irrespective of the route they take.

The Internet layer offers the functional and procedural method for transferring variable length data sequences from one node to another with the help of various networks.

Message delivery at the network layer does not give any guaranteed to be reliable network layer protocol.

Layer-management protocols that belong to the network layer are:

Routing protocols
Multicast group management
Network-layer address assignment.
The Network Interface Layer
Network Interface Layer is this layer of the four-layer TCP/IP model. This layer is also called a network access layer. It helps you to defines details of how data should be sent using the network.

It also includes how bits should optically be signaled by hardware devices which directly interfaces with a network medium, like coaxial, optical, coaxial, fiber, or twisted-pair cables.

A network layer is a combination of the data line and defined in the article of OSI reference model. This layer defines how the data should be sent physically through the network. This layer is responsible for the transmission of the data between two devices on the same network.

Differences between OSI and TCP/IP Models


Here, are some important differences between the OSI and TCP/IP model:

OSI Model	TCP/IP model
It is developed by ISO (International Standard Organization)	It is developed by ARPANET (Advanced Research Project Agency Network).
OSI model provides a clear distinction between interfaces, services, and protocols.	TCP/IP doesn't have any clear distinguishing points between services, interfaces, and protocols.
OSI refers to Open Systems Interconnection.	TCP refers to Transmission Control Protocol.
OSI uses the network layer to define routing standards and protocols.	TCP/IP uses only the Internet layer.
OSI follows a vertical approach.	TCP/IP follows a horizontal approach.
OSI model use two separate layers physical and data link to define the functionality of the bottom layers.	TCP/IP uses only one layer (link).
OSI layers have seven layers.	TCP/IP has four layers.
OSI model, the transport layer is only connection-oriented.	A layer of the TCP/IP model is both connection-oriented and connectionless.
In the OSI model, the data link layer and physical are separate layers.	In TCP, physical and data link are both combined as a single host-to-network layer.
Session and presentation layers are not a part of the TCP model.	There is no session and presentation layer in TCP model.
It is defined after the advent of the Internet.	It is defined before the advent of the internet.
The minimum size of the OSI header is 5 bytes.	Minimum header size is 20 bytes.
Most Common TCP/IP Protocols
Some widely used most common TCP/IP protocol are:

TCP:
Transmission Control Protocol is an internet protocol suite which breaks up the message into TCP Segments and reassembling them at the receiving side.

IP:
An Internet Protocol address that is also known as an IP address is a numerical label. It is assigned to each device that is connected to a computer network which uses the IP for communication. Its routing function allows internetworking and essentially establishes the Internet. Combination of IP with a TCP allows developing a virtual connection between a destination and a source.


HTTP:
The Hypertext Transfer Protocol is a foundation of the World Wide Web. It is used for transferring webpages and other such resources from the HTTP server or web server to the web client or the HTTP client. Whenever you use a web browser like Google Chrome or Firefox, you are using a web client. It helps HTTP to transfer web pages that you request from the remote servers.

SMTP:
SMTP stands for Simple mail transfer protocol. This protocol supports the e-mail is known as a simple mail transfer protocol. This protocol helps you to send the data to another e-mail address.

SNMP:
SNMP stands for Simple Network Management Protocol. It is a framework which is used for managing the devices on the internet by using the TCP/IP protocol.

DNS:
DNS stands for Domain Name System. An IP address that is used to identify the connection of a host to the internet uniquely. However, users prefer to use names instead of addresses for that DNS.

TELNET:
TELNET stands for Terminal Network. It establishes the connection between the local and remote computer. It established connection in such a manner that you can simulate your local system at the remote system.

FTP:
FTP stands for File Transfer Protocol. It is a mostly used standard protocol for transmitting the files from one machine to another.

Advantages of TCP/IP
Here, are pros/benefits of using the TCP/IP model:

It helps you to establish/set up a connection between different types of computers.
It operates independently of the operating system.
It supports many routing-protocols.
It enables the internetworking between the organizations.
TCP/IP model has a highly scalable client-server architecture.
It can be operated independently.
Supports a number of routing protocols.
It can be used to establish a connection between two computers.
Disadvantages of TCP/IP
Here, are few drawbacks of using the TCP/IP model:

TCP/IP is a complicated model to set up and manage.
The shallow/overhead of TCP/IP is higher-than IPX (Internetwork Packet Exchange).
In this, model the transport layer does not guarantee delivery of packets.
Replacing protocol in TCP/IP is not easy.
It has no clear separation from its services, interfaces, and protocols.
Summary:
The full form of TCP/IP is Transmission Control Protocol/ Internet Protocol.
TCP supports flexible architecture
Four layers of TCP/IP model are 1) Application Layer 2) Transport Layer 3) Internet Layer 4) Network Interface
Application layer interacts with an application program, which is the highest level of OSI model.
Internet layer is a second layer of the TCP/IP model. It is also known as a network layer.
Transport layer builds on the network layer in order to provide data transport from a process on a source system machine to a process on a destination system.
Network Interface Layer is this layer of the four-layer TCP/IP model. This layer is also called a network access layer.
OSI model is developed by ISO (International Standard Organization) whereas TCP/IP model is developed by ARPANET (Advanced Research Project Agency Network).
An Internet Protocol address that is also known as an IP address is a numerical label.
HTTP is a foundation of the World Wide Web.
SMTP stands for Simple mail transfer protocol which supports the e-mail is known as a simple mail transfer
SNMP stands for Simple Network Management Protocol.
DNS stands for Domain Name System.
TELNET stands for Terminal Network. It establishes the connection between the local and remote computer
FTP stands for File Transfer Protocol. It is a mostly used standard protocol for transmitting the files from one machine to another.
The biggest benefit of TCP/IP model is that it helps you to establish/set up a connection between different types of computers.
TCP/IP is a complicated model to set up and manage.

resource: https://www.guru99.com/tcp-ip-model.html

## TCP
TCP/IP stands for Transmission Control Protocol/ Internet Protocol. It is specifically designed as a model to offer highly reliable and end-to-end byte stream over an unreliable internetwork.
## UDP
In computer networking, the User Datagram Protocol (UDP) is one of the core members of the Internet protocol suite. The protocol was designed by David P. Reed in 1980 and formally defined in RFC 768. With UDP, computer applications can send messages, in this case referred to as datagrams, to other hosts on an Internet Protocol (IP) network. Prior communications are not required in order to set up communication channels or data paths.

UDP uses a simple connectionless communication model with a minimum of protocol mechanisms. UDP provides checksums for data integrity, and port numbers for addressing different functions at the source and destination of the datagram. It has no handshaking dialogues, and thus exposes the user's program to any unreliability of the underlying network; there is no guarantee of delivery, ordering, or duplicate protection. If error-correction facilities are needed at the network interface level, an application may use Transmission Control Protocol (TCP) or Stream Control Transmission Protocol (SCTP) which are designed for this purpose.

UDP is suitable for purposes where error checking and correction are either not necessary or are performed in the application; UDP avoids the overhead of such processing in the protocol stack. Time-sensitive applications often use UDP because dropping packets is preferable to waiting for packets delayed due to retransmission, which may not be an option in a real-time system.[1]
resource: https://en.wikipedia.org/wiki/User_Datagram_Protocol
## Packets
a network packet is a formatted unit of data carried by a packet-switched network. A packet consists of control information and user data;[1] the latter is also known as the payload. Control information provides data for delivering the payload (e.g., source and destination network addresses, error detection codes, or sequencing information). Typically, control information is found in packet headers and trailers.

In packet switching, the bandwidth of the transmission medium is shared between multiple communication sessions, in contrast to circuit switching, in which circuits are preallocated for the duration of one session and data is typically transmitted as a continuous bit stream.


Contents
1	Terminology
2	Architecture
3	Framing
4	Contents
5	Examples
5.1	IP packets
5.2	NASA Deep Space Network
5.3	MPEG packetized stream
5.4	NICAM
6	See also
7	References
Terminology
In the seven-layer OSI model of computer networking, packet strictly refers to a protocol data unit at layer 3, the network layer.[citation needed] A data unit at layer 2, the data link layer, is a frame. In layer 4, the transport layer, the data units are segments and datagrams. Thus, in the example of TCP/IP communication over Ethernet, a TCP segment is carried in one or more IP packets, which are each carried in one or more Ethernet frames.

Architecture
The basis of the packet concept is the postal letter: the header is like the envelope, the payload is the entire content inside the envelope, and the footer would be your signature at the bottom.[2]

Network design can achieve two major results by using packets: error detection and multiple host addressing.[citation needed]

resource: https://en.wikipedia.org/wiki/Network_packet