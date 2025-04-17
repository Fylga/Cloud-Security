# Cloud-Security
EPITECH Cyber-Security MODULE 5 - Secure the development and production environment for an app.


## ✅ ASSIGNMENT OVERVIEW

**Designing a secure Azure-based architecture** for **Cool Delivery**, a popular delivery app moving to the cloud that contains:

1. A **professional architectural document**.
2. A **working Azure-based infrastructure prototype**.
3. A **clear and convincing presentation**.
4. Demonstrated ability to **communicate like a professional cloud consultant**.

---

## ✅ DELIVERABLES & EVALUATION BREAKDOWN

### **Deliverable 1: Architectural Document (30%)**

Content:

- Map out a **secure, cost-efficient Azure infrastructure**.
- Include identity, access management, networks, services, cost estimation.
- Address the **three environments** (Dev, QA, Prod).
- Clearly describe **IAM policies**, **network segmentation**, **monitoring**, **auto-deployment**, etc.
- Include architecture diagram using **draw.io**.

### **Deliverable 2: Working Infrastructure (30%)**

- Deploy **at least one environment** in Azure (Dev, QA, or Prod).
- Ensure all components work together (e.g. Frontend connects to backend which connects to DB).
- **Bonus:** Setup CI/CD (e.g. GitHub → Azure Web App) for auto-deployment.

### **Deliverable 3: Presentation (20%)**

- Visually clean and professional (use diagrams and screenshots).
- Easy to follow even for non-technical stakeholders.
- Focused on **benefits to the client**: security, scalability, cost-efficiency.

### **Deliverable 4: Client Communication (20%)**

- Use client-centric language.
- Explain trade-offs, pricing, and security in clear business terms.
- Anticipate client questions (e.g., *“Why Azure?”, “How secure is this?”*).

---

## ✅ TECHNICAL PLAN

### 🔧 **Cloud Implementation Model**

- **Implementation Type**: Full **Cloud** (to reduce on-prem costs and increase scalability).
- **Business Model**: **Public Cloud (Azure)** for cost-effectiveness (Private is too costly for a startup).
- **Environment Types**: Separate **resource groups or subscriptions** for Dev / QA / Prod.

---

## 🔐 SECURITY ARCHITECTURE

### 🔐 1. **Identity & Access Management**
- Use **Azure Active Directory (AAD)**.
- Apply **RBAC (Role-Based Access Control)** per environment.
- Enforce **MFA**.
- Use **managed identities** for Azure services.

### 🌐 2. **Networking & Segmentation**
- Use **Azure Virtual Networks (VNets)** with **Network Security Groups (NSGs)**:
  - **Frontend** exposed via **Application Gateway** or **Azure Front Door**.
  - Backend and DB in **private subnets**.
- **Allow minimal ports** (e.g. 443, 22 with IP filtering).
- Use **VNet Peering** for isolated environments.

### 🖥️ 3. **Servers**
- Host backend on **Azure App Service** (secured via VNet integration).
- DB hosted on **Azure Cosmos DB (Mongo API)**.
- Use **Azure Defender for Cloud** to secure resources.
- Install **antivirus/anti-malware** agents where applicable.

### 📈 4. **Monitoring & Logging**
- Use **Azure Monitor + Log Analytics + Azure Sentinel (SIEM)** for threat detection.
- Enable **Activity Logs**, **NSG Flow Logs**, **App Insights**.

---

## 💸 COST OPTIMIZATION (AZURE $100 CREDIT)

| Resource            | Type                      | Notes                                           |
|---------------------|---------------------------|-------------------------------------------------|
| App Service Plan    | B1 (Basic)                | Host Python Flask backend                       |
| Azure Static Web App| Free Tier (if Frontend SPA)| Host HTML/JS/CSS frontend                       |
| Cosmos DB           | Free Tier (Mongo API)     | DB layer with security                          |
| Azure Monitor       | Basic logs for free       | Only enable advanced on Production              |
| Azure DevOps / GitHub | Free pipelines           | CI/CD from GitHub                               |

👉 **Note**: Provide cost tables in the architectural doc showing dev/test/prod monthly cost estimations.

---

## 🧱 ENVIRONMENTS PLAN

- **Dev**: Lightweight setup, open to team.
- **QA**: Mirror of Prod, restricted access.
- **Prod**: Hardened, monitored, publicly available frontend only.

Each environment has:

- 1x Frontend
- 1x Backend
- 1x MongoDB (Azure Cosmos DB)
- Specific Resource Group & Network Isolation

---

## 🧪 PROTOTYPE SETUP (Deliverable 2)

**Azure Setup**:
- Deploy DEV environment using ARM templates, Bicep, or Terraform (optional).
- Push code to GitHub.
- Configure GitHub Actions to auto-deploy to Azure App Service.
- Test connectivity between frontend → backend → DB.

---

## 🎯 PRESENTATION STRUCTURE

Slide deck layout suggestion:

1. **Introduction**
   - Business goal
   - Cloud migration rationale

2. **Architecture Overview**
   - Draw.io diagram
   - Explanation of each component

3. **Security Measures**
   - IAM, Networking, Monitoring layers

4. **Cost & Scalability**
   - Table of resources
   - Explanation of growth strategy

5. **Prototype Demo**
   - Screenshots or live URL
   - GitHub → Azure auto-deploy process

6. **Next Steps**
   - Suggestions for future enhancements
   - Optional services (e.g., Key Vault, API Management)

