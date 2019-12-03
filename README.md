# tvm: Terraform Version Manager
A little bit like RVM, for Terraform.

I work with Terraform *a lot* and with many versions. I use [RVM](http://rvm.io/) for Ruby on Rails project and find its syntax to be drop-dead easy.

So I made this script -- in a hurry, I admit -- because I needed a fast way to switch between Terraform versions. It's far from perfect, but usable in its present state.

## How it works
It downloads versions of Terraform from Hashicorp's website into a `terraforms` directory. Then it symlinks the `terraform` command to the version you specify in `tvm use`. Subsequent calls to `tvm use` replace the symlink.

## Installation
* Clone the repo
* Add the repo's dir to your `PATH`
* If you are not on 64-bit Linux, edit `ARCH` to match your needs.

## Use
### Installing a particular Terraform version
```
$ tvm install 0.12.9
```

### Listing installed Terraform versions
```
$ tvm list
terraform-0.11.14
terraform-0.12.13
terraform-0.12.16
terraform-0.12.3
terraform-0.12.7
terraform-0.12.9
```

### Switching between installed Terraform versions
```
$ tvm use 0.11.14
now using /home/john/tvm/terraforms/terraform-0.11.14

$ terraform -v
Terraform v0.11.14

$ tvm use 0.12.13
now using /home/john/tvm/terraforms/terraform-0.12.13

$ terraform -v
Terraform v0.12.13
```

### Parse `required_version`
```
# assumes a file in the current directory contains a `required_version` [declaration](https://www.terraform.io/docs/configuration/terraform.html#specifying-a-required-terraform-version)
$ tvm use
found required_version of 0.12.13
now using /home/john/tvm/terraforms/terraform-0.12.13
```

