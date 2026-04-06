# Azure Secure VNet with Private Endpoint

This project demonstrates a secure Azure Virtual Network design that isolates workloads, restricts access, and enables private connectivity to Azure Storage using a Private Endpoint. It follows zero‑trust principles by ensuring that no public access is permitted to the Storage Account and that all traffic flows through private IP space.

The project was built manually in the Azure portal, with AI guidance used to help refine documentation, improve clarity, and ensure best‑practice explanations.

## Architecture Overview

Azure VNet (10.0.0.0/16)  
│  
├── Subnet: subnet-app (10.0.1.0/24)  
│     ├── NSG: nsg-subnet-app  
│     └── VM: vm-secure-app (private IP)  
│  
└── Private Endpoint → Storage Account (private IP)

This architecture ensures that:
- The VM communicates with the Storage Account privately.
- The Storage Account is not exposed to the public internet.
- The NSG enforces controlled inbound and outbound traffic.
- All traffic stays within Azure’s backbone network.

## Infrastructure Setup

### Resource Group
- **Name:** rg-secure-vnet-demo  
Used to logically group all resources for easier management and clean teardown.

### Virtual Network
- **Name:** vnet-secure-demo  
- **Address Space:** 10.0.0.0/16  
Provides the private IP space for all workloads.

### Subnets
- **subnet-app (10.0.1.0/24)**  
Dedicated application subnet hosting the VM and Private Endpoint.

## Components

| Component | Purpose |
|----------|---------|
| **VNet** | Defines the private network boundary for all resources |
| **Subnet** | Segments the VNet into isolated network zones |
| **NSG** | Controls inbound and outbound traffic using security rules |
| **VM** | Used to test private connectivity to the Storage Account |
| **Storage Account** | Target service for private access and connectivity validation |
| **Private Endpoint** | Provides a private IP for the Storage Account within the subnet |

## Deployment Steps

1. Create a Resource Group 
2. Deploy a Virtual Network and subnet  
3. Create an NSG and associate it with the subnet  
4. Deploy a Windows VM into the subnet  
5. Create a Storage Account  
6. Disable all public access to the Storage Account  
7. Create a Private Endpoint mapped to the Storage Account  
8. Validate that the VM can access the Storage Account privately  

Each step reinforces secure-by-default design:
- The VM has no public exposure.
- The Storage Account is reachable only through the Private Endpoint.
- The NSG ensures controlled access at the subnet boundary.

## Testing

Testing was performed from the VM to confirm that private connectivity was functioning correctly.

Validation steps:
- Verified that the Storage Account resolves to a **10.x.x.x** private IP.
- Uploaded and downloaded files using the Private Endpoint.
- Confirmed that the Storage Account cannot be reached from the public internet.
- Ensured that disabling the Private Endpoint breaks connectivity, proving isolation.

## What This Demonstrates

- Understanding of Azure networking fundamentals  
- Ability to design segmented, secure network topologies  
- Use of NSGs to enforce traffic control  
- Implementation of Private Endpoints for secure service access  
- Zero‑trust cloud design principles  
- Practical troubleshooting and validation of private connectivity  

## AI Assistance

AI guidance (Microsoft Copilot) was used to help structure the documentation, refine explanations, and ensure clarity. All Azure deployment, configuration, testing and validation were performed manually in the Azure portal.

## What This Demonstrates

- Azure networking fundamentals  
- Subnet isolation and NSG enforcement  
- Private service access using Private Endpoints  
- Zero‑trust cloud design  
- Practical troubleshooting and validation  
