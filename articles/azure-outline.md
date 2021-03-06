# Azure outline #

## Content ##

- [Foundational Concepts](#foundational-concepts)
  - [Why cloud?](#why-cloud)
  - [Elements of the Cloud Computing Model](#elements-of-the-cloud-computing-model)
  - [Cloud Infrastructure Models](#cloud-infrastructure-models)
  - [Cloud Deliver Models](#cloud-deliver-models)
- [Virtual Machines](#virtual-machines)
  - [Which Model is Best For Your Workload?](#which-model-is-best-for-your-workload)
  - [Things to Keep in Mind Regarding Azure VMs](#things-to-keep-in-mind-regarding-azure-vms)
  - [Virtual Machine Resources](#virtual-machine-resources)
  - [Azure VMs base types](#azure-vms-base-types)
  - [Connect to Windows VMs](#connect-to-windows-vms)
  - [Connect to Linux VMs](#connect-to-linux-vms)
- [Storage](#storage)
  - [Things to Keep in Mind Regarding Azure Storage for IaaS VMs](#things-to-keep-in-mind-regarding-azure-storage-for-iaas-vms)
  - [Azure Storage Types](#azure-storage-types)
  - [Replication Options](#replication-options)
  - [Azure VM Disk Types](#azure-vm-disk-types)
  - [Azure Storage Account Types](#azure-storage-account-types)
  - [Virtual Network Service Endpoints](#virtual-network-service-endpoints)
  - [Host Caching](#host-caching)
- [VM Configuration](#vm-configuration)
  - [Things to Keep in Mind Regarding Azure VMs Configuration](#things-to-keep-in-mind-regarding-azure-vms-configuration)
- [Scaling and High Availability](#scaling-and-high-availability)
  - [Things to Keep in Mind Regarding Scaling and High Availability](#things-to-keep-in-mind-regarding-scaling-and-high-availability)
  - [Azure Maintenance Events](#azure-maintenance-events)
  - [Fault and Update Domains](#fault-and-update-domains)
  - [VM scale set](#vm-scale-set)
  - [Scale set use cases](#scale-set-use-cases)
  - [Load balancer](#load-balancer)
  - [Application gateway](#application-gateway)
  - [Traffic manager](#traffic-manager)
- [Networking](#networking)
  - [When multiple VNets make sense](#when-multiple-vnets-make-sense)
  - [VNet-to-VNet VPN](#vnet-to-vnet-vpn)
  - [VNet-to-VNet VPN Points to Ponder](#vnet-to-vnet-vpn-points-to-ponder)
  - [Inter-VNet troubleshooting tips](#inter-vnet-troubleshooting-tips)
  - [Troubleshooting](#troubleshooting)
  - [Things to Keep in Mind Regarding Networking](#things-to-keep-in-mind-regarding-networking)
  - [Public IP address SKUs](#public-ip-address-skus)
  - [Azure VPN SKUs](#azure-vpn-skus)
  - [Name Resolution for Azure VNets](#name-resolution-for-azure-vnets)
  - [Azure VNet Design Best Practices](#azure-vnet-design-best-practices)
  - [Network Security Groups](#network-security-groups)
  - [VM IP addressing best practices](#vm-ip-addressing-best-practices)
- [Security](#security)
  - [Terminology](#terminology)
  - [Access Concepts](#access-concepts)
  - [Things to Keep in Mind Regarding Security](#things-to-keep-in-mind-regarding-security)
  - [Protect the Storage Subsystem](#protect-the-storage-subsystem)
  - [Roles](#roles)
  - [Azure Resource Manager Policies](#azure-resource-manager-policies)
  - [Data Plane Security](#data-plane-security)
  - [Encryption in Transit](#encryption-in-transit)
  - [Encryption at Rest](#encryption-at-rest)
  - [Storage Analytics](#storage-analytics)
  - [Firewall](#firewall)
  - [Antimalware](#antimalware)
  - [Azure Security Center](#azure-security-center)
  - [ASC policy component](#asc-policy-component)
  - [Azure activity log](#azure-activity-log)
  - [Patch Management for Azure VMs](#patch-management-for-azure-vms)
- [Monitoring](#monitoring)
  - [Three monitoring tiers](#three-monitoring-tiers)
  - [Ways to check Azure service status](#ways-to-check-azure-service-status)
  - [Things to Keep in Mind Regarding Azure VM Monitoring](#things-to-keep-in-mind-regarding-azure-vm-monitoring)
  - [Tools](#tools)
  - [Monitoring - A layer Approach](#monitoring---a-layer-approach)
  - [Monitoring and Diagnostics Pipeline](#monitoring-and-diagnostics-pipeline)
  - [Azure Monitor Components](#azure-monitor-components)
  - [Azure diagnostics data](#azure-diagnostics-data)
  - [Azure resource log](#azure-resource-log)
  - [Monitoring - Questions of scale and intelligence](#monitoring---questions-of-scale-and-intelligence)
  - [Log Analytics](#log-analytics)
  - [What can you do with Webhooks](#what-can-you-do-with-webhooks)
- [Troubleshooting and support](#troubleshooting-and-support)
  - [Azure VM troubleshooting checklist](#azure-vm-troubleshooting-checklist)
- [Cost management](#cost-management)
  - [How to buy azure services](#how-to-buy-azure-services)
  - [Azure SLA](#azure-sla)
  - [Azure support plans](#azure-support-plans)
- [Managed disks](#managed-disks)
  - [Storage account limits](#storage-account-limits)
  - [Value proposition](#value-proposition)
  - [Managed disks facts](#managed-disks-facts)
- [Help and support](#help-and-support)
  - [Azure support issue types](#azure-support-issue-types)

## Foundational Concepts ##

### Why cloud? ###

- CapEx vs. OpEx
  - [CapEx](https://www.investopedia.com/terms/c/capitalexpenditure.asp) - Capital expenditure or capital expense (capex or CAPEX) is the money a company spends to buy, maintain, or improve its fixed assets, such as buildings, vehicles, equipment, or land.
  - [OpEx](https://en.wikipedia.org/wiki/Operating_expense) - An operating expense, operating expenditure, operational expense, operational expenditure or OpEx is an ongoing cost for running a product, business, or system
- How old is your technology?
- How flexible is your infrastructure?
- How much [redundancy](https://en.wikipedia.org/wiki/Redundancy_(engineering)) do you have?
- How well do you [scale](https://en.wikipedia.org/wiki/Scalability)?

### Elements of the Cloud Computing Model ###

- [Elasticity](https://sdqweb.ipd.kit.edu/publications/pdfs/HeKoRe2013-ICAC-Elasticity.pdf)
  - Dynamically adjust to service demand
  - Short-term strategy
- [Scalability](https://en.wikipedia.org/wiki/Scalability)
  - Vertical and horizontal
  - Long-term strategy
- [Pooling](https://blogs.technet.microsoft.com/yungchou/2013/08/08/resource-pooling-virtualization-fabric-and-cloud/)
  - Compute, storage, network
  - Services "on tap"
  - Pay only for what you use
- [Provisioning](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-automatic-user-provisioning-portal)
  - Self-service
  - RBAC - Role Based Access Control
  
  ### Cloud Infrastructure Models ###
  
- [Public](https://azure.microsoft.com/en-us/overview/what-is-a-public-cloud/)
  - All services exist in the internet
  - Multi-tenancy
  - Azure
- [Private](https://azure.microsoft.com/en-us/overview/what-is-a-private-cloud/)
  - All services exists in the private network complex
  - System center
  - Azure Stack
- [Hybrid](https://azure.microsoft.com/en-in/overview/what-is-hybrid-cloud-computing/)
  - Secure, private connection between public and private clouds
  - VPN or ExpressRoute
  
  ### Cloud Deliver Models ###
  
 - [SaaS](https://azure.microsoft.com/en-us/overview/what-is-saas/)
   - Target: Office 365
 - [PaaS](https://azure.microsoft.com/en-us/overview/what-is-paas/)
   - Target:
     - Developer
     - Azure App Service
- [IaaS](https://azure.microsoft.com/en-us/overview/what-is-iaas/)
  - Target:
    - Sysadmin
    - Azure Virtual Machines

** [Availability Zone](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview) - zone of availability inside the region
A region is a set of Azure data centers in a named geographic location. Every Azure resource, including virtual machines, is assigned a region

## Virtual Machines ##

### Which Model is Best For Your Workload? ###

- [PaaS](https://azure.microsoft.com/en-us/overview/what-is-paas/)
  - Higher agility
  - Higher ease of management
  - Lower degree of control
  - Lower support for legacy apps
- [IaaS](https://azure.microsoft.com/en-us/overview/what-is-iaas/) (VM's)
  - Higher degree of control
  - Higher support for legacy apps
  - Lower ease of management
  - Lower agility
  
### Things to Keep in Mind Regarding Azure VMs ###
  
- Unless the VM is deallocated, it still incurs [charge](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/windows/)
- Deleting the VM doesn't delete the [managed disk](https://github.com/MicrosoftDocs/azure-docs/blob/master/includes/virtual-machines-managed-disks-overview.md)
- Related assets are charged separately
- You can't connect without an [NSG](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group) (network security group) rule
- You can't connect to VMs in other [virtual networks](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
- [DNS](https://en.wikipedia.org/wiki/Domain_Name_System) names require creativity and should be standardized

### Virtual Machine Resources ###

- [SRP](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services) (storage resource provider)
  - [Disk](https://azure.microsoft.com/en-us/services/storage/disks/) (blob)
  - [Storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview)
- [CRP](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services) (compute resource provider)
  - [Virtual machine](https://azure.microsoft.com/en-us/services/virtual-machines/)
  - [Availability set](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability)
- [NRP](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services) (network resource provider)
  - [VM IP address](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-deploy-static-pip-arm-portal)
  - [Virtual network](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
  - [NSG](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group)
  - [Load balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)
  
Scale refers to adding network bandwidth, memory, storage, or compute power to achieve better performance.

Scaling up, or vertical scaling, means to increase the memory, storage, or compute power on an existing virtual machine. For example, you can add additional memory to a web or database server to make it run faster.

Scaling out, or horizontal scaling, means to add extra virtual machines to power your application. For example, you might create many virtual machines configured in exactly the same way and use a load balancer to distribute work across them.

[Azure Advisor](https://azure.microsoft.com/en-us/services/advisor/) and [Azure Cost Management](https://azure.microsoft.com/en-us/services/cost-management/) are two services that help you optimize cloud spend. You can use these services to identify where you're using more than you need, and then scale back to the capacity you're actually using.

### Azure VMs base types ###

Type | Sizes | Description
--- | --- | ---
[General purpose](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-general) | Dsv3, Dv3, DSv2, Dv2, DS, D, Av2, A0-7 | Balanced CPU-to-memory. Ideal for dev/test and small to medium applications and data solutions.
[Compute optimized](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-compute) | Fs, F | High CPU-to-memory. Good for medium-traffic applications, network appliances, and batch processes.
[Memory optimized](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes-memory) | Esv3, Ev3, M, GS, G, DSv2, DS, Dv2, D | High memory-to-core. Great for relational databases, medium to large caches, and in-memory analytics.
[Storage optimized](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes-storage) | Ls | High disk throughput and IO. Ideal for big data, SQL, and NoSQL databases.
[GPU optimized](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-gpu) | NV, NC | Specialized VMs targeted for heavy graphic rendering and video editing.
[High performance](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-hpc) | H, A8-11 | Our most powerful CPU VMs with optional high-throughput network interfaces (RDMA).

### Connect to Windows VMs ###

- [RDP](https://docs.microsoft.com/en-us/windows/desktop/TermServ/remote-desktop-protocol)
  - [TCP](https://tools.ietf.org/html/rfc793) 3389
  - relies upon the [NSG](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group)
- [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-6)
  - [TCP](https://tools.ietf.org/html/rfc793) 5985/5986

### Connect to Linux VMs ###

- Secure Shell ([SSH](https://www.ietf.org/rfc/rfc4253.txt))
  - Industry standard, secure remote access protocol
- [Authentication](https://www.cryptomathic.com/news-events/blog/digital-authentication-the-basics)
  - Password or keys
- [RDP](https://docs.microsoft.com/en-us/windows/desktop/TermServ/remote-desktop-protocol)
  - Install a desktop environment, [RDP server](http://www.xrdp.org/), and [create an NSG rule](https://docs.microsoft.com/en-us/cli/azure/network/nsg/rule?view=azure-cli-latest)

## Storage ##

### Things to Keep in Mind Regarding Azure Storage for IaaS VMs ###

- [Standard disks](https://azure.microsoft.com/en-us/pricing/details/managed-disks/) cost per transaction and per GB
- [Premium disks](https://azure.microsoft.com/en-us/pricing/details/managed-disks/) aren't charged by transaction
- Azure holds an infinite lease on page blobs
- [Blob](https://azure.microsoft.com/en-us/services/storage/blobs/) storage namespace is flat
- [Premium storage](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage) supports only [LRS](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy-lrs)
- 99.9% read/write availability [SLA](https://azure.microsoft.com/en-us/support/legal/sla/)

### Azure Storage Types ###

- [Blob](https://azure.microsoft.com/en-us/services/storage/blobs/) - unstructured file data.
  - A collection of binary data stored as a single entity in a storage system. Blobs are typically images, audio or other multimedia objects, or binary executable code. VM VHDs are stored as page blobs. 
- [Table](https://azure.microsoft.com/en-us/services/storage/tables/) - NoSQL semi-structured data
- [Queue](https://azure.microsoft.com/en-us/services/storage/queues/) - pub\sub messaging data
- [File storage](https://azure.microsoft.com/en-us/services/storage/files/) - SMB file shares

### Replication Options ###

- [LRS](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy-lrs) Locally redundant storage
  - 3 copies withn single data center in single region
  - For [premium storage](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage) only
- [ZRS](https://azure.microsoft.com/en-us/blog/azure-zone-redundant-storage-in-public-preview/) Zore redundant storage
  - 3 copies across 2-3 data centers in single region
  - block blobs only; available only during SA creation
  - available only at VM creation
- [GRS](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy-grs) Geo redundant storage
  - 3 copies in primary region
  - 3 copies in secondary region
- [RA-GRS](https://docs.microsoft.com/en-us/azure/storage/common/storage-designing-ha-apps-with-ragrs) Read-Access geo redundant storage
  - RO access to secondary region data

### Azure VM Disk Types ###

- [OS Disks](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/about-disks-and-vhds#operating-system-disk)
  - Fixed disk VHD files stored as page blobs
  - Generation 1 (VHD) // Generation 2 is VHDx format
  - Registered as SATA
  - Maximum size 1023 GB (1TB)
- [Data Disks](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/about-disks-and-vhds#data-disk)
  - D: is a temporary disk that holds pagefile/swapfile
  - Attached VHD
  - Registered as SCSI
  - Maximum size 1023 GB (1TB)

### Azure Storage Account Types ###

- [Standard](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/standard-storage)
  - HDD
  - Default for some instances sizes; others use SSD
  - IOPS values represent maximum values (IOPS input-ouput per second)
  - Can use any redundancy option (Premium is [LRS](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy-lrs) only)
- [Premium](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage-performance)
  - SSD
  - OIPS alues represent expected performance levels (not maximum)
  - Great for I/O intensive workloads like Dynamics, Exchange Server, SQL server
  - Not available in all Azure regions
  - Need a [DSv2](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-general#dsv2-series)-, [DSv3](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-general#dsv3-series-sup1sup)-, [GS](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-memory#gs-series)-, or [FS](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes-compute#fs-series-sup1sup)-series VM
  - Available in 3 sizes (128 GB, 512 GB, or 1024 GB)

### Virtual Network Service Endpoints ###

Associate a storage account with a VNet
Limit access to storage account from VNet
[NAT](https://tools.ietf.org/html/rfc4787) rules to support on-premises connection (NAT network address rules)

### Host Caching ###

Host - is hardware host, HyperV VM

- [None](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage-performance#disk-caching)
  - Disable on IaaS DCs
  - Good for random I/O
- [Read only](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage-performance#disk-caching)
  - Write-through
  - Stored on disk and RAM of host OS
- [Read\write](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage-performance#disk-caching)
  - Write-back
  - Stored in memory of host OS

## VM Configuration ##

### Things to Keep in Mind Regarding Azure VMs Configuration ###

- [NSG rules](https://blogs.msdn.microsoft.com/igorpag/2016/05/14/azure-network-security-groups-nsg-best-practices-and-lessons-learned/)
- Need [availability sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets) for 99.95% [SLA](https://azure.microsoft.com/en-us/support/legal/sla/)
- [Premium storage](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/premium-storage) offers 99.9% for single VMs
- [Shared responsibility model](https://blogs.msdn.microsoft.com/azuresecurity/2016/04/18/what-does-shared-responsibility-in-the-cloud-mean/)
- Combine [Azure Load Balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview) with [Avail. Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets)
- Use separate [storage accounts](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview) for each VM
	
** to connect to an Azure-based VM that isn't in your [Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis) domain add an entry to workstation's Trusted Hosts list.

## Scaling and High Availability ##

### Things to Keep in Mind Regarding Scaling and High Availability ###

- Group related VMs into [availability sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets)
- Combine a load balancer with [availabiilty sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets)
- Consider [Scale Sets](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview) for bigger compute jobs
- Know that [AS](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets) and [SS](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/overview) both incur runtime charges
- Premium storage supports single-instance [SLA](https://azure.microsoft.com/en-us/support/legal/sla/)

### Azure Maintenance Events ###

- [Planned](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/scheduled-events) - the azure team gives you advances notification
- Unplanned - rack - or datacenter-level failures

### Fault and Update Domains ###

- [Fault domains](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability#configure-multiple-virtual-machines-in-an-availability-set-for-redundancy) are VMs that share the same power source and switch
  - 3 fault domains available
- [Update domains](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/manage-availability#configure-multiple-virtual-machines-in-an-availability-set-for-redundancy) are VMs that share the same hardware host
  - 5-20 update domain available
- Place VMs of each app tier into their own [availability sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets)

** Availability set can be configured only when creating a VM workaround can be done via PS

### VM scale set ###

- Platform-independent [PaaS](https://azure.microsoft.com/en-us/overview/what-is-paas/)
  - [Azure App Service](https://azure.microsoft.com/en-us/services/app-service/) is known for elastic [auto scaling](https://azure.microsoft.com/en-us/features/autoscale/)
- Method for:
  - Deploying and managing Azure VMs as a set
  - [Scalable compute platform](https://azure.microsoft.com/en-us/solutions/big-compute/)
- Integrated with:
  - [Azure load balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)
  - [Azure auto scale](https://azure.microsoft.com/en-us/features/autoscale/)

** scale set

### Scale set use cases ###

- [Hyperscale workloads](https://en.wikipedia.org/wiki/Hyperscale_computing)
- Stateless web frontends
- [Container orchestration](https://azure.microsoft.com/en-us/blog/tag/container-orchestration/)
- [Microservices clusters](https://azure.microsoft.com/en-in/services/service-fabric/)

### Load balancer ###

- [Entity](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview) which watches to the internet and distributes traffic among recipients
- A secure entry point to VNet
- Works at [OSI](https://docs.microsoft.com/en-us/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model) [layer 4](https://en.wikipedia.org/wiki/OSI_model#Layer_4:_Transport_Layer) (TCP/UDP)
- Uses 5-tuple has algorithm
  - Source and destination IP
  - Source and destination port
  - Protocol

### Application gateway ###

- [Entity](https://docs.microsoft.com/en-us/azure/application-gateway/overview) which works OSI layer 7 (HTTP/HTTPS)
- [SSL](http://info.ssl.com/article.aspx?id=10241) offload

### Traffic manager ###

- [Global load balancer](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview)
- Uses [DNS](https://azure.microsoft.com/en-us/services/dns/)
- [Geo-distributed services](https://azure.microsoft.com/en-us/blog/tag/geo-distributed-applications/)

## Networking ##

*[Virtual Network](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview) (VNet)* - is a communications and security boundary that enables Azure resources (virtual machines, storage accounts, App Services apps, Azure SQL Database instances) to communicate with each other securely.

- 50-100 VNets allowed per subscription
- Provides [network isolation](https://docs.microsoft.com/en-us/azure/security/azure-isolation#networking-isolation) and [segmentation](https://docs.microsoft.com/en-us/azure/security/azure-network-security)
- Name resolution (Azure-provided DNS; [Azure DNS service](https://azure.microsoft.com/en-us/services/dns/))
- Traffic filtering (NSGs, [network virtual appliances](https://azure.microsoft.com/en-us/solutions/network-appliances/))

### When multiple VNets make sense ###

- Saving money
  - Share a [network virtual appliance](https://azure.microsoft.com/en-us/solutions/network-appliances/) among several [VNets](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview) (service chaining)
- Segmentation workloads
  - [NSGs](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group) and [UDRs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview) give you routing and traffic control
- [Securing traffic](https://docs.microsoft.com/en-us/azure/security/azure-security-network-security-best-practices)
  - Private connectivity that uses the Microsoft backbone network

*[Virtual Private Network](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways) (VPN)* - is a secure connection over an unsecure medium. Azure [site-to-site](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) VPNs use [IPSec/IKE](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) tunnels

### VNet-to-VNet VPN ###

[Ref](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-vnet-vnet-resource-manager-portal)

- Create isolation or administrative boundaries
- Provide cross-region geo-redundancy and replication securely
- No traffic crosses the public internet
- Private IP addressing
	
### VNet-to-VNet VPN Points to Ponder ###

- Different pricing model from [VNet peering](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)
- Make sure your [VNet address spaces](https://blogs.msdn.microsoft.com/premier_developer/2018/10/22/understanding-cidr-notation-when-designing-azure-virtual-networks-and-subnets/) do not overlap
- Global VNet peering means you no longer need a [VPN gateway](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways) for cross-region connectivity

** for P2S and VNet-to-VNet VPN deploy route-based [Azure VPN gateway](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways)

*[Network Peering](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)* - is a seamless connection between two Azure virtual networks. The peered networks appear as one, or connectivity purposes.

### Inter-VNet troubleshooting tips ###

- Azure blocks [ICMP](https://tools.ietf.org/html/rfc792) (Internet Communication Messaging Protocol (uses for ping)) between VNets and the internet
- Simplify your NSGs as much as possible to reduce troubleshooting friction
- Azure portal diagnose and solve problems/Resource Health blade is useful
- [Network watcher](https://docs.microsoft.com/en-us/azure/network-watcher/network-watcher-monitoring-overview) and [network performance monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor) make troubleshooting much easier

### Troubleshooting ###

- [tcping](https://github.com/cloverstd/tcping)
- [Network watcher](https://docs.microsoft.com/en-us/azure/network-watcher/network-watcher-monitoring-overview)
  - Enable for your azure region(s)
  - Install VM extension
- [Network performance monitor]((https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor)) (NPM)
  - Part of [Insight](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) & [Analytics](https://azure.microsoft.com/en-us/resources/videos/azure-insight-analytics/) azure management solution
  - [Log analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/log-faq) workspace
  - [Microsoft monitoring agent](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/agents-overview)

### Things to Keep in Mind Regarding Networking ###

- Most regions support [dual-stack IP](https://www.cisco.com/c/dam/en/us/products/collateral/ios-nx-os-software/enterprise-ipv6-solution/aag_c45-625513.pdf)
- Reserved public IPs can be chargeable
- [Vnet-to-Vnet](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-vnet-vnet-resource-manager-portal) requires peering or VPN
- Remember NSG and Windows Firewall
- Configuring a local [VPN gateway](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways) has complexity
- [Azure DNS](https://azure.microsoft.com/en-us/services/dns/) questions

### Public IP address SKUs ###

- Basic
  - The original public IP address
  - Static or dynamic allocation
  - Assigned to any public IP-addressable resource
  - Can be assigned to a specific [availability zone](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview)
  - Not zone redundant
- Standard
  - Different price point
  - Static allocation only
  - Assigned to [vNICs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-network-interface) or standard [internet-facing load balancers](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-get-started-internet-classic-cloud)
  - Zone redundant by default

### Azure VPN SKUs ###

[Ref](https://azure.microsoft.com/en-us/pricing/details/vpn-gateway/)

| | BANDWIDTH | S2S TUNNELS | P2S TUNNELS | 
| --- | --- | --- | --- |
| Basic | 100 Mbps | Max 10 1-10: Included | Max 128 1-128: Included |
| VpnGw1 | 650 Mbps | Max 30 1-10: Included | Max 128 1-128: Included |
| VpnGw2 | 1 Gbps | Max 30 1-10: Included | Max 128 1-128: Included |
| VpnGw3 | 1.25 Gbps | Max 30 1-10: Included | Max 128 1-128: Included |

- Basic
  - 80-100 Mbps, 99.9% SLA
- Dev/test
- New SKUs all have 99.95% SLA and are faster
  - VpnGw1
    - 650 Mbps
  - VpnGw2
    - 1 Gbps
  - VpnGw3
    - 1.25 Gbps

### Name Resolution for Azure VNets ###

- Azure-provided [name resolution](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)
  - No configuration required
  - All VMs within a VNet can resolve each others' host names
  - Issue: cross-VNet name resolution
  - Issue: No custom DNS suffix
  - You can add custom DNS server IP addresses
  - You can host your own DNS server(s)
- [Azure DNS](https://azure.microsoft.com/en-us/services/dns/)
  - Host your public DNS domain in Azure
    - Use Azure geo-distributed name servers
  - Create [private DNS zones](https://docs.microsoft.com/en-us/azure/dns/private-dns-overview)
    - Linked to VNets
    - Registration VNet
    - Resolution VNet

### Azure VNet Design Best Practices ###

- Create subnets based on workloads
- Bind network security groups ([NSGs](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group)) at the subnet level
- Deploy a network virtual appliance ([NVA](https://azure.microsoft.com/en-us/solutions/network-appliances/)) and user-defined routes ([UDRs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview)) to further customize traffic
- Implement [site-to-site](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal) or [point-to-site](https://docs.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about) VPN tunnels with on-premises environment
	
### Network Security Groups ###
	
  **([NSGs](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group))
  **Software firewall object

- Stateful firewall for inbound and outbound traffic
- 5-tuple hash src+dst IP and ports; protocol
- [Default rules](https://docs.microsoft.com/en-us/rest/api/virtualnetwork/defaultsecurityrules)
- [Augmented rules](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview#augmented-security-rules)
- [Service tags and ASGs](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview#service-tags)
- Bound to [vNIC](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-network-interface) or subnet
	
### VM IP addressing best practices ###

- If a VM doesn't need a public IP address ([PIP](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-ip-addresses-overview-arm)), then don't assign one and use an [Azure load balancer](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview) instead
- Plan your VNet private address space to avoid overlap
- Never configure networking from within the VM

## Security ##

### Terminology ###

*[Asset](https://www.iso.org/standard/39066.html)* - people, property, or information (databases, software, code, company records)

*[Threat](https://tools.ietf.org/html/rfc2828)* - person or process that can exploit a vulnerability (intentionally or accidentally) to obtain, damage or destroy an asset

*[Vulnerability](https://en.wikipedia.org/wiki/Vulnerability_(computing))* - weakness or gap in a security program that can be exploited by threats to gain unauthorized access to an asset

*[Risk](https://en.wikipedia.org/wiki/Computer_security#Systems_at_risk)* - the potential for loss, damage, or destruction of an asset as a result of a threat exploiting a vulnerability

### Access Concepts ###

- Least privilege
  - Limiting resource access to what is necessary and no more (scope permissions)
- [RBAC](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview)
  - Regulating resource access based on job role

### Things to Keep in Mind Regarding Security ###

- Azure conforms with many compliance certs
- Leverage defence in depth
- You can get Microsoft's permissions to run pen tests
- Consider [virtual network security appliances](https://azure.microsoft.com/en-us/solutions/network-appliances/)
- Control [routing behaviour](https://azure.microsoft.com/mediahandler/files/resourcefiles/security-best-practices-for-azure-solutions/Azure%20Security%20Best%20Practices.pdf)
- Enable [azure security center](https://azure.microsoft.com/en-us/services/security-center/)

- Logically segment subnets
  - Use [NSGs](https://docs.microsoft.com/en-us/azure/virtual-network/manage-network-security-group) for inter-subnet traffic
- Control routing
  - Consider [virtual network appliances](https://azure.microsoft.com/en-us/solutions/network-appliances/)
- Enable forced tunneling
  - Constrain [outbound VM traffic](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections)
- Disable [RDP](https://docs.microsoft.com/en-us/windows/desktop/TermServ/remote-desktop-protocol)/[SSH](https://www.ssh.com/)
  - Employ [VPNs](https://azure.microsoft.com/en-us/services/vpn-gateway/) and [jump box](https://docs.microsoft.com/en-us/azure/security/azure-security-management#azure-operations)
- [Web Application Firewall](https://docs.microsoft.com/en-us/azure/application-gateway/waf-overview)
  - Centralised web application protection from [common exploits and vulnerabilities](https://cve.mitre.org/)
- [DDoS Protection](https://docs.microsoft.com/en-us/azure/virtual-network/ddos-protection-overview)
  - Always-on traffic monitoring and [real-time DDoS mitigation](https://azure.microsoft.com/en-us/services/ddos-protection/)
- [Azure Security Center](https://docs.microsoft.com/en-us/azure/security-center/)
  - Unify security management and enable [advanced threat protection](https://docs.microsoft.com/en-us/azure-advanced-threat-protection/what-is-atp)


### Protect the Storage Subsystem ###

- [Protecting the storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-security-guide) account itself
  - [Managed disk storage](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/managed-disks-overview) vs. [traditional storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction)
- [RBAC](https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal)
  - Simplify it AMAP
- [Storage account keys](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-manage#access-keys) (use for traditional storage accounts)
  - 512-bit string created by Azure
  - [Key rollover](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-ovw-storage-keys)
  - [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/)
    - Secret protection store

#### Role based access control (RBAC) ####
regulating resource access based on job role. It is a granular, role-based resource access to users, groups, and applications.

### Roles ###

- [Owner](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#owner)
  - Full access to all resources
  - Delegate access to others
- [Contributor](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#contributor)
  - Create and manage all of types of Azure resources
  - Cannot grant access to others
- [Reader](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#reader)
  - View Azure resources
- [User access administrator](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#user-access-administrator)
  - Manage user access to Azure resources
- [Custom](https://docs.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles)
  - Defined programmatically with JSON, PS, CLI or REST API

### Azure Resource Manager Policies ###

- [RBAC](https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal) focuses on [user actions at different scopes](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/roles-permissions-security)
- [ARM policies](https://docs.microsoft.com/en-us/azure/governance/policy/overview) focus on resource properties during deployment
  - Require [tags](https://docs.microsoft.com/en-us/rest/api/resources/tags) for [cost center management](https://azure.microsoft.com/en-us/updates/introducing-native-azure-cost-management-preview/)
  - Constrain resources to particular regions
- Create policy definitions with JSON
  - [New-AzureRmPolicyDefinition](https://docs.microsoft.com/en-us/powershell/module/azurerm.resources/new-azurermpolicydefinition?view=azurermps-6.13.0)
  - [New-AzureRmPolicyAssignment](https://docs.microsoft.com/en-us/powershell/module/azurerm.resources/new-azurermpolicyassignment?view=azurermps-6.13.0)
		
### Data Plane Security ###

- Protecting storage account services
  - [Blobs, files, queues, tables](https://docs.microsoft.com/en-us/azure/storage/common/storage-security-guide#data-plane-security)
- Shared access signatures ([SAS](https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1))
  - Time-limited URIs
  - CRUD
- [Stored Access Policies](https://azure.microsoft.com/en-us/updates/manage-stored-access-policies-for-storage-accounts-from-within-the-azure-portal/)
  - Standardised, [reusable SAS rules](https://docs.microsoft.com/en-us/rest/api/storageservices/constructing-a-service-sas)

### Encryption in Transit ###

- Enable [HTTPS](https://support.google.com/webmasters/answer/6073543?hl=en)
  - [App Services](https://docs.microsoft.com/en-us/azure/app-service/) apps
  - [IaaS](https://azure.microsoft.com/en-us/overview/what-is-iaas/) web apps
  - [Blob service URIs](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-manage-access-to-resources)
- [SMB 3.0 encryption](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn551363(v=ws.11)#BKMK_SMBEncryption) in [Azure File Share service](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-introduction)
- Client-side [encryption](https://docs.microsoft.com/en-us/azure/security/security-azure-encryption-overview)
  - Protects user app data before it's uploaded to Azure
  - Accessed through the [Azure SDK libraries](https://azure.microsoft.com/en-us/downloads/)

### Encryption at Rest ###

- Storage Service Encryption ([SSE](https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption))
  - On-the-fly storage account encryption
- [Azure Disk Encryption](https://docs.microsoft.com/en-us/azure/security/azure-security-disk-encryption-faq)
  - [BitLocker](https://blogs.technet.microsoft.com/showmewindows/2018/01/18/how-to-enable-bitlocker-and-escrow-the-keys-to-azure-ad-when-using-autopilot-for-standard-users/) for Windows Server VM OS and data disks
  - [DM-Crypt for Linux VM disks](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/encrypt-disks)

### Storage Analytics ###

- Storage account logging and metrics data
  - [Storage Analytics metrics](https://docs.microsoft.com/en-us/rest/api/storageservices/about-storage-analytics-metrics) are available for the Blob, Queue, Table, and File services
  - [Storage Analytics logging](https://docs.microsoft.com/en-us/rest/api/storageservices/about-storage-analytics-logging) is available for the Blob, Queue, and Table services. However, premium storage account is not supported
  - [Storage accounts with a replication](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy) type of Zone-Redundant Storage (ZRS) do not have the metrics or logging capability enabled at this time
- Requests
  - Successful and failed access
  - SAS requests
  - Request for analytics data
- Accessible (as always) through REST API

### Firewall ###

- [NSG](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview)
  - Can be attached to [vNIC](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-network-interface-vm) or [vNet](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview) subnet
- [Software Firewall](https://azuremarketplace.microsoft.com/en-us/marketplace/?term=Firewall)
  - May or may not be necessary
  - More restrictive rules than NSG (cant overwrite NGS rules)
- [Virtual Appliances](https://azure.microsoft.com/en-us/solutions/network-appliances/)
  - VM images from leading [third-party OEM](https://azure.microsoft.com/en-us/updates/azure-marketplace-third-party-reseller-services-now-use-azure-monetary-commitment/)s

### Antimalware ###

- VM Extensions
  - [Microsoft Monitoring Agent](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/agents-overview)
  - Third-party partners
- Antimalware Assessment
  - Part of [Security & Compliance management solution](https://docs.microsoft.com/en-us/azure/security/security-management-and-monitoring-overview)
  - [Azure security center](https://docs.microsoft.com/en-us/azure/security-center/security-center-partner-integration)
			Azure Security Center makes it easy to enable integrated third-party partner security solutions. Benefits include:
    - Simplified deployment: Security Center offers streamlined provisioning of integrated partner solutions. For solutions like antimalware and vulnerability assessment, Security Center can provision the needed agent on your virtual machines. For firewall appliances, Security Center can take care of much of the network configuration required.
    - Integrated detections: Security events from partner solutions are automatically collected, aggregated, and displayed as part of Security Center alerts and incidents. These events also are correlated with detections from other sources to provide advanced threat detection capabilities.
    - Unified health monitoring and management: Integrated health events provide monitoring of all partner solutions at a glance. Basic management is available, with easy access to advanced setup using the partner solution.
    - Currently, integrated security solutions include:
      - Endpoint protection such as Trend Micro, Symantec, System Center Endpoint Protection ([SCEP](https://azure.microsoft.com/en-us/resources/videos/microsoft-endpoint-protection-for-azure/)), and Windows Defender
      - Web application firewalls ([WAF](https://docs.microsoft.com/en-us/azure/application-gateway/waf-overview)) such as Azure Application Gateway, Barracuda, F5, Fortinet, and Imperva
      - Next-generation firewalls ([NGFW](https://docs.microsoft.com/en-us/azure/security-center/security-center-add-next-generation-firewall)) such as Barracuda, Check Point, Cisco, Fortinet, and Palo Alto Networks
      - Vulnerability assessment such as Qualys
- [Log analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/log-query-overview)

### Azure Security Center ###

[Ref](https://docs.microsoft.com/en-us/azure/security-center/security-center-intro)

Provides:
- Unified security management
- [Advanced threat protection](https://docs.microsoft.com/en-us/azure-advanced-threat-protection/atp-architecture)
  - Machine learning and behavioral analytics
- [Protection for hybrid cloud workloads](https://mva.microsoft.com/en-us/training-courses/hybrid-cloud-workload-protection-with-azure-security-center-18173)
  - Onboard and protect Azure and on-premises resources

It monitors:
- Windows Server and Linux VMs
  - In Azure and on-premises
- vNets
- [Azure SQL](https://azure.microsoft.com/en-us/services/sql-database/)
- Azure storage accounts
- Azure web apps in [ASE](https://docs.microsoft.com/en-us/azure/app-service/environment/intro)
- Partner solutions ([WAF](https://azure.microsoft.com/en-us/blog/azure-web-application-firewall-waf-generally-available/)s)

Has kind of alerts:
- Unencrypted disks
- Missing or out-of-date antimalware
- Attacks:
  - Brute force attacks against VMs
  - Alerts from antimalware/firewall software
  - Compromised VMs communicating with known malicious IP addresses
  - [SQL injections](https://www.owasp.org/index.php/SQL_Injection) against Azure SQL and IaaS SQL Server databases

Notes:
- ASC provides 30-days trial period.
- For monitoring it uses Microsoft Monitoring Agent available for Windows and Linux.
- It stores its data in a traditional Azure storage account.
- Forced tunneling requires selected Azure VMs to access the Internet through the on-premises network.
- Azure uses Dm-Crypt to encrypt Linux VM OS and data disks.

### ASC policy component ###

[Ref](https://docs.microsoft.com/en-us/azure/security-center/tutorial-security-policy)

Consists of:
- Pricing tier
- [Webhooks](https://azure.microsoft.com/en-gb/resources/videos/introduction-to-webhooks-for-azure-alerts/)
- [Prevention policy](https://docs.microsoft.com/en-us/azure/governance/policy/)

### Azure activity log ###

- Formerly [known](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/activity-logs-overview) as “audit logs”  or “operational logs”
- Separate and distinct from [diagnostic logs](https://docs.microsoft.com/en-us/azure/cdn/cdn-azure-diagnostic-logs)
- Report control-plane events on your subscription
- Great flexibility in query, report and export

** set up security center installs Microsoft Monitoring Agent to the VMs
 
### Patch Management for Azure VMs ###

- WSUS ([Windows Server Update Services](https://docs.microsoft.com/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus))
  - Local network
  - Virtual network
- [System Center](https://comparisons.financesonline.com/microsoft-azure-vs-microsoft-system-center)
  - Local network
  - Virtual network
- [Update Management Solution](https://docs.microsoft.com/en-us/azure/automation/automation-update-management)
  - Part of Azure Automation service
  - Manage updates for Windows server and Linux endpoint

## Monitoring ##

### Three monitoring tiers ###

- [Resource health](https://docs.microsoft.com/en-us/azure/service-health/resource-health-overview)
- [Monitor Center](https://docs.microsoft.com/en-us/azure/azure-monitor/overview)
- [Log Analytics and Operations Management suite (OMS)](https://azure.microsoft.com/es-es/blog/new-ways-to-enable-log-analytics-oms-on-azure-vms/)

### Ways to check Azure service status ###

- [Twitter](https://twitter.com/azurestatus)
- [Azure site](https://azure.microsoft.com/en-us/status/)
- [Service health on the Azure portal](https://azure.microsoft.com/en-us/features/service-health/)

### Things to Keep in Mind Regarding Azure VM Monitoring ###

- You're free to use native tools ([PerfMon](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/perfmon), [ps](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-6))
- With hybrid cloud, you can use [System Center](https://www.microsoft.com/fi-fi/cloud-platform/system-center)
- Take Azure into account when evaluating [monitor solution](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/solutions)
- [OMS](https://social.technet.microsoft.com/wiki/contents/articles/51206.microsoft-operations-management-suite-oms-a-beginner-s-guide.aspx) (operation management suite) is a tightly integrated solution
- Learn about [webhooks](https://docs.microsoft.com/en-us/azure/automation/automation-webhooks), [REST](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/rest-api-walkthrough), and [SQL](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/azure-sql)
- Consider streaming data via [Event Hub](https://azure.microsoft.com/en-us/services/event-hubs/)

** Log analytics sets inside an OMS workspace which has a free tier option

### Tools ###

#### Infrastructure provides ####

- [Application logs and metrics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-collection)
- [Diagnostic logs](https://docs.microsoft.com/en-us/azure/cdn/cdn-azure-diagnostic-logs)
- [Metrics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/metrics-charts)
- [Activity log](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/activity-logs-overview)

#### Analysing tools ####

- Visualize
  - [Graphics](https://docs.microsoft.com/en-us/azure/azure-monitor/visualizations)
  - [Portal views](https://docs.microsoft.com/en-us/azure/azure-monitor/learn/tutorial-viewdata)
  - [Dashboards](https://docs.microsoft.com/en-us/azure/azure-monitor/learn/tutorial-app-dashboards)
  - [Charts](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/charts)
- Archive
  - [Store in blob storage](https://azure.microsoft.com/en-us/services/storage/archive/)
  - [Audit trail](https://docs.microsoft.com/en-us/azure/security/azure-log-audit)
  - [Security analysis](https://docs.microsoft.com/en-us/azure/security-center/security-center-vulnerability-assessment-recommendations)
- Query
  - [REST API](https://docs.microsoft.com/en-us/rest/api/azure/)
  - [CLI](https://docs.microsoft.com/en-us/cli/azure/)
  - [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-6)
- Route
  - [Streaming](https://docs.microsoft.com/en-us/azure/iot-hub/tutorial-routing)
  - [Notification service](https://docs.microsoft.com/en-us/azure/notification-hubs/)
- Automate
  - [Webhooks](https://azure.microsoft.com/en-us/resources/videos/introduction-to-webhooks-for-azure-alerts/)
  - [Autoscale](https://azure.microsoft.com/en-us/features/autoscale/)
  - [Azure automation](https://azure.microsoft.com/en-us/services/automation/)
  - [Azure runbooks](https://docs.microsoft.com/en-us/azure/automation/start-runbooks)
		

### Monitoring - A layer Approach ###

- Resource level
  - Internal tools
  - [Metrics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/metrics-charts), [alert rules](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-metric)
- Resource group level
  - Monitor blade
- Enterprise level
  - [Hybrid nodes](https://www.pluralsight.com/courses/microsoft-azure-hybrid-cloud-networks-monitoring)
  - [Log analytics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/log-faq)
  - [Azure automation](https://azure.microsoft.com/en-us/services/automation/)

*Telemetry* - is an automated communications process by which measurements and other data are collected at remote or inaccessible points and transmitted to receiving equipment for monitoring.

### Monitoring and Diagnostics Pipeline ###

<img src="https://docs.microsoft.com/en-us/azure/architecture/best-practices/images/monitoring/pipeline.png"/>

### Azure Monitor Components ###

- [Activity log](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-audit)
  - On a Resource Group scale
- [Metrics](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/metrics-charts)
  - Plot data points to a custom, sharable dashboard
- [Diagnostic logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-overview)
  - Aggregated data can be analyzed with Power BI
- [Alerts](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-overview)
  - Get notified when metrics exceed threshold values
  - Automatic remediation ([Azure automation runbook, webhook](https://docs.microsoft.com/en-us/azure/automation/automation-webhooks))

### Azure diagnostics data ###

- [Event tracing](https://docs.microsoft.com/en-us/windows/desktop/etw/event-tracing-portal)
  - Configured by app developers
- [Performance counters](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-sources-performance-counters)
  - The 4 traditional subsystems
- Event logs
  - [ETW](https://docs.microsoft.com/en-us/dotnet/framework/wcf/samples/etw-tracing)
- Application logs
  - Configured by app developers
- [Azure diagnostics logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-overview)
  - Table and/or blob storage

### Azure resource log ###

- [Activity log](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-audit) (audit log)
  - Records operational details
  - "Who did what, and when" in Azure
- [Diagnostic log](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-overview)
  - Performance counters
  - Event logs (system, application, security)
  - IIS logs
  - Crash dump data
  - Custom error log

### Monitoring - Questions of scale and intelligence ###

- Log flood
  - So many data sources
  - How to quickly extract value?
- Predictive analytics
  - How to know what to look for?
- Automation
  - Immediate remediation

### Log Analytics ###

#### Provides ####

- Monitoring
- Analysis
- Alerting
- Remediation

#### Data sources ####

- [Counters](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-sources-performance-counters)
- [Logs](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-overview)
- [App Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
- [Agent devices](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/agents-overview) (cloud and on-prem)
- [SCOM management groups](https://docs.microsoft.com/en-us/system-center/scom/manage-create-manage-groups)

[Log Analytics query syntax](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/query-language)

#### The need for an alerting solution ####

- Avoiding surprises
- Email, SMS
- [Third-party security and event management](https://docs.microsoft.com/en-us/azure/security/security-azure-log-integration-overview) (SIEM)
- Azure integration is eminently possible

*Webhook* - is a way for an app to provide other applications with real-time information. Also called a web callback or an HTTP push API. The payload is ordinarily JSON.

### What can you do with Webhooks ###

- Third-party integrations
  - [PagerDuty](https://www.pagerduty.com), [OpsGenie](https://www.opsgenie.com/), [VictorOps](https://victorops.com/), [Slack](https://slack.com/), [HipChat](https://www.atlassian.com/partnerships/slack), [Campfire](https://www.campfiretechnology.com/), etc.…
- Script execution
  - [Azure automation runbooks](https://docs.microsoft.com/en-us/azure/automation/automation-webhooks)
- SMS text
  - [Twilio API](https://www.twilio.com/docs/usage/api)
 
## Troubleshooting and support ##

### Azure VM troubleshooting checklist ###

- Reset
  - Admin credentials
  - [RDP configuration](https://docs.microsoft.com/en-us/azure/virtual-machines/troubleshooting/reset-rdp)
- Verify
  - [NSG rules](https://blogs.msdn.microsoft.com/mvpawardprogram/2018/05/08/troubleshoot-nsgs/)
- Review
  - [Console logs](https://docs.microsoft.com/en-us/azure/application-gateway/application-gateway-diagnostics)
- [Check VM resource health](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/vminsights-health)
- [Restart](https://docs.microsoft.com/en-us/azure/virtual-machines/troubleshooting/understand-vm-reboot)
- [Redeploy](https://docs.microsoft.com/en-us/azure/virtual-machines/troubleshooting/redeploy-to-new-node-linux)
  - Migrates VM to a new hardware host
  - VM will be down during the migration
- [Delete](https://docs.microsoft.com/en-us/powershell/module/servicemanagement/azure/remove-azurevm)
  - Only the config, not the NIC or storage
  - Attack disk to working VM
  - Tweak registry
  - Recreate

## Cost management ##

### How to buy azure services ###

- [Pay-as-You-Go](https://azure.microsoft.com/en-us/offers/pay-as-you-go/)
  - No minimum spend
  - Pay for what you use
  - Cancel anytime
- [Enterprise agreement](https://azure.microsoft.com/en-us/pricing/purchase-options/enterprise-agreement/) (EA)
  - Advantage: forecasting
  - Azure enterprise portal
		

Trial is not automatically converted
Analyze resource usage
Set billing alerts
Consider spending limits


### Azure SLA ###

*Service-Level Agreement (SLA)* - is an official commitment between a service provider and a customer.

### Azure support plans ###

- [Basic](https://azure.microsoft.com/en-us/support/plans/)
  - Free
- [Developer](https://azure.microsoft.com/en-us/support/plans/developer/)
  - 29$/month
- [Standard](https://azure.microsoft.com/en-us/support/plans/standard/)
  - 300$/month
- [Professional direct](https://azure.microsoft.com/en-us/support/plans/prodirect/)
  - 1,000$/month
- [Premier](https://azure.microsoft.com/en-us/support/plans/premier/)
  - Contact Microsoft

## Managed disks ##

### Storage account limits ###

- [check](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits) for the actual data 
    - Number of storage account per subscription is 200
    - TB per storage account is 500 TB

### Value proposition ###

[video](https://azure.microsoft.com/en-us/resources/videos/ignite-2018-understanding-the-value-proposition-of-azure-key-vault/)

- Azure manages VHDs
- Node direct public access
- Disk-level RBAC

- Scaling that's free of storage account limitations
- VM scale set support

- Availability set storage isolation

### Managed disks facts ###

- LRS only
- Fixed sizes:
  - Standard: 32 Gb, 64 Gb, 128 Gb, 512 Gb, 1 TB
  - Premium: 128 Gb, 512 Gb, 1 TB
- Can create empty managed disk

## Help and support ##

### Azure support issue types ###

- Technical
- Quota
- Billing
