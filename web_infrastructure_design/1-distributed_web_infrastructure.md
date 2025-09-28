# Task 1: Distributed Web Infrastructure

## Infrastructure Components

### Additional Elements Added

#### 1. Load Balancer (HAproxy)
Solves scaling problems by using multiple servers to distribute traffic, prevents crashes from bottlenecking, and provides failsafe redundancy.

#### 2. Server 1
If Server 1 fails, Server 2 will continue operating. Distributes workload across multiple machines for better performance.

#### 3. Server 2  
If Server 2 fails, Server 1 will continue operating. Distributes workload across multiple machines for better performance.

## Load Balancer Configuration

### What distribution algorithm your load balancer is configured with and how it works
We will configure it with **Round Robin** algorithm:
- Distributes requests in circular order: Server 1 → Server 2 → Server 1 → Server 2
- Simple and fair distribution
- Good for servers with equal capacity

### Is your load-balancer enabling an Active-Active or Active-Passive setup, explain the difference between both

**Our Configuration: Active-Active**
- Load balancer sends traffic to both servers
- Both servers are running and actively handling requests
- Better resource utilization and higher total capacity

**Active-Passive Alternative:**
- Only one server handles requests while the second server sits in idle mode as backup
- Backup server only activates if the primary server fails
- Simpler but wastes resources

## Database Cluster Configuration

### How a database Primary-Replica (Master-Slave) cluster works
- **Primary:** Handles all WRITE operations (INSERT, UPDATE, DELETE)
- **Replica:** Handles READ operations (SELECT)
- Data replicates from Primary to Replica in one-way synchronization

### What is the difference between the Primary node and the Replica node in regard to the application
- **Primary:** Source of truth for all data
- **Writing data:** Application connects to Primary database
- **Reading data:** Application connects to either Primary or Replica database
- **Data flow:** Primary → Replica (one-way sync)

## Infrastructure Issues

### 1. Where are SPOF
- **Load Balancer:** If it fails, entire site goes down
- **Primary Database:** If it fails, no write operations possible

### 2. Security issues (no firewall, no HTTPS)
- **No Firewall:** Servers exposed to potential attacks
- **No HTTPS:** Data transmitted unencrypted over the network

### 3. No monitoring
- Can't see performance metrics
- Don't know if servers are healthy
- No alerts when problems occur
- No visibility into system status