
2024-09-14 23:26

Tags:

# Webserver with Python

![[serverworking.png]]

A webserver is a a software like thingy made on top of a bunch of computers where when a person sends a signal they receive it and then do some processing or something on it and then send an output.

All this happens using an HTTP protocol 

Now HTTP protocol works using a TCP connection; so basically what happens is that a TCP connection is made first and then an HTTP response is sent when the server receives it they create a response and send another HTTP response back after that the TCP connection is closed.

**http://localhost:8888/hello**

http -> protocol
localhost -> host name
8888 -> port number
hello -> path

to send a request and expect a response we do

GET /hello HTTP/1.1

GET -> to show that we expect a response
HTTP/1.1 -> the version of the protocol

HTTP/1.1 200 OK 

200 -> HTTP status code
OK -> HTTP status code reason phrase



# References
---


	