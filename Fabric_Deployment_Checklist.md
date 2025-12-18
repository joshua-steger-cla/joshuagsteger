
# Microsoft Fabric (Power BI) – Tenant & Project Setup Checklist

> **Purpose:** Use this checklist to stand up a new analytics environment across **Microsoft Entra**, **Microsoft 365**, **Azure**, **Power BI/Fabric**, and supporting tools. Tick items as you complete them. Replace the `![placeholder]()` images with your screenshots or architecture diagrams.

---

## 🔐 1. Entra Portal (Azure Active Directory)
- [ ] **Create new users or guest accounts**  
  ![Create users – Entra](images/entra-create-users.png)
- [ ] **Assign role: Fabric Administrator** (Azure RBAC)  
  ![Assign role – Fabric Admin](images/entra-fabric-admin-role.png)
- [ ] **Create security group** for *Analytics Administrators*  
  ![Security group – Analytics Admins](images/entra-security-group.png)
- [ ] **(Optional) Register App / Service Principal** in *App registrations*  
  ![App registration](images/entra-app-registration.png)
  - [ ] Save **secret value**, **app/client ID**, and **tenant ID** in **LastPass** & **Azure Key Vault**
  - [ ] Add proper **API permissions** (Graph, Power BI service)  
    ![API permissions](images/entra-api-permissions.png)

---

## 🧰 2. Microsoft 365 Admin Center
- [ ] **Assign productivity licensing** (Outlook, Teams, Power BI) for client comms  
  ![Licensing overview](images/m365-licensing.png)
  - [ ] Business **Basic / Standard / Premium**
  - [ ] **E5 / E3**
  - [ ] **G3 / G5** (Government)
  - [ ] **F1 / F3** (Frontline)
  - [ ] **A1 / A3 / A5** (Education)
- [ ] **Assign Power BI Pro** licenses where needed  
  - [ ] Use **Power BI Pro 60-day trials** if applicable  
    ![Power BI licensing](images/powerbi-pro-license.png)

---

## ☁️ 3. Azure Portal
- [ ] **Create Azure Subscription**  
  ![Create subscription](images/azure-subscription.png)
  - [ ] MSP **set up & enable** (if applicable)
  - [ ] Add **Subscription Reader** role
  - [ ] **Register** `Microsoft.Fabric` **resource provider** *(Settings → Resource providers)*
- [ ] **Create Azure Resource Group**  
  ![Resource group](images/azure-resource-group.png)
  - [ ] Add **Contributor** role
- [ ] **Create resources** inside the Resource Group
  - [ ] **Microsoft Fabric**  
    ![Microsoft Fabric resource](images/azure-fabric-resource.png)
    - [ ] Create associated **reservations** via Reservation service
    - [ ] Check **Quotas** service
  - [ ] *(Optional)* **Azure Key Vault**  
    ![Key Vault](images/azure-key-vault.png)
    - [ ] Add **Key Vault secrets** (SP secrets, connection strings)
    - [ ] **Firewall exceptions** for identified IP addresses
  - [ ] *(Optional)* **Azure Storage** (Data Lake Storage Gen2)  
    ![Storage account](images/azure-storage.png)
  - [ ] *(Optional)* **Azure Data Factory** / **Synapse pipelines**  
    ![ADF](images/azure-adf.png)
  - [ ] *(Optional)* **Azure SQL Database**  
    ![Azure SQL DB](images/azure-sql-db.png)
    - [ ] **Firewall exceptions** for identified IP addresses

---

## 📊 4. Power BI / Fabric Portal
- [ ] Open **Admin gear** (top right) and **create Fabric trial** (if needed)  
  ![Fabric trial](images/fabric-trial.png)
- [ ] In **Admin portal → Tenant settings**, **add security group** to restrict enabled capabilities  
  ![Tenant settings](images/fabric-tenant-settings.png)
  - [ ] Enable: **Allow service principals to use Power BI APIs**
  - [ ] Review **all tenant** and **capacity admin** settings and enable as necessary
- [ ] **Understand admin levels**  
  ![Admin levels diagram](images/fabric-admin-levels.png)
  - [ ] **Tenant admin** (assigned in Azure)
  - [ ] **Capacity admin** (assigned in Power BI/Fabric; one or more capacities)
  - [ ] **Workspace admin** (per workspace)
- [ ] **Create initial workspace**  
  ![Workspace create](images/fabric-workspace.png)
  - [ ] Go to **Workspace settings** → **Enable Workspace identity**

---

## 🔗 5. Bridges: Cloud ↔ On‑Premises Data Sources
- [ ] **Download & Install on local server**  
  ![Gateway](images/powerbi-gateway.png)
  - [ ] **Power BI Gateway** (for on-prem data sources)
  - [ ] **Azure Integration Runtime** (Self-hosted)  
    ![Integration Runtime](images/azure-integration-runtime.png)

---

## 🧪 6. GitHub / Azure DevOps Setup *(Optional)*
- [ ] **Create Org, Project & Repo**  
  ![DevOps project](images/ado-project.png)
- [ ] **Connect Fabric workspace to repo** (Git integration)  
  ![Workspace Git connect](images/fabric-git-connect.png)

---

## 📈 7. Monitoring & Governance *(Optional)*
- [ ] **OneLake Catalog** → Review **Explore, Govern & Secure** tabs  
  ![OneLake Catalog](images/onelake-catalog.png)
- [ ] **Install monitoring tools**  
  ![Monitoring tools](images/fabric-monitoring.png)
  - [ ] **Capacity Metrics App**
  - [ ] **FUAM**, **FCA**, etc
- [ ] **Microsoft Purview** *(Optional)* – set up data governance, lineage, and policies  
  ![Purview](images/purview.png)

---

### Notes
- Replace `images/*.png` links with your own screenshots or architecture diagrams.
- Use this file in GitHub, Azure DevOps Wikis, or SharePoint for collaborative tracking.

---

*Generated on 2025-12-17 22:55*
