### **Lab 1 – Docker Fundamentals**

**Goal:**

- Understand Docker, containerd, and how containers run
- Explore Docker's core components and architecture
- Inspect Docker daemon and runtime environment

**Deliverables:**

- Run `docker info` and `docker version` to inspect Docker installation
- Explore Docker socket and daemon configuration
- Document understanding of Docker architecture components

---

### **Lab 2 – Build and Run Your First Image**

**Goal:**

- Create a simple Python or FastAPI application
- Build custom Docker image with Dockerfile
- Understand ENTRYPOINT vs CMD

**Deliverables:**

- Simple Python/FastAPI app with `Dockerfile`
- Build image with `docker build`
- Run container with `docker run`
- Working example using both `ENTRYPOINT` and `CMD`

---

### **Lab 3 – Container Networking Modes**

**Goal:**

- Understand Docker networking modes (bridge, host, none)
- Inspect and configure container networks
- Test connectivity between containers

**Deliverables:**

- Inspect default bridge network with `docker network inspect`
- Run containers in host mode with `docker run --network host`
- Run containers in bridge mode and test inter-container communication
- Document network behavior differences

---

### **Lab 4 – Run Containers with CPU and Memory Limits**

**Goal:**

- Apply resource constraints to containers
- Monitor container resource usage
- Understand resource management best practices

**Deliverables:**

- Run containers with `--cpus`, `--memory`, and `--memory-swap` flags
- Measure resource effects with `docker stats`
- Test behavior under resource constraints
- Document resource limit configurations

---

### **Lab 5 – Docker Remote API and Secure Access**

**Goal:**

- Enable Docker remote API on worker nodes
- Authenticate and secure remote Docker access
- Interact with Docker API programmatically

**Deliverables:**

- Configure Docker daemon for remote API access
- Test Docker API using `curl` and Python `requests`
- Implement secure authentication for Docker API
- Document API endpoints and usage

---

### **Lab 6 – Build a Container Launcher Agent**

**Goal:**

- Build FastAPI app that launches containers dynamically
- Use Docker SDK or CLI to manage containers
- Create API-driven container orchestration

**Deliverables:**

- FastAPI app exposing container management endpoints
- `POST /containers` endpoint to launch containers dynamically
- Use Docker SDK for Python or subprocess calls to Docker CLI
- Return container ID and status from API

---

### **Lab 7 – Mount Volumes and Pass Env Vars**

**Goal:**

- Understand Docker volumes and bind mounts
- Pass environment variables and configuration to containers
- Manage secrets and configs securely

**Deliverables:**

- Use `-v` and `--mount` for volume mounting
- Pass environment variables with `-e` and `--env-file`
- Mount secrets/configs for deployed applications
- Demonstrate persistent data storage across container restarts

---

### **Lab 8 – Collect Container Metrics with cAdvisor**

**Goal:**

- Run cAdvisor to collect container metrics
- Explore container resource usage and performance data
- Export metrics for monitoring systems

**Deliverables:**

- Deploy cAdvisor as a sidecar container
- Access metrics via `/metrics` endpoint
- Explore CPU, memory, network, and disk metrics
- Document available metrics and their meanings

---

### **Lab 9 – View Resource Usage with Docker Stats**

**Goal:**

- Monitor real-time container resource usage
- Export container metrics for visualization
- Understand container runtime behavior

**Deliverables:**

- Use `docker stats` to monitor running containers
- Use `docker inspect` to explore container configuration and runtime details
- Export stats data for Prometheus or other visualization tools
- Create script to collect and format metrics

---

### **Lab 10 – Log Forwarding with Fluent Bit**

**Goal:**

- Install and configure Fluent Bit for log aggregation
- Route container logs to centralized storage
- Scale from `docker logs` to production log streaming

**Deliverables:**

- Install Fluent Bit as log forwarder
- Route container logs to Elasticsearch or file output
- Configure log parsing and filtering
- Compare `docker logs` with centralized logging approach

---

### **Lab 11 – Docker Compose for Multi-Service Apps**

**Goal:**

- Define multi-container applications with Docker Compose
- Orchestrate services with networking and dependencies
- Manage complex application stacks declaratively

**Deliverables:**

- `docker-compose.yml` defining API, Prometheus, and Node Exporter services
- Use `depends_on` to manage service startup order
- Configure custom networks and volumes
- Bring up entire stack with `docker compose up`

---

### **Lab 12 – Docker Image Optimization**

**Goal:**

- Optimize Docker images for size and build speed
- Use multi-stage builds effectively
- Apply best practices for production images

**Deliverables:**

- Implement multi-stage Dockerfile for FastAPI app
- Reduce image size using Alpine base images
- Create `.dockerignore` to exclude unnecessary files
- Compare image sizes before and after optimization

---

### **Lab 13 – Push and Pull from DockerHub / ECR**

**Goal:**

- Authenticate with container registries (DockerHub, ECR)
- Push custom images to remote registries
- Automate image build and push with CI/CD

**Deliverables:**

- Authenticate to DockerHub and/or AWS ECR
- Tag and push container scheduler image
- Pull image from registry on different machine
- Automate image build and push using GitHub Actions

---

### **Lab 14 – Secure Docker Environments**

**Goal:**

- Implement Docker security best practices
- Run containers with minimal privileges
- Harden container runtime environment

**Deliverables:**

- Run containers as non-root user
- Avoid host mounts and privileged mode where possible
- Use read-only filesystems with `--read-only` flag
- Apply seccomp profiles for syscall filtering
- Document security configurations and trade-offs