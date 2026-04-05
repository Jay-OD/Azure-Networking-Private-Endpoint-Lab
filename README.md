# Azure Secure VNet with Private Endpoint

This project demonstrates a secure Azure Virtual Network design using:
- A VNet and subnet
- A Network Security Group (NSG)
- A virtual machine for testing
- A Storage Account locked behind a Private Endpoint
- No public access to storage

The goal is to show practical cloud networking skills, private service access, and zero‑trust design principles suitable for early‑career cloud engineering roles.

## Architecture Overview

Azure VNet (10.0.0.0/16)
│
├── Subnet: subnet-app (10.0.1.0/24)
│     ├── NSG: nsg-subnet-app
│     └── VM: vm-secure-app (private IP)
│
└── Private Endpoint → Storage Account (private IP)

## Components

| Component | Purpose |
|----------|---------|
| **VNet** | Private network boundary for Azure resources |
| **Subnet** | Segmented network space for workloads |
| **NSG** | Controls inbound and outbound traffic |
| **VM** | Used to test private connectivity to storage |
| **Storage Account** | Target service for private access |
| **Private Endpoint** | Provides private IP access to storage |

## Deployment Steps

1. Create a Resource Group: rg-secure-vnet-demo
2. Create a VNet and subnet  
3. Create an NSG and associate it with the subnet  
4. Deploy a VM into the subnet  
5. Create a Storage Account  
6. Disable public access to the Storage Account  
7. Create a Private Endpoint connected to the subnet  
8. Test connectivity from the VM to the Storage Account  

## Testing

- Confirm the VM resolves the Storage Account to a private IP  
- Upload/download a file via the Private Endpoint  
- Confirm the Storage Account is not reachable from the public internet  

## What This Demonstrates

- Azure networking fundamentals  
- Subnet isolation and NSG enforcement  
- Private service access using Private Endpoints  
- Zero‑trust cloud design  
- Practical troubleshooting and validation  
