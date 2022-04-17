# rustok_cloudformation
cloudformationStacks
WordPress runing on fargate ECS cluster.
Architecture with 3 layers: PUBLIC, APPLICATION AND DB LAYER.
Fargate contains persistent storage
The DB is an RDS mysql DB.
There is an application load balancer facing external traffic which is locate in the public subnets.
All is secure with a Network ACL and few security groups, all are modifiable to the requirements of the organization.
The Fargate is set to register all of their new IPs (public IP are disabled for fargate) to the target group of the application load balancer.
The traffic is handle with 3 different route table. One route table is for public subnets to let them face internet directly and through an internet gateway.
Two route tables are design to handle all internal traffic and get internet access through a NAT gateway, one in each AZ (we are handling only two AZ in only one region) separating the traffic per AZ.
