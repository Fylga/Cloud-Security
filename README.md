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

Would you like me to:
- Draft the **architecture diagram**?
- Help build the **architectural document**?
- Create the **PowerPoint presentation outline**?
- Walk through **Azure setup** for the prototype?

Let me know where you want to start, and we’ll build this step-by-step.