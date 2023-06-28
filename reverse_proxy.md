# Nginx Reverse Proxy

## What are ports?
In computer networking, a port or port number is a number assigned to uniquely identify a connection endpoint and to direct data to a specific service. 

Within an OS, a port is a logical construct that identifies a specific process or a type of network service.

## What is a reverse proxy? How is it different to a proxy?

A proxy (or forward proxy) enables computers isolated on a private network to connect to the public internet. A reverse proxy enables computers on the internet to access a private subnet.

<REVERSE/PROXY DIAGRAM>

## What is Nginx's default configuration
The default configuration for Nginx is proxy.

## How do you set up a Nginx reverse proxy?
1. Install Nginx on your Windows or Linux server.
2. Add the Nginx proxy_pass setting in a virtual host or the default config file.
3. Map a context root to the URL of a backend server. (Optional - set headers for the Nginx reverse proxy to use with the backend).
4. Restart Nginx reverse proxy and test the reverse proxy setup