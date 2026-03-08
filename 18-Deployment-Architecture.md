# 🚀 بنية النشر

## 🎯 مقدمة

يقدم هذا المستند استراتيجية النشر والبنية التحتية للنظام مع Docker و Kubernetes.

---

## 🏛️ بنية النشر

```mermaid
flowchart TB
    subgraph DNS["DNS"]
        CF[Cloudflare]
    end
    
    subgraph CDN["CDN"]
        CloudFront[AWS CloudFront]
    end
    
    subgraph LoadBalancer["Load Balancer"]
        Nginx[Nginx]
    end
    
    subgraph K8s["Kubernetes Cluster"]
        subgraph API["API Pods"]
            API1[API Pod 1]
            API2[API Pod 2]
            API3[API Pod 3]
        end
        
        subgraph Web["Web Pods"]
            Web1[Web Pod 1]
            Web2[Web Pod 2]
        end
        
        subgraph Workers["Background Workers"]
            W1[Worker 1]
            W2[Worker 2]
        end
    end
    
    subgraph Data["Data Layer"]
        Postgres[(PostgreSQL)]
        Redis[(Redis)]
        MinIO[MinIO]
        RabbitMQ[RabbitMQ]
    end
    
    CF --> CloudFront --> Nginx
    Nginx --> API
    Nginx --> Web
    API --> Data
    Workers --> Data
```

---

## 📦 Docker Compose

### ملف docker-compose.yml

```yaml
version: '3.8'

services:
  # API Service
  api:
    build:
      context: ./src/ERP.API
      dockerfile: Dockerfile
    container_name: erp-api
    ports:
      - "5000:80"
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ConnectionStrings__Default=Host=postgres;Database=erp;Username=erp;Password=erp123
      - Redis__Connection=redis:6379
      - Jwt__Secret=${JWT_SECRET}
    depends_on:
      - postgres
      - redis
      - rabbitmq
    networks:
      - erp-network
    restart: unless-stopped

  # Web Frontend
  web:
    build:
      context: ./src/ERP.Web
      dockerfile: Dockerfile
    container_name: erp-web
    ports:
      - "3000:80"
    environment:
      - REACT_APP_API_URL=http://api:5000
    depends_on:
      - api
    networks:
      - erp-network
    restart: unless-stopped

  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    container_name: erp-postgres
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_DB=erp
      - POSTGRES_USER=erp
      - POSTGRES_PASSWORD=erp123
    volumes:
      - postgres-data:/var/lib/postgresql/data
      - ./init-scripts:/docker-entrypoint-initdb.d
    networks:
      - erp-network
    restart: unless-stopped

  # Redis Cache
  redis:
    image: redis:7-alpine
    container_name: erp-redis
    ports:
      - "6379:6379"
    volumes:
      - redis-data:/data
    networks:
      - erp-network
    restart: unless-stopped

  # RabbitMQ Message Queue
  rabbitmq:
    image: rabbitmq:3-management-alpine
    container_name: erp-rabbitmq
    ports:
      - "5672:5672"
      - "15672:15672"
    environment:
      - RABBITMQ_DEFAULT_USER=erp
      - RABBITMQ_DEFAULT_PASS=erp123
    volumes:
      - rabbitmq-data:/var/lib/rabbitmq
    networks:
      - erp-network
    restart: unless-stopped

  # MinIO Object Storage
  minio:
    image: minio/minio:latest
    container_name: erp-minio
    ports:
      - "9000:9000"
      - "9001:9001"
    environment:
      - MINIO_ROOT_USER=erp
      - MINIO_ROOT_PASSWORD=erp123456
    command: server /data --console-address ":9001"
    volumes:
      - minio-data:/data
    networks:
      - erp-network
    restart: unless-stopped

  # Nginx Reverse Proxy
  nginx:
    image: nginx:alpine
    container_name: erp-nginx
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
      - ./nginx/ssl:/etc/nginx/ssl
    depends_on:
      - api
      - web
    networks:
      - erp-network
    restart: unless-stopped

volumes:
  postgres-data:
  redis-data:
  rabbitmq-data:
  minio-data:

networks:
  erp-network:
    driver: bridge
```

---

## ☸️ Kubernetes Deployment

### API Deployment

```yaml
# k8s/api-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: erp-api
  labels:
    app: erp-api
spec:
  replicas: 3
  selector:
    matchLabels:
      app: erp-api
  template:
    metadata:
      labels:
        app: erp-api
    spec:
      containers:
      - name: api
        image: erp/api:latest
        ports:
        - containerPort: 80
        env:
        - name: ASPNETCORE_ENVIRONMENT
          value: "Production"
        - name: ConnectionStrings__Default
          valueFrom:
            secretKeyRef:
              name: erp-secrets
              key: db-connection
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 80
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /health
            port: 80
          initialDelaySeconds: 5
          periodSeconds: 5
---
apiVersion: v1
kind: Service
metadata:
  name: erp-api-service
spec:
  selector:
    app: erp-api
  ports:
  - port: 80
    targetPort: 80
  type: ClusterIP
```

### Horizontal Pod Autoscaler

```yaml
# k8s/hpa.yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: erp-api-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: erp-api
  minReplicas: 3
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
```

---

## 📊 متطلبات الموارد

### الموارد المطلوبة

| الخدمة | CPU | الذاكرة | التخزين |
|--------|-----|---------|---------|
| **API** | 0.5 core | 512 MB | - |
| **Web** | 0.25 core | 256 MB | - |
| **PostgreSQL** | 1 core | 2 GB | 50 GB |
| **Redis** | 0.25 core | 512 MB | 10 GB |
| **RabbitMQ** | 0.5 core | 1 GB | 10 GB |
| **MinIO** | 0.5 core | 1 GB | 100 GB |

### الإجمالي

| البيئة | CPU | الذاكرة | التخزين |
|--------|-----|---------|---------|
| **تطوير** | 2 cores | 4 GB | 50 GB |
| **إنتاج** | 4 cores | 8 GB | 200 GB |

---

## 🔐 إدارة الأسرار

### Kubernetes Secrets

```yaml
# k8s/secrets.yaml
apiVersion: v1
kind: Secret
metadata:
  name: erp-secrets
type: Opaque
stringData:
  db-connection: "Host=postgres;Database=erp;Username=erp;Password=erp123"
  jwt-secret: "your-256-bit-secret-key-here"
  redis-connection: "redis:6379"
  rabbitmq-connection: "amqp://erp:erp123@rabbitmq:5672"
```

---

## 📈 المراقبة

### Prometheus + Grafana

```yaml
# k8s/monitoring.yaml
apiVersion: v1
kind: Service
metadata:
  name: prometheus
  labels:
    app: prometheus
spec:
  ports:
  - port: 9090
    targetPort: 9090
  selector:
    app: prometheus
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: grafana
spec:
  replicas: 1
  selector:
    matchLabels:
      app: grafana
  template:
    metadata:
      labels:
        app: grafana
    spec:
      containers:
      - name: grafana
        image: grafana/grafana:latest
        ports:
        - containerPort: 3000
```

---

**الوثيقة:** بنية النشر  
**الإصدار:** 1.0  
**تاريخ التحديث:** 2026-03-07
