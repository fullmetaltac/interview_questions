# Table of Contents
- [Table of Contents](#table-of-contents)
    - [UDP](#udp)
    - [TCP](#tcp)
  - [References](#references)


### UDP

1. **Message-oriented**:  
<br>
UDP is a message-oriented protocol, and message means chunks of data that are delivered on the internet. UDP only delivers the message, without any handling like split or combine.

More specifically:  

- At the sender's end，when a UDP message is sent, the UDP protocol will get the data from the application layer, and it will only add the UDP header to the data, nothing else, then deliver it to the network layer.

- At the receiver's end，when getting a UDP message from the network layer, the UDP protocol will only remove the additional IP header on data without any other operations.  <br>

2.  **Unreliable**:

- UDP is connectionless, communication happens without connecting or disconnecting;
- UDP is unreliable, it will deliver whatever it has got, no cache is involved and it does not care about the delivery.
- UDP has no congestion control, data is sent at a constant speed. Even if the network is terrible, it will not adjust the speed, so it is inevitable to lose some packets. However it has the advantage of real-time applications, for example we will use UDP instead of TCP in telephone conference.

3. **Efficient**:  
<br>
Since there is no guarantee of delivery and no promise that data is not lost and arrives in orderly in UDP, it is not as complicated as TCP. It does not cost a lot in its header data with only 8 bytes, much less than TCP whose head data needs at least 20 bytes. So it can transport data efficiently.

![UDP](images/udp.png)

The UDP header consists of 4 fields:

- two port number of 16 bits, source port (optional) and destination port
- the length of the data
- checksum (IPv4 optional) which is used for error-checking of the header and the data.

4. **Transmission mode**:  
<br>
The transmission modes of UDP contains not only one-to-one, but also one-to-many, many-to-many, and many-to-one, which means UDP supports unicast, multicast and broadcast.

---

### TCP

1. **Header**:  
The header of TCP is much more complicated than UDP's:
![UDP](images/tcp.png)

When talking about the header of TCP, these fields are significant:

- Sequence Number: This number can guarantee that all the segments are ordered, and the opposite host can order the segments by it.
- Acknowledgment Number: This number indicates the next segment number that the opposite host expects, and everything before this has been received.
- Window Size: How many segments can the opposite host accept; it is used to control the flow.
- Identifier
  - URG=1: When this flag is set, that means this segment is urgent and should be prioritised.
  - ACK=1: Besides according to the TCP protocol, after connection, all the segments that transported should set the ACK=1.
  - PSH=1: When this flag is set, it means that the receiver should push the data to the application layer instead of store it in the caches until the cache is full.
  - RST=1: When this flag is set, it means that the TCP connection has a serious problem. It may need to reconnect. It also can be used to refuse invalid segments or requests.
  - SYN=1: When SYN is 1 and ACK is 0, it means that this is a connect request segment, while SYC is 1 and ACK is 1, it is a response that agrees to connect.
  - FIN=1: When this flag is set, it means that this is a request segment that asks for closing the connection.

2. **State machine**:  




## References
 - https://github.com/InterviewMap/CS-Interview-Knowledge-Map/blob/master/Network/Network_en.md
 - https://github.com/nairuzabulhul/.CodeBits/blob/master/InterviewQuestions/Top%20100%20Networking%20Interview%20Questions%20%26%20Answers.md
 - https://www.interviewbit.com/networking-interview-questions/
    