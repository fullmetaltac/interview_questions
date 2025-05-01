# Table of Contents
- [Table of Contents](#table-of-contents)
    - [What function does DNS play on a network?](#what-function-does-dns-play-on-a-network)
    - [What is HTTP?](#what-is-http)
    - [What are HTTP status codes?](#what-are-http-status-codes)
    - [Describe the most common HTTP methods/verbs](#describe-the-most-common-http-methodsverbs)
    - [What is an HTTP proxy and how does it work?](#what-is-an-http-proxy-and-how-does-it-work)
    - [Describe briefly how HTTPS works.](#describe-briefly-how-https-works)
    - [What is SMTP?](#what-is-smtp)
    - [UDP](#udp)
    - [TCP](#tcp)
  - [References](#references)

### What function does DNS play on a network?

It's on the core for any environment, responsible to translate IP addresses into names, **DNS** can also provides a load balancer layer using geolocation, service discovery using SRV entry and a lot of others features, like domain ownership confirmation using TXT entries ( useful to generate SSL certs, for example )

### What is HTTP?

**HTTP** (hypertext transport protocol) it's a protocol that defines how messages are formated and transmitted via web, and what actions webservers and browsers should take in response of various commands.

### What are HTTP status codes?

HTTP status codes are predefined status of the task at the server
- `1xx` - represents informational responses
- `2xx` - represents succesful responses
- `3xx` - represents redirect responses
- `4xx` - represents client errors
- `5xx` - represents server errors

The most commmons status codes are:  
- `200` - SUCCESS/OK
- `201` - CREATED - used by POST or PUT methods
- `304` - NOT MODIFIED - used in conditional GET Request to reduce bandwitdth use
- `400` - BAD REQUEST - This can be due to validation errors or missing input data
- `404` - NOT FOUND - Resource method is not available
- `500` - INTERNAL SERVER ERROR - server threw some exceptions while running the method
- `502` - BAD GATEWAY - Server was not able to get the response from another upstream server

### Describe the most common HTTP methods/verbs

- `GET` - Read only operation, used to fetch detail from the server, downloads
- `POST` - This method is used for the creationg of new resources on the server
- `PUT` - This method is used to update existing resource on the server or to replace the resource,  
  PUT it's indepotent, and POST isn't, with PUT you can update a resource N times, but if you try  
  with post you will create N resources. PUT - can create resources.
- `PATCH` - Applies a partial update to a resource and doesn't create a new resource
- `DELETE` - This method is used to delete the resource on the server
- `TRACE` - Provides a loop back test along the path to the target resource providing a useful debugging mechanism.
- `OPTIONS` - Fetches the list of supported options of resources present on the server.

### What is an HTTP proxy and how does it work?

An HTTP **proxy** it's a service that forwards HTTP connections, for example a user A want's to access a server www.b.com, but for security reasons the user cannot have direct access on internet, so the user's browser will ask for the HTTP proxy to access the website, the webserver from www.b.com will receive a HTTP message from the proxy and will answer as usual, but in the http HEADER from the message will be changed by the HTTP proxy server who will add or change some headers like User-Agent, X-Forwarded-For, used a lot by companies that need to control their users Internet access.

### Describe briefly how HTTPS works.

**HTTPS** use the same HTTP protocol but creates a security layer(tunnel) using SSL/TLS, on top of it, this prevents anyone modify or inspect what's happening inside this tunnel and ensure the client it's communicating with the right server. The SSL handshake is established and after that all HTTP responses are send by. The SSL uses both types of encryption, symmetrical and assymetrical, first when the key exchange happens, a assymetrical encriptions is put in place to the result of the key exchange be a symmetrical encryption.

### What is SMTP?

**SMTP** ( Simple Mail transport protocol) works in the application layer, and uses a process called "store and forward", working close to a MTA (Mail Tranfer Agent), this MTA service sends via SMTP a package with the messages, when this message arrives at the destination, the client will use POP3/IMAP to download it.

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
    