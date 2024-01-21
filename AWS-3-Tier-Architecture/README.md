## AWS 3-Tier Architecture: Web, App, and RDS

Welcome to the AWS 3-Tier Architecture project within this repository! This architecture is designed to showcase a scalable and resilient application infrastructure on AWS, leveraging three tiers: Web, App, and RDS (PostgreSQL). The entire setup is carefully organized across public and private subnets, with the utilization of NAT Gateways for enhanced security and optimal connectivity.

### Architecture Overview:

#### VPC Setup:
Begin by creating a VPC with public and private subnets across two availability zones in the Virginia region. This foundational step establishes the network environment for the subsequent components.

#### Public and Private Subnets:
The architecture incorporates the use of public subnets for the Web tier, ensuring that these instances have direct internet access. The App tier and RDS (PostgreSQL) reside in private subnets, adding an extra layer of security by restricting direct access from the internet.

#### Multi-Availability Zone Deployment:
To enhance availability and fault tolerance, both the Web and App tiers are deployed across two availability zones in the Virginia region. This ensures that the application remains resilient even in the face of disruptions in a single availability zone.

#### NAT Gateways:
As part of the VPC setup, create NAT Gateways in each public subnet to enable secure outbound internet access for instances in the private subnets. This facilitates the App tier instances to fetch updates, access external APIs, and more, while maintaining a secure and controlled environment.

### Deployment Steps:

1. **Web Tier (Public Subnets):**
   - Launch EC2 instances in the public subnets to host the web applications.
   - Configure security groups to allow inbound traffic from the internet.

2. **App Tier (Private Subnets):**
   - Launch EC2 instances in the private subnets to host the application logic.
   - Configure security groups to allow inbound traffic only from the Web tier.

3. **RDS (PostgreSQL) Database:**
   - Deploy an RDS instance in the private subnets to host the PostgreSQL database.
   - Configure security groups to allow inbound traffic only from the App tier.

### Conclusion:

This 3-Tier Architecture project not only serves as a practical demonstration of best practices in AWS architecture but also provides a foundation for building scalable, secure, and highly available applications. Explore the documentation and deployment steps to gain insights into the setup and configurations, empowering you to design robust AWS architectures for your own projects.
