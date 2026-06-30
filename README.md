# terraform-aws-vpc
## Overview
This the Terraform module create an AWS VPC with a given Cidr block. It also crreates multiple subnets (Public and Provate),and for public subnes it sets up an IGW and appropriate route tables.

## Features

- Creates a VPC with a specified CIDR blocks
- Creates public and private subnets.
- Creates an internet gate way for public subnets
- Sets up route tables for public subnets

## Usage

...
module "vpc" {
  source = "./modules/vpc"
  vpc_config  = {
    cidr_block = "10.0.0.0/16"
    name        = "my-test-vpc"
  }
  subnet_config = {
    #key={cidr, az}
public_subnets = {
    cidr_block = "10.0.0.0/24"
    az = "ap-south-1a"
    public = true
}

private_subnet = {
    cidr_block = "10.0.1.0/24"
    az = "ap-south-1b"
}
  }
}
...
