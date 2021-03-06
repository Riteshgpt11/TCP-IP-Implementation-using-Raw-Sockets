# TCP-IP-Implementation-using-Raw-Sockets
Implementation of TCP/IP stack using RAW sockets

DESCIPTION OF OUR APPROACH
============================
We divided the project into the following steps:
 - Parsed the given URL and extract the Host name and path name
 - Extracted the source and destination IP Addresses
 - Created appropriate raw sockets and made sure they are sending and receiving data without any protocol error
 - Contructed the IP and TCP headers using struct pack
 - Calculated the checksum of TCP header and IP Header
 - Implemented the 3 way handshake 
 - Constructed the HTTP GET request and Sent acknowledgements to the recieved packets
 - Implemented congestion control mechanism
 - Checked for vaild HTTP status code "200 OK" and prints error message for other HTTP status code other than 200.
 - Extracted body from HTTP response
 - Created file in the current directory that was named on the basis of the end path of the URL.
   If URL ended with '/' or if it does not include any path, default filename 'index.html' is created
 - Wrote html page into that file
 - Teared down the connection after receiving the complete data
 - Used wget to directly download html page from the web server for comparision with the recieved packet from raw sockets
 - Validated the received data, by using diff and md5sum commands
 - Using the command line, we were able to create files in the current directory which contained the downloaded HTML content.

 
 TCP/IP FEATURES IMPLEMENTED:
==============================

1. Basic HTTP: Constructed a simple HTTP GET request and later verify the response for 200 OK code and extract the body

2. TCP : The following,
 
 - constructing TCP segments and calculating checksums
 - Intial Handshake mechanism
 - Congestion control mechanism with initial cwnd = 1 with a timeout functionality
 - Handling out of order packets 
 - Graceful teardown

3. IP : 
 - constructing IP datagrams
 - receiving IP datagrams and extracting the length, protocol and other fields 
 

 CHALLENGES FACED 
===================

1. Constructing Raw Sockets with Headers in exact form  and carrying out handshake was challenging.
2. Calculation of Checksum was cumbersome
3. Finding the exact the combo of domain,family and protocol for receiving socket was quite tricky.
4. Managing the sequence and ack numbers during the communication
5. Implementing congestion control mechanism was little tricky as well.
6. Removing the extra characters from the HTTP chunked responses was initially challenging, but got resolved later when used HTTP/1.0
7. Sorting and arranging the packets in sequence took a lot of time


 TESTING 
=========

Tested with several URLs within college intranet that include project page, fakebook, 2MB,10MB and 50MB log files too. Verified using diff and md5sum
Tested with invalid urls, more than 2 arguments, and no arguments


INDIVIDUAL CONTRIBUTION
==============================
Riteshkumar Gupta - 001280361

	- Constructing Raw sockets for sending and receiving, parsing of URL
	- Extracted Source Address
	- Implemented 3 way handshake
	- Handled Sending and Recieving of packets
	- Handled Congestion mechanism, 
	- Handled Sequencing and Ordering of packets 
	- Performed Testing using diff, md5sum

Prajwal Patil - 001280390
	- Constructing TCP Header and IP Headers
	- Extracted Destination Address
	- Computed Checksum, Created HTTP GET header
	- Handled HTTP status code and extracted body from HTTP response
	- Created the function to save the HTML file
	- Handled Congestion mechanism
	- Built timer function
