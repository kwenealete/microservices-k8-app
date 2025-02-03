
This config.yaml file is used to configure various microservices in a distributed application. It includes essential settings such as service discovery, database connections, API configurations, and security settings. Proper configuration ensures that the application runs smoothly in development, staging, and production environments.

## What is a Microservice?

A microservice is an independently deployable service that performs a specific business function. Unlike monolithic applications, microservices are loosely coupled, allowing for greater flexibility, scalability, and maintainability. They communicate with each other via APIs and can be deployed, scaled, and updated independently.

## Some security and production best practices adopted 


### 1. Liveness Probe

• Checks if the application is still running.
• If the probe fails, Kubernetes restarts the container.
• Helps recover from deadlocks or unresponsive applications.

### 2. Readiness Probe

• Determines if the service is ready to receive traffic.
• If the probe fails, Kubernetes removes the pod from the load balancer.
• Ensures that traffic is only routed to fully initialized services.


## Some Security Best Practices: 

1. Use Environment Variables for Secrets
• Never hardcode secrets in config.yaml. Use environment variables or a secrets manager like HashiCorp Vault or AWS Secrets Manager.

2. Enable Authentication & Authorization
• Use JWT, OAuth, or OpenID Connect for secure authentication.
• Implement role-based access control (RBAC).

3. Restrict Network Access
• Use ClusterIP for internal services and Ingress controllers for external access.
• Avoid exposing services directly via NodePort.

4. Enable TLS Encryption
• Use TLS (HTTPS) for all communications.
• Configure an Ingress controller with a valid TLS certificate.

5. Restrict External Exposure
• Use firewalls and security groups to restrict access.
• Implement API rate limiting and monitoring.

## Why Not Use NodePort?
• Security Risks: Exposing a service via NodePort makes it accessible from any external IP, increasing attack surface.
• Scalability Issues: Ports are limited (30000–32767), making it unsuitable for large-scale applications.
• Lack of Load Balancing: NodePort does not provide automatic load balancing across nodes.
• Alternative: Use Ingress Controllers with LoadBalancer type services rather.

### Production Best Practices

1. Use ConfigMaps & Secrets
• Store non-sensitive configurations in Kubernetes ConfigMaps.
• Store secrets in Kubernetes Secrets or a dedicated secrets manager.

2. Use Resource Limits
• Define CPU & memory limits for microservices to prevent resource exhaustion.
