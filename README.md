# PostgreSQL Primary-Replica Setup with Docker Compose  

## Overview  
This project sets up a PostgreSQL database with one primary and one replica using Docker Compose. The primary database handles all writes and sends updates to the replica, which is kept in sync. The setup includes Patroni to manage automatic failover, ensuring high availability.  

If the primary database fails, Patroni promotes the replica to become the new primary automatically. This ensures the application continues to work without downtime.  

---

## Features  
- **Primary and Replica Databases**: Data is copied from the primary to the replica in real-time.  
- **Automatic Failover**: If the primary database goes down, the replica becomes the new primary automatically.  
- **Containerized Setup**: Everything runs in Docker containers, making it easy to manage and deploy.  
- **Custom Configurations**: Settings for PostgreSQL and Patroni are adjusted for smooth replication and failover.  

---

## Folder Structure  
```plaintext  
postgres-replication/  
├── data/  
│   ├── primary/         # Data for the primary database  
│   └── replica/         # Data for the replica database  
├── init-scripts/        # Initialization scripts for PostgreSQL  
├── patroni-config/      # Configuration files for Patroni  
├── docker-compose.yml   # File to run everything with Docker Compose  
```  

---

## How It Works  
1. **Primary and Replica Setup**  
   - The primary database is set up to allow replication.  
   - The replica connects to the primary and stays updated by applying changes sent by the primary.  

2. **Patroni for Failover**  
   - Patroni monitors the primary database.  
   - If the primary goes offline, Patroni promotes the replica to take over as the new primary automatically.  

3. **Docker for Easy Management**  
   - All components are packaged in Docker containers.  
   - Docker Compose handles starting, stopping, and managing the containers.  

---

