# Dropbox-like Distributed File Storage System
Dropbox-like Distributed File Storage System Using MinIO and gRPC

## Project Overview
- Users can upload and download files.

- Files are replicated across multiple storage nodes to ensure high availability.

- Metadata (like file names, upload times, and versions) is managed centrally.

- The system handles eventual consistency by syncing file updates across nodes.

# System Architecture
- gRPC Server: Manages file uploads, downloads, and metadata.

- MinIO Distributed Storage Nodes: Handles object storage and replication.

- Client Interface: Allows users to interact with the system via HTTP.

## Step 1: install dependencies
npm install

## step 2: Setting Up MinIO Distributed Storage Nodes
```sh
docker run -p 9001:9000 --name minio1 -e "MINIO_ACCESS_KEY=minioadmin" -e "MINIO_SECRET_KEY=minioadmin" -d minio/minio server /data
docker run -p 9002:9000 --name minio2 -e "MINIO_ACCESS_KEY=minioadmin" -e "MINIO_SECRET_KEY=minioadmin" -d minio/minio server /data
docker run -p 9003:9000 --name minio3 -e "MINIO_ACCESS_KEY=minioadmin" -e "MINIO_SECRET_KEY=minioadmin" -d minio/minio server /data
```
## steip 3: run the system

- 1 run the client
```sh
node ./client/client.js
```

- 2 run the server
```sh
node ./server/index.js
```

<hr>

### Please help improve and expand the project.