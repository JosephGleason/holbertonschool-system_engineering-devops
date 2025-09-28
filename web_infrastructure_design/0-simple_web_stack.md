# Task 0: Simple Web Stack Infrastructure

## Infrastructure Components

### 1. What is a server?
A server is a computer that services other computers over a network. In my case, it's the machine at IP address 8.8.8.8 that hosts our site. It processes the requests and returns content.

### 2. What is the role of the domain name?
Domain name is the human readable equivalent to the IP address. It makes it easier to understand. In my case, it's www.foobar.com which translates to 8.8.8.8.

### 3. What type of DNS record is 'www' in www.foobar.com?
It's an A record that points to our server's IP address 8.8.8.8.

### 4. What is the role of the web server?
Nginx receives HTTP requests and serves static content or forwards dynamic requests to the application server. In our case, it sends dynamic requests to the application server.

### 5. What is the role of the application server?
Takes the request, reads code, executes it, makes database queries, makes calculations, and creates a response. In my case, it generates the final webpage, sends response back to Nginx and then to user.

### 6. What is the role of the database?
It stores/saves all user data, site content, and any app info it needs to run properly.

### 7. What is the server using to communicate with the computer of the user requesting the website?
It uses HTTP (HyperText Transfer Protocol).

## Issues with this Infrastructure

### 1. SPOF (Single Point of Failure)
Means one component failing and crashing the entire system. In my case, everything runs on one server. If anything fails, it brings down the whole system.

### 2. Downtime when maintenance needed
When we need to perform maintenance tasks such as:
- Deploy new code
- Restart Nginx
- Update MySQL database  
- Server reboot

The entire website goes offline because all services are running on a single server.

### 3. Cannot scale if too much incoming traffic
- Cannot add more servers as everything is tied to one machine
- Can't distribute load across multiple servers
- Single bottleneck handles all requests
- Causes lag and potential crashes when traffic exceeds server capacity