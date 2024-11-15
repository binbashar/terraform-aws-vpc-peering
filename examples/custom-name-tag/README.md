# Setting a Custom Name Tag for the Peering Connection

This is a basic configuration example, which creates a peering connection between VPCs in a single region within the same AWS account.

However, here we set a custom name tag for the peering connection using the `name` variable.

**Notice**: You need to declare both providers even with single region peering.

## Code Sample

```hcl
provider "aws" {
  region     = "eu-west-1"
}

module "single_account_single_region" {
  source = "../../"

  providers = {
    aws.this = aws
    aws.peer = aws
  }

  name = "prod-external"

  this_vpc_id = var.this_vpc_id
  peer_vpc_id = var.peer_vpc_id

  auto_accept_peering = true

  tags = {
    Environment = "Test"
  }
}
```

## Usage

Change the variables to fit your purposes and run:

```bash
terraform init
terraform plan
terraform apply
```
