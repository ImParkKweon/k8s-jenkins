# Kubernetes Jenkins Deployment

## 📌 Overview
이 저장소는 **Kubernetes 환경에서 Jenkins CI/CD 서버를 배포 및 운영하는 매니페스트**를 정리한 리포지토리입니다.  
Jenkins를 Kubernetes 클러스터 위에 배포하고 구성하는 데 필요한 **Namespace, Deployment, Service, Volume 등 리소스를 YAML로 정의**하여 실제 클러스터에서도 바로 적용 가능하도록 구성되어 있습니다.

👉 **DevOps 환경에서 Jenkins를 Kubernetes에 배포·운영할 수 있는 능력**을 증명하는 것을 목표로 합니다.

---

## 🧩 Architecture
```
[ Kubernetes Cluster ]
       ├── [ Namespace: jenkins ]
       ├── [ ServiceAccount ]
       ├── [ Deployment: jenkins ]
       ├── [ Service: jenkins ]
       └── [ Persistent Volume / PVC ]
```

---

## 📂 Repository Structure
```
.
├── namespace.yaml         # Jenkins 용 Namespace 정의
├── serviceAccount.yaml    # Jenkins ServiceAccount
├── volume.yaml            # PVC / Volume 정의
├── deployment.yaml        # Jenkins Deployment manifest
├── service.yaml           # Jenkins Service (ClusterIP / NodePort)
├── nfs/                   # NFS 기반 공유 스토리지 설정 (선택)
├── README.md              # 설명 파일
```

---

## ⚙️ Prerequisites
- Kubernetes Cluster (온프레미스 / 클라우드 무관)
- kubectl configured
- Jenkins 및 Kubernetes 기본 개념 이해

---

## 🚀 How to Use

### 1️⃣ Namespace 생성
```bash
kubectl apply -f namespace.yaml
```

### 2️⃣ ServiceAccount 생성
```bash
kubectl apply -f serviceAccount.yaml
```

### 3️⃣ Persistent Volume / PVC 생성
```bash
kubectl apply -f volume.yaml
```

### 4️⃣ Jenkins Deployment
```bash
kubectl apply -f deployment.yaml
```

### 5️⃣ Jenkins Service 생성
```bash
kubectl apply -f service.yaml
```

### 6️⃣ Jenkins 접속
```bash
kubectl port-forward svc/jenkins 8080:8080 -n jenkins
```

---

## ✅ What This Project Demonstrates
- Jenkins CI/CD 서버의 Kubernetes 배포 경험
- YAML 기반 인프라 리소스 정의 능력
- DevOps 파이프라인 구성 이해
- 컨테이너 기반 CI/CD 환경 운영 역량

---
