# Client-Server Basics

## Summary 

Cover how a client asks a server for something over networks, and the pieces in between.

## Learning Objectives

- Client-Server model
- DNS, client, server, port, protocol, network

## Notes

**Service, Client, Server:** A example for how these terms connect is a person using a browser to navigate to a website. The browser is the **client** that requests the webpage, and the **server** is the system that provides it.

**Request and Response:** Continuing from the previous example, a person can use a browser to **request** a webpage from a server, which then sent the webpage to the client.

**Protocol:** A protocol can be a variety of things such as which commands a client and server understands, how a request is structured, what syntax is used, response to request, etc.

**Port:** A port is used to identify a specific service running on a system. When a client wants to access a service on a server it must use the correct port.

**DNS:** DNS stands for Domain Name Service. When you enter the name of a website, DNS resolves it to the server's location. These location coordinates are called an Internet Protocol (IP) address. 

### HTTP 

**Hypertext Transfer Protocol (Secure)** or **HTTP(S)** is a stateless client-server protocol used for the World Wide Web. This means that each request is proccessed independently, without the server retatining information about previous requests.

#### HTTP COMMANDS

The 9 core commands (or methods) are:
- GET
- POST
- PUT
- DELETE
- PATCH
- HEAD
- OPTIONS
- CONNECT
- TRACE

**GET:**  Used to retrieve resources from web servers. When you open a browser (client) and type "https://google.com", the browser constructs the message using information you provide and other fields defined in the HTTP specifications. When the server receives the request, it sends a respone including a status code (indicating response) and information requested. 
