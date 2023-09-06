# Microservices-Deployment-on-Kubernetes-Deploying-a-Microservice-Application
# README for Kubernetes Deployment Configuration

This README provides an overview of the Kubernetes Deployment configuration for a microservices-based application. The configuration consists of multiple Deployment and Service objects, each responsible for running and exposing a specific microservice. The following microservices are included:

1. **Email Service**
   - Deployment: `emailservice`
   - Service: `emailservice`
   - Port: 8080 (containerPort)
   - Additional Configuration:
     - Environment variables: `PORT`, `DISABLE_TRACING`, `DISABLE_PROFILER`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

2. **Recommendation Service**
   - Deployment: `recommendationservice`
   - Service: `recommendationservice`
   - Port: 8080 (containerPort)
   - Additional Configuration:
     - Environment variables: `PORT`, `PRODUCT_CATALOG_SERVICE_ADDR`, `DISABLE_TRACING`, `DISABLE_PROFILER`, `DISABLE_DEBUGGER`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

3. **Product Catalog Service**
   - Deployment: `productcatalogservice`
   - Service: `productcatalogservice`
   - Port: 3550 (containerPort)
   - Additional Configuration:
     - Environment variable: `PORT`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

4. **Payment Service**
   - Deployment: `paymentservice`
   - Service: `paymentservice`
   - Port: 50051 (containerPort)
   - Additional Configuration:
     - Environment variable: `PORT`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

5. **Currency Service**
   - Deployment: `currencyservice`
   - Service: `currencyservice`
   - Port: 7000 (containerPort)
   - Additional Configuration:
     - Environment variable: `PORT`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

6. **Shipping Service**
   - Deployment: `shippingservice`
   - Service: `shippingservice`
   - Port: 50051 (containerPort)
   - Additional Configuration:
     - Environment variable: `PORT`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

7. **Ad Service**
   - Deployment: `adservice`
   - Service: `adservice`
   - Port: 9555 (containerPort)
   - Additional Configuration:
     - Environment variable: `PORT`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

8. **Cart Service**
   - Deployment: `cartservice`
   - Service: `cartservice`
   - Port: 7070 (containerPort)
   - Additional Configuration:
     - Environment variable: `REDIS_ADDR`
     - Readiness and liveness probes using `/bin/grpc_health_probe`

9. **Redis Cart**
   - Deployment: `redis-cart`
   - Service: `redis-cart`
   - Image: `redis:alpine`
   - Port: 6379 (containerPort)
   - Additional Configuration:
     - Readiness and liveness probes using TCP socket
     - Data storage volume mounted

10. **Checkout Service**
    - Deployment: `checkoutservice`
    - Service: `checkoutservice`
    - Port: 5050 (containerPort)
    - Additional Configuration:
      - Environment variables: `PORT`, `PRODUCT_CATALOG_SERVICE_ADDR`, `SHIPPING_SERVICE_ADDR`, `PAYMENT_SERVICE_ADDR`, `EMAIL_SERVICE_ADDR`, `CURRENCY_SERVICE_ADDR`, `CART_SERVICE_ADDR`
      - Readiness and liveness probes using `/bin/grpc_health_probe`

11. **Frontend Service**
    - Deployment: `frontend`
    - Service: `frontend`
    - Port: 8080 (containerPort)
    - Additional Configuration:
      - Environment variables: `PORT`, `PRODUCT_CATALOG_SERVICE_ADDR`, `CURRENCY_SERVICE_ADDR`, `CART_SERVICE_ADDR`, `RECOMMENDATION_SERVICE_ADDR`, `SHIPPING_SERVICE_ADDR`, `CHECKOUT_SERVICE_ADDR`, `AD_SERVICE_ADDR`
      - Readiness and liveness probes using HTTP GET requests

Each microservice is deployed as a Kubernetes Deployment with specified resource requests and limits for CPU and memory. Additionally, Kubernetes Services are created to expose the microservices within the cluster.

The `frontend` service is exposed as a NodePort with port 80 and nodePort 30007, allowing external access to the application.

Please make sure you have a Kubernetes cluster set up and configured before applying these YAML configurations. You can apply these configurations using the `kubectl apply -f <filename>.yaml` command for each file.

For more detailed information on each microservice's configuration or for troubleshooting, refer to the respective microservice's documentation.
