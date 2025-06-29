# 🚀 Spring PetClinic – Full DevOps CI/CD Pipeline

This project demonstrates a complete DevOps CI/CD pipeline for the [Spring PetClinic](https://github.com/spring-projects/spring-petclinic) application using industry-standard tools including Jenkins, Git, Maven, Docker, Ansible, Graphite, and Grafana.

---

## 📦 Technologies Used

| Tool         | Purpose                            |
|--------------|-------------------------------------|
| **Git**      | Version Control                     |
| **Jenkins**  | CI/CD Automation                    |
| **Maven**    | Build and Dependency Management     |
| **Docker**   | Containerization of Application     |
| **Ansible**  | Automated Deployment                |
| **Graphite** | Metrics Storage and Visualization   |
| **Grafana**  | Monitoring Dashboard Visualization  |

---

## 🛠️ Pipeline Workflow

1. **Source Code Management**
   - Java-based Spring Boot application hosted in Git.

2. **Build Phase**
   - Jenkins pulls code from Git and builds using Maven.
   - Unit tests (JUnit) are skipped or run based on requirement.

3. **Packaging**
   - Maven creates `.jar` file.
   - Docker image is built using `Dockerfile`.

4. **Deployment**
   - Ansible playbook (`deploy.yml`) stops old container, removes image, builds new one, and runs it on port `9192`.

5. **Monitoring**
   - Spring Boot app sends metrics to **Graphite**.
   - **Grafana** visualizes these metrics via Graphite data source.

---

## 🔗 URLs and Endpoints

| Service       | URL                                  |
|---------------|---------------------------------------|
| **PetClinic App** | `http://<your-server-ip>:9192/`    |
| **Jenkins**       | `http://<your-server-ip>:8080/`    |
| **Grafana**       | `http://<your-server-ip>:3000/`    |
| **Graphite UI**   | `http://<your-server-ip>:8081/` *(if exposed separately)*

_Replace `<your-server-ip>` with `10.0.2.15` if you're using VirtualBox NAT networking._

---

## 📊 Sample Grafana Panel Metrics

- `custom.metric.test`
- `jvm.memory.used`
- `process.cpu.usage`
- `system.cpu.usage`
- `http.server.requests.count`

---

## 📁 File Structure Highlights

```bash
todo-app/
├── Dockerfile
├── deploy.yml
├── ansible-hosts
├── src/
│   └── main/
│       └── resources/
│           └── application.properties  # Includes graphite config
```

---

## 🧪 Testing Graphite Metric

Manually push a test metric:
```bash
echo "custom.metric.test 42 $(date +%s)" | nc 127.0.0.1 2003
```

Then refresh Grafana to view the update.

---

## 📝 Author

**Vedant**  
DevOps Enthusiast | Automating Everything | Always Shipping 🚀
