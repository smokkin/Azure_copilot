# Azure Copilot Agents

A comprehensive guide to Azure Copilot's specialized agents for deployment, migration, and observability.

---

## Table of Contents

- [Deployment Agent](#deployment-agent)
- [Migration Agent](#migration-agent)
- [Observability Agent](#observability-agent)

---

## Deployment Agent

The Azure Copilot **Deployment agent** helps you design, configure, and deploy Azure infrastructure using best practices and automation. It streamlines everything from deciding which Azure services to use, to generating Infrastructure-as-Code templates, to integrating with CI/CD pipelines to deploy those resources.

### How It Works

The Deployment agent interprets your requirements and creates a detailed deployment plan, referencing the **Azure Well-Architected Framework (WAF)** and Azure architecture best practices to ensure the solution is robust, secure, and cost-effective.

> **Interactive Dialog:** The agent supports multi-turn conversations and may ask clarifying questions such as:
> - "What kind of redundancy do you need?"
> - "Is this a production or dev environment?"

### Key Capabilities

| Feature | Description |
|---------|-------------|
| **Infrastructure Design** | Recommends Azure services, configurations, security, and monitoring setups |
| **IaC Generation** | Translates finalized plans into **Terraform** configurations |
| **Code Review** | Opens generated files in an embedded editor or **Visual Studio Code for Web** |
| **GitHub Integration** | Automatically creates pull requests with new Terraform files |
| **Direct Deployment** | Provides step-by-step instructions to run Terraform configurations |
| **CI/CD Guidance** | Advises on connecting Terraform to **Azure DevOps** pipelines |
| **Cost Validation** | Cross-checks with **Azure Pricing Calculator** for cost estimates |
| **Best Practice Validation** | Uses **Azure Resource Graph** and **Azure Architecture Center** references |

### Example Scenarios

#### 1. Greenfield Environment Provisioning

**Prompt:** *"I want to deploy a highly available web application with a front-end, an API layer, a database, and monitoring."*

**Result:** The agent designs a multi-tier architecture including:
- **Azure Front Door** or **Azure Application Gateway**
- **App Service** for the web front-end
- **AKS** or **App Service** for the API layer
- **Azure SQL** or **Cosmos DB** for the database
- **Azure Monitor / App Insights** for observability
- Secure connectivity configurations
- Generated Terraform code for all resources

#### 2. Infrastructure-as-Code Automation

Organizations practicing IaC can use the Deployment agent to:
- Codify existing architecture in Terraform
- Ensure consistent **tags**, **naming conventions**, and **resource group structure**
- Maintain compliance with relevant policies
- Encapsulate Azure's evolving best practices

#### 3. Complex Multi-Service Deployments

**Example:** Deploying a data analytics pipeline with:
- **Event Hubs**
- **Databricks**
- **Data Lake Storage**
- **Power BI** integration

The agent outputs complete architecture with networking, governance, and Infrastructure as Code.

#### 4. Integration with DevOps Workflows

The agent integrates into enterprise change management systems by:
- Adjusting infrastructure based on prompts (e.g., adding subnets)
- Providing Terraform deltas or new configurations
- Creating GitHub pull requests for compliance checks
- Handling the heavy lifting of writing infrastructure code

> By automating design and code generation, the Deployment agent reduces human errors and increases continuous deployment velocity.

---

## Migration Agent

The Azure Copilot **Migration agent** helps you plan and execute the migration of workloads from on-premises or other cloud locations to Azure. It provides AI-driven guidance throughout the entire migration process.

### How It Works

1. **Discovery** — Surveys existing infrastructure and applications
2. **Assessment** — Analyzes workloads' utilization and configurations
3. **Planning** — Creates migration plans and business cases
4. **Provisioning** — Deploys target Azure Landing Zones
5. **Migration** — Executes migration using Azure native services
6. **Modernization** — Suggests platform updates and app modernization

### Key Capabilities

| Feature | Description |
|---------|-------------|
| **Discovery** | Identifies servers, VMs, databases, and applications in current estate |
| **Assessment** | Determines cloud readiness and optimal Azure sizing |
| **Migration Strategy** | Identifies "lift-and-shift" vs. modernization candidates |
| **Business Case** | Generates projected Azure costs, savings, and ROI |
| **Landing Zone Deployment** | Automates Azure Landing Zone provisioning per **Cloud Adoption Framework (CAF)** |
| **Native Migration Tools** | Uses **Azure Migrate** and **Azure Database Migration Service** |
| **Dependency Orchestration** | Groups dependent servers into migration waves |
| **Modernization** | Recommends OS updates, containerization, and code refactoring |

### Example Scenarios

#### 1. Cloud Adoption Planning

**Prompts:**
- *"What would it cost to move a specific application to Azure?"*
- *"Identify my 10 least-utilized servers that are easiest to migrate first."*

The agent applies discovery data and Azure pricing to provide answers and migration order recommendations.

#### 2. Bulk Server Migrations

The agent can:
- Discover hundreds of **VMware VMs**
- Generate migration plans and cost estimates
- Move VMs to **Azure VMs** or **Azure VMware Solution**
- Analyze dependencies and execute migrations in waves
- Ensure workloads land in preconfigured landing zones
- Verify post-move operation

#### 3. Database Migrations and Upgrades

Supports on-premises databases including:
- **SQL Server**
- **Oracle**
- **MySQL**

**Example:** Detecting an Oracle database that could move to **Azure Database for PostgreSQL**, providing schema change plans and using **Azure Database Migration Service**.

Also handles open-source migrations (e.g., MySQL → **Azure MySQL**) by consolidating assessment, schema conversion, and data migration into one orchestrated workflow.

#### 4. Application Modernization During Migration

The agent can propose replatforming:
- Web servers → **Azure App Service**
- Database tier → **Azure SQL Database**

It assesses app components and generates Infrastructure-as-Code templates. Integration with **GitHub Copilot** helps refactor hard-coded file paths or dependencies for cloud readiness.

> The Migration agent ties together discovery tools, cost analysis, Azure migration services, and code modernization into a guided migration experience.

---

## Observability Agent

The **Observability agent** focuses on infrastructure and application observability. Its goal is to help cloud operators ensure Azure resources and applications are performing well and to automatically investigate anomalies or alerts.

### Core Value

This agent brings AI into the monitoring domain — it can:
- Detect issues automatically
- Correlate data from different sources
- Suggest root causes without manual analysis

This significantly boosts incident response efficiency and system health management by proactively pinpointing problems in complex cloud systems.

### How It Functions

The Observability agent is deeply integrated with **Azure Monitor** and related services (**Application Insights**, **Log Analytics**, etc.).

#### AI-Driven Investigation Process

```
1. Gather Data
   ├── Metrics (CPU, memory, latency, request rates)
   ├── Logs (application logs, Azure diagnostics, activity logs)
   └── Traces (from affected resources and related components)

2. Anomaly Detection
   └── Scans for irregular patterns or errors around incident time

3. Cross-Source Correlation
   └── Links symptoms across resources to identify causal chains

4. Smart Scoping
   └── Widens analysis to potentially related resources

5. Findings & Insights
   └── Produces clear summaries with explanations and recommendations
```

#### Integration with Azure Monitor

All findings are attached to an **"issue"** context in Azure Monitor. When an alert triggers:
1. Select **"Investigate"**
2. The agent kicks off automatically
3. Results are posted into the issue timeline
4. Teams can review and collaborate on the incident record

> The agent's output is transparent — it provides supporting data (charts, log excerpts) so operators can validate findings or perform deeper manual analysis.

### Example Scenarios

#### 1. Automatic Alert Investigation

In an enterprise IT operations center with thousands of monitors:

| Alert Type | Agent Response |
|------------|----------------|
| **High CPU on VM** | Checks and finds nightly backup process caused spike → annotates: *"likely caused by backup job; no user impact"* |
| **Web service down** | Pinpoints that **Service A** is down because dependent **Service B** in another region had an outage |

This causal analysis across services significantly speeds up incident resolution.

#### 2. Performance Tuning and Anomaly Detection

**Prompt:** *"Why did our app's response time slow down yesterday around 3 PM?"*

The agent pulls monitoring data and might find:
> *"A third-party API call was timing out, causing queues to back up."*

**Proactive Query:** *"What's the latest on our system health? Any anomalies?"*

The agent could note:
> *"We're seeing an unusual increase in error rate on Service X since this morning."*

#### 3. Correlating Across Logs and Metrics

For a given user-facing error, the agent can:
- Retrieve relevant **Application Insights** logs (exceptions)
- Match to spikes in **Azure Function** execution time metrics
- Highlight dependency calls that took unusually long

**Example Narrative:**
> *"The function slowed down due to slow DB queries; logs show timeout exceptions at the same time."*

#### 4. Multi-Resource Incidents

When multiple alerts fire simultaneously (database, app, cache all showing errors):
- The agent determines if one root cause triggered cascading failures
- Clusters alerts into a single **"issue"**
- Surfaces the primary fault

This prevents confusion and duplicated effort during high-stress incidents.

#### 5. Guidance for Resolution

| Finding | Recommendation |
|---------|----------------|
| Memory leak pattern (memory rising until crash) | Increase memory or review recent code changes for leaks |
| Traffic spike caused issue | Enable autoscale or upgrade pricing tier |
| Recent deployment introduced errors | Roll back the deployment |

### Business Impact

| Benefit | Description |
|---------|-------------|
| **Reduced MTTR** | Automates incident analysis, freeing engineers to focus on fixes |
| **Knowledge Democratization** | Helps less-experienced team members interpret complex monitoring data |
| **Signal Filtering** | Acts as a smart filter and analyst as observability data volume scales |
| **Hidden Dependency Detection** | Catches correlations humans might miss in microservices/distributed systems |

> The Observability agent effectively automates much of what a skilled SRE or support engineer would do when faced with an alert — checking metrics, cross-checking logs, correlating events, and hypothesizing causes — all in seconds rather than hours.

---

## Quick Reference

| Agent | Primary Use Case | Key Integration |
|-------|-----------------|-----------------|
| **Deployment** | Design & deploy Azure infrastructure | Terraform, Azure DevOps, GitHub |
| **Migration** | Move workloads to Azure | Azure Migrate, Database Migration Service, CAF |
| **Observability** | Monitor & diagnose issues | Azure Monitor, Application Insights, Log Analytics |

---

## Resources

- [Azure Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/)
- [Azure Architecture Center](https://learn.microsoft.com/azure/architecture/)
- [Cloud Adoption Framework](https://learn.microsoft.com/azure/cloud-adoption-framework/)
- [Azure Monitor Documentation](https://learn.microsoft.com/azure/azure-monitor/)
- [Azure Migrate Documentation](https://learn.microsoft.com/azure/migrate/)
- [Terraform on Azure](https://learn.microsoft.com/azure/developer/terraform/)
