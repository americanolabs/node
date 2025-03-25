# Dummy Rollup Deployment Guide

## Prerequisites
- Ensure you have Docker and Docker Compose installed on your machine.
- Clone the necessary repository:
  ```sh
  git clone https://github.com/americanolabs/node.git
  ```

## Setting Up the Environment

### 1. Navigate to the Project Root Directory
   ```sh
   cd node/
   ```

### 2. Modify Docker Compose Paths
   Depending on your system setup, adjust paths:
   - For `root` user: `/root`
     ```yaml
     volumes:
       - ./wasm:/root/wasm/
       - ./database:/root/.arbitrum
     ```
   - For standard user: `/home/user`
     ```yaml
     volumes:
       - ./wasm:/home/<user>/wasm/
       - ./database:/home/<user>/.arbitrum
     ```
     Note: Change `<user>` with the actual username on your computer.
### 3. Start the Main Project Containers
   Run the following command in the project root directory:
   ```sh
   docker compose up -d
   ```

### 4. Navigate to `caff-node` Folder
   ```sh
   cd caff-node
   ```

### 5. Start the `caff-node` Containers
   ```sh
   docker compose up -d
   ```

### 6. Verify Running Containers
   Check if Docker is running and ensure there are three active containers:
   ```sh
   docker ps
   ```
   You should see three running containers related to the project.

## Handling Expected Errors
If you encounter this error:
```sh
error acting as staker                    
err="error advancing stake from node 2 (hash 0xee288c5dcc61206e6868fa7a01da6abaabe22d6c849718a47eb361857b7e8dd8): error generating node action: block validation is still pending"
```
This is expected when running a newly deployed rollup with no recent activity. The error occurs because there are no new nodes to stake on or no new batches posted. Simply allow the system to continue running.

