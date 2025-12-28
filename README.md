# StreamOps Infrastructure

Production-grade Azure cloud infrastructure for a streaming analytics platform, built with Terraform.

## Architecture

This project provisions a complete Azure environment including:

- **Virtual Network** (10.0.0.0/16) with public and private subnets
- **App Service** for hosting web applications
- **Azure SQL Database** with private networking
- **Storage Account** for data persistence
- **Application Insights** for monitoring and observability

## Infrastructure Components

| Resource | Purpose | Configuration |
|----------|---------|---------------|
| Resource Group | Logical container for all resources | Central US region |
| Virtual Network | Private network isolation | 10.0.0.0/16 address space |
| Public Subnet | Web-facing resources | 10.0.1.0/24 |
| Private Subnet | Database tier | 10.0.2.0/24 |
| App Service Plan | Compute tier | Linux, F1 (Free) SKU |
| Linux Web App | Application hosting | Python/Node.js support |
| SQL Server | Database server | Version 12.0, private access only |
| SQL Database | Data storage | Basic tier, 2GB |
| Storage Account | Blob/file storage | Locally redundant (LRS) |
| Application Insights | Monitoring | Web application type |

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) >= 1.5
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
- Azure subscription

## Usage

### 1. Clone and Initialize
```bash
git clone https://github.com/YOUR_USERNAME/streamops-infrastructure.git
cd streamops-infrastructure
terraform init
```

### 2. Authenticate with Azure
```bash
az login
az account set --subscription "YOUR_SUBSCRIPTION_ID"
```

### 3. Deploy Infrastructure
```bash
# Preview changes
terraform plan

# Deploy
terraform apply
```

### 4. Verify Deployment

After deployment completes, Terraform outputs the web app URL. The infrastructure is live and ready for application deployment.

### 5. Cleanup
```bash
terraform destroy
```

## Security Features

- SQL Database isolated in private subnet
- Public network access disabled on database server
- TLS 1.2 minimum for database connections
- Network segmentation between web and data tiers

## Production Considerations

This infrastructure uses free/basic tiers for learning purposes. For production:

- Upgrade to Standard/Premium SKUs
- Implement Azure Key Vault for secrets management
- Add private endpoints for all services
- Configure autoscaling for App Service
- Enable geo-replication for database
- Set up Azure Front Door or Application Gateway
- Implement backup and disaster recovery

## Cost

With free/basic tiers, this infrastructure costs approximately:
- App Service (F1): Free
- SQL Database (Basic): ~$5/month
- Storage Account: ~$0.02/month
- Application Insights: Free tier (first 5GB)

**Estimated total: ~$5/month**

## Learning Outcomes

This project demonstrates:
- Infrastructure as Code (IaC) with Terraform
- Azure networking and security best practices
- Resource dependency management
- Cloud architecture design patterns
- Cost-effective resource provisioning

## Author

Built by me as part of cloud infrastructure learning path.

## License

MIT