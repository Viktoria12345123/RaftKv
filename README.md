
# RaftKV: Distributed Key-Value Store with Raft Consensus

RaftKV is a distributed key-value store implementation based on the Raft consensus algorithm. The system ensures that multiple server instances agree on the order of operations, even in the presence of failures. It includes leader election, log replication, and consistency across nodes in the cluster.

## Features

- **Leader Election**: Nodes elect a leader to handle incoming requests, ensuring fault tolerance and consistency.
- **Log Replication**: The leader replicates log entries to follower nodes to maintain consistency.
- **Heartbeat Mechanism**: The leader sends periodic heartbeats to followers to prevent them from starting an election.
- **Raft Consensus**: Ensures fault-tolerant and consistent processing of operations (e.g., `put` and `get` requests).

## Components

### 1. RaftServer
The core component of the RaftKV system, responsible for:
- **Node State**: Manages the state of the node (Follower, Candidate, Leader).
- **Log Replication**: Leader appends log entries and replicates them to followers.
- **Election**: Periodic elections to select a new leader if no heartbeats are received.
- **Request Handling**: Processes client `put` and `get` requests.

### 2. RaftLog
Handles log management:
- **Log Entries**: Each entry contains a command, term, and index.
- **Appending Logs**: The leader appends the log entry to its local log and replicates it to followers.

### 3. RaftClient
Enables clients to interact with the RaftKV system:
- **Client Requests**: Send `put` and `get` requests to servers.
- **Communication**: Uses gRPC for server communication.

### 4. LogEntry
Represents a single log entry in the Raft log:
- **Command**: The operation being performed (e.g., `put` or `get`).
- **Term**: The term during which the entry was added.
- **Index**: The entry's index in the log.

## Setup Instructions

### Prerequisites
- Java 11 or higher
- Maven for dependency management
- gRPC library for client-server communication
- A cluster of at least 2 nodes for full functionality

### Running the Server

1. **Clone the repository**:
   ```bash
   git clone <repo_url>
   cd RaftKV