---

## ✅ FINAL CHECKLIST

| Item                           | Done? |
|--------------------------------|-------|
| Architectural Doc (draw.io, security layers, IAM, pricing) | ⬜️ |
| Working Azure Prototype (one env) | ⬜️ |
| CI/CD deployment (bonus)        | ⬜️ |
| Client Presentation Slides      | ⬜️ |
| Clear client-facing language    | ⬜️ |


---

## 🧱 MULTI-ENVIRONMENT ARCHITECTURE OVERVIEW

### 🔄 Shared Strategy

| Component            | Approach |
|----------------------|----------|
| Environments         | 3 Resource Groups (or Subscriptions): `Azure-Dev`, `Azure-QA`, `Azure-Prod` |
| Isolation            | Separate VNets, subnets, NSGs for each |
| Naming Convention    | E.g., `azure-prod-api`, `azure-qa-db`, `azure-dev-front` |
| CI/CD                | GitHub Actions or Azure DevOps per branch (`main` → Prod, `qa` → QA, `dev` → Dev) |
| IaC                  | Optional: Bicep / ARM / Terraform to define infrastructure as code |

---

## 🛡️ SECURITY ARCHITECTURE (With Tool Suggestions)

Let's go **layer by layer** and suggest where your tools come in:

---

### 🔐 1. **IDENTITY & ACCESS MANAGEMENT (IAM)**

| Element           | Tool / Service                  | Why |
|-------------------|----------------------------------|-----|
| Central IAM       | **Azure AD + RBAC**              | Enforce least-privilege access |
| MFA               | **Azure AD MFA**                 | Standard for secure logins |
| Secrets Handling  | **Azure Key Vault**              | Store API keys, DB passwords, certs securely |
| Admin Access      | **Azure Bastion**                | Secure jump-box to access VMs without exposing RDP/SSH |

✅ **Required for all 3 environments.**

---

### 🌐 2. **NETWORKING & FIREWALLING**

| Layer                | Tool / Service                        | Why |
|----------------------|----------------------------------------|-----|
| Perimeter Protection | **Cloudflare WAF** or **Azure WAF**   | Block DDoS, bots, and OWASP Top 10 threats |
| Intra-network Rules  | **NSGs + ASGs**                        | Enforce segmentation between tiers (FE/BE/DB) |
| Firewall             | **Barracuda CloudGen Firewall** *(Optional)* | Extra control + analytics at the network edge |
| VPN Replacement      | **Zscaler** *(Optional)*               | For secure private access during remote DevOps |

⚠️ **Use Azure-native WAF unless Barracuda/Zscaler is part of enterprise stack or customer has budget.**

---

### 💾 3. **WORKLOAD SECURITY**

| Component        | Tool / Service                                | Why |
|------------------|------------------------------------------------|-----|
| Endpoint/VM Sec  | **CrowdStrike** or **Trend Micro Cloud One**  | Protect against shell injection, malware, zero-day |
| Code Protection  | **TOPIA** *(Optional)*                        | Vulnerability ranking and remediation guidance |
| Logging & SIEM   | **Azure Sentinel** or **Splunk Enterprise Sec** | Real-time threat analytics, centralized logs |
| Container Image Sec | Azure Defender + TOPIA                     | Scan app images before deployment |
| Backup           | **Rubrik** *(Optional)*                       | Highly secure searchable backups for rollback |

✅ Azure Defender + Trend Micro is solid out-of-the-box. Choose Splunk only if deep log analytics is a must.

---

### 🔍 4. **MONITORING, VISIBILITY & COMPLIANCE**

| Tool/Service           | Why |
|------------------------|-----|
| **Azure Monitor + Log Analytics** | Performance + event monitoring |
| **Azure Sentinel (SIEM)**         | Security analytics & threat intelligence |
| **Orca Security** *(Optional)*    | Cloud security posture mgmt across environments |
| **Databricks** *(Optional)*       | Not directly needed unless you're doing data science or ML workloads |

✅ Azure-native tools cover most of your needs, but Orca or Splunk can add value for enterprise-level visibility.

---

## 📦 AZURE SERVICES USED PER ENVIRONMENT

| Layer           | Service                          | Purpose |
|------------------|----------------------------------|---------|
| Frontend         | Azure Static Web App             | HTML/JS/CSS hosting |
| Backend          | Azure App Service (Linux)        | Flask API |
| Database         | Azure Cosmos DB (Mongo API)      | Scalable MongoDB |
| Networking       | Azure VNet + NSG + App Gateway   | Network security and traffic control |
| Secret Mgmt      | Azure Key Vault                  | Store secrets |
| IAM              | Azure AD + RBAC                  | User & app access control |
| DevOps           | GitHub Actions / Azure Pipelines | CI/CD |
| Monitoring       | Azure Monitor + App Insights     | Logs, metrics, traces |

---

## 💡 BONUS STRATEGY (PROD-HARDENING ONLY)

In **Production only**, we can recommend:

- **CrowdStrike**: Lightweight endpoint security (for App Service + any deployed VMs).
- **Cloudflare WAF**: DDoS + reverse-proxy security layer.
- **Azure Front Door** (optional): CDN + WAF + global traffic management.
- **Sentinel + Rubrik**: Advanced monitoring + reliable backups.
- **Zscaler**: Only if a secure tunnel/VPN alternative is necessary.

---
