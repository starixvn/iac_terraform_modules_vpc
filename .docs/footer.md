## Usage

Sample usage of this module is as shown below. For detailed info, look at inputs and outputs.

### Step 1

In your main.tf, add the following code:
<!-- NOTE: The package-source and version x.x.x will be auto populated by the ci job. You do not need to change anything here. -->
```hcl

module "my_module_name" {
  source = "{{package-source}}"
  version = "x.x.x"
  
  context = {
    "cost_center": "b-0001"
    "project_code": "xyz"
    "region": "us-east-1"
    "env_name": "dev"
    "zone": "ez"
    "tier": "web"
  }

  additional_tags = {          
    "foo"        = "bar"    
  }
  
}

```

Note:
- **my_module_name** is the name of the module. You can use any name you want.

### Step 2

In your provider.tf, add the following code, if it doesn't exist already:

```hcl

terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.0"
    }
  }
}

provider "aws" {
  region = "ap-southeast-1"
}

```

### Step 3

Verify your settings using the following command:

``` bash
terraform init
terraform plan
```

### Step 4

Apply the changes

``` bash
terraform apply
```

### Note:

This repository serves as an example of how to document a Terraform module and automate it using Gitlab's CICD. To understand the full process and how it works, please refer to the accompanying article on Medium titled "Documenting Terraform Modules" found at the following link: Documenting Terraform Modules
https://medium.com/p/9e284d692d8/