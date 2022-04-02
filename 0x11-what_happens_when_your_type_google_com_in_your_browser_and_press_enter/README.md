What happens when you type https://www.google.com in your browser and press Enter.

Have you ever thought of what happens when you type https://www.google.com in your browser and press Enter? think no further as you are about to find out what goes on behind the scenes of your browser. It takes a lot of chain actions to get you a webpage in just milliseconds, I’ll highlight briefly how these various topics work together to deliver the webpage we see.
Fortunate for us, our user specified that this is a URL or Uniform Resource Location (so we’ll skip the URL parsing stage) and specified that the protocol is HTTPS which we know runs on the TCP port 443.
I believe that you have seen a set of four octets (8 binary bits), something like 123.45.67.89 before. This is what is referred to as an IP address, specifically they are version 4 (IPv4), Version 6 or IPv6. Computers communicate to each other through IPs, but as you guessed, humans aren’t good at cramming these numbers. Imagine having to know the exact IP of every site you visit. If you think that taxi drivers memorizing 25,000 streets is quite a feat, think again, what it would be like memorizing close to 2 billion websites. Okay to be fair, an average person only visits common websites like social media sites, school or work portals, and wiki sites, but still, no one wants to cram random numbers just to access their favorite site.

DNS Request
DNS simply means 'Domain Name System'. It is a naming system used to keep records of computers or services over the internet communicating to each other using the Internet Protocol. Think of DNS like a phonebook for the internet. Because we can easily remember words, DNS simply translates domain names into IP addresses, for example, google.com would be 216.58.210.142 or wikipedia.org 91.198.174.192. I recommend this cartoon explanation of how DNS works, it will go in-depth into how the resolver, Top Level Domains, Authoritative Name Servers work.
So when a user types “https://www.google.com” in their favorite browser (Google, Firefox, Safari, Edge or Opera) and presses the “Enter” key, a DNS request is made and performs a DNS lookup. The browser checks if the domain is in its cache. If not found, the browser calls a function to do the lookup which checks if the hostname can be resolved by referencing the local hosts file before trying to resolve the hostname through DNS. If it’s not cached or found in the hosts file, a request to the DNS server is made configured in the local router or the ISP’s (Internet Service Provider’s) caching DNS server. The DNS server then follows the ARP (Address Resolution Protocol) Process to perform a lookup using the MAC address and route tables to find the target IP.
After the network library has the IP address of either our DNS server or the default gateway the DNS client establishes a socket to UDP (User Datagram Protocol) port 53 on the DNS server, using a source port above 1023. If the response size is too large, TCP (Transmission Control Protocol) will be used instead. If the local/ISP DNS server does not have it, then a recursive search is requested and that flows up the list of DNS servers until an answer is returned. Once the browser receives the IP address of the destination server, it takes that and the given port number from the URL (443 since we are using HTTPS, the use of Secure Socket Layer as opposed to HTTP which runs on port 80 of TCP/IP) and then headers are wrapped to form packets that are forwarded by NAT (Network Address Translation) which translates private network addresses into globally unique addresses.

TCP Connection & TLS Handshake

The next step involves what they call a “handshake”. The server and the client agree on the particular key used and once verified, perform a handshake. A TLS (Transport Layer Security) connection from the Client establishes a public key and private key; the Client sends a Hello message to the Server and creates a handshake, using an encrypted symmetric algorithm. A connection between the server and client is established once the client verifies the server via a certificate during the TLS handshake. A finish (FIN) message is sent by the client to the server with the agreed symmetric key. During the TLS handshake, the HTTP version is decided e.g. HTTP/1.1 and HTTP/2.0.

GET request

The client sends the server a GET request and the server responds with a response code, 200 OK, in our case showing success, and the content in HTML form of www.google.com. This involves parsing the HTML and the server or web browser repeats this process for each content on the HTML page eg CSS, or image.

Firewall

A firewall monitors incoming and outgoing traffic over a network, in essence, whatever rules are set by a particular team to define what’s or who can access particular channels, think of it as a barrier between private and public internet.

Load balancer

A load balancer is a device that acts as a reverse proxy and distributes network or application traffic across a number of servers. In short, a load balancer serves to distribute requests across different servers, because obviously, Google doesn’t have a single server. Best engineering practices suggest that teams eliminate a single point of failure through various techniques.

Web server

A web server is a software program that serves web pages to web users (browsers). It serves static content, like simple HTML pages, images or plain text files using the HTTP or HTTPS protocols. Examples include Apache HTTP Server, Microsoft Internet Information Services (IIS), Nginx.

Application Server

An application server works with a web server to handle requests for dynamic content, from web applications, this is what handles the business logic of an application.

Database

A database is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a database management system (DBMS). In this case, the content of what you search will be stored in a database.
