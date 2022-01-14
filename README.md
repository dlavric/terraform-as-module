# Repository for learning Terraform

## This Repository will create a local module 

## Instructions

### Prerequisites

- [X] [Terraform](https://www.terraform.io/downloads)

## How to Use this Repo

- Clone this repository:
```shell
git clone git@github.com:dlavric/terraform-as-module.git
```

- Go to the directory where the repo is stored and make sure the `main.tf` file is there too:
```shell
cd terraform-as-module
```

- Initialize Terraform by running `terraform init` to download any external dependencies
```shell
terraform init

Initializing modules...

Initializing the backend...

Initializing provider plugins...
- Reusing previous version of hashicorp/random from the dependency lock file
- Using previously-installed hashicorp/random v3.1.0

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

- Apply the changes with `terraform apply`
```shell
terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # random_pet.var will be created
  + resource "random_pet" "var" {
      + id        = (known after apply)
      + length    = 1
      + separator = "-"
    }

Plan: 1 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + var = (known after apply)

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

random_pet.var: Creating...
random_pet.var: Creation complete after 0s [id=rooster]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Outputs:

var = "rooster"
```

- Destroy the instance b running `terraform destroy`
```shell
terraform destroy

random_pet.var: Refreshing state... [id=rooster]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # random_pet.var will be destroyed
  - resource "random_pet" "var" {
      - id        = "rooster" -> null
      - length    = 1 -> null
      - separator = "-" -> null
    }

Plan: 0 to add, 0 to change, 1 to destroy.

Changes to Outputs:
  - var = "rooster" -> null

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value: yes

random_pet.var: Destroying... [id=rooster]
random_pet.var: Destruction complete after 0s

Destroy complete! Resources: 1 destroyed.
```
