**# The-AWS-Devops-Practical-Project.**

**Terraform** is a fairly new project that was started in 2015.

Terraform is powerful and one of the most used tools which allow management infrastructure as code. It allows developers to do a lot of things and does not restrict them from doing things in ways that will be hard to support or integrate with.

Some information described in this book may not seem like the best practices. I know this, and to help readers to separate what are established best practices and what is just another opinionated way of doing things, I sometimes use hints to provide some context and icons to specify the level of maturity on each subsection related to best practices.

A few years later it has been updated with more actual best practices available with Terraform 1.0. Eventually, this book should contain most of the indisputable best practices and recommendations for Terraform users.

**The AWS Modules with Meta Configuration's:**


terraform {
  source = "${path_relative_)
}

include {
  path = find_in_parent_folders()
}

locals {
  branch_protections = {
    "terraform-aws-*/master" = {
      required_status_checks = {
        contexts = [
          "WIP"
        ]
      }
    }

    "terraform-aws-meta/master" = {
      allows_force_pushes = true # just for local development
      required_status_checks = {
        contexts = [
          "WIP",
        ]
      }
    }
  }
}

inputs = {

  repositories = {

    terraform-aws-acm = {
      description  = "Terraform module which creates and validates ACM certificate 🇺🇦"
     
      topics       = ["aws", "aws-acm", "aws-acm-certificate", "terraform-module"]
    }

    terraform-aws-alb = {
      description  = "Terraform module to create an AWS Application/Network Load Balancer (ALB/NLB) and associated resources 🇺🇦"
     
      topics       = ["aws", "application-load-balancer", "alb", "network-load-balancer", "nlb", "terraform-module"]
    }

    terraform-aws-apigateway-v2 = {
      description  = "Terraform module to create an AWS API Gateway v2 (HTTP/WebSocket) 🇺🇦"
     
      topics       = ["aws", "aws-apigateway", "serverless", "terraform-serverless", "terraform-module"]
    }

    terraform-aws-appsync = {
      description  = "Terraform module to create AWS AppSync resources 🇺🇦"
     
      topics       = ["aws", "aws-appsync", "graphql", "appsync", "serverless", "terraform-serverless", "terraform-module"]
    }

    terraform-aws-atlantis = {
      description  = "Terraform configurations for running Atlantis on AWS Fargate. Github, Gitlab and BitBucket are supported 🇺🇦"
      
      topics       = ["aws", "atlantis", "aws-fargate", "terraform-module"]
    }

    terraform-aws-autoscaling = {
      description  = "Terraform module which creates Auto Scaling resources on AWS 🇺🇦"

      topics       = ["aws", "autoscaling-groups", "autoscaling", "aws-autoscaling", "terraform-module"]
    }
    
    
    
**Script's:**


#!/usr/bin/env bash

set -e # do exit on bad exit code

# Locate the directory in which this script is located
readonly SCRIPT_PATH="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

# This dir
readonly GITHUB_REPOS_DIR="${SCRIPT_PATH}/../github/repositories"


# All dirs including hidden (.github, for eg)
#dirs=($(find * -mindepth 1 -maxdepth 1 -type d -path "terraform-aws-modules/*" | sort))

dirs=(
terraform-aws-modules/.github
terraform-aws-modules/meta
terraform-aws-modules/terraform-aws-acm
terraform-aws-modules/terraform-aws-alb
terraform-aws-modules/terraform-aws-apigateway-v2
terraform-aws-modules/terraform-aws-appsync
terraform-aws-modules/terraform-aws-atlantis
terraform-aws-modules/terraform-aws-autoscaling
terraform-aws-modules/terraform-aws-cloudwatch
terraform-aws-modules/terraform-aws-customer-gateway
terraform-aws-modules/terraform-aws-dynamodb-table
terraform-aws-modules/terraform-aws-ebs-optimized
terraform-aws-modules/terraform-aws-ec2-instance
terraform-aws-modules/terraform-aws-ecs
terraform-aws-modules/terraform-aws-eks
terraform-aws-modules/terraform-aws-elb
terraform-aws-modules/terraform-aws-rds-aurora
terraform-aws-modules/terraform-aws-redshift
terraform-aws-modules/terraform-aws-s3-bucket
#terraform-aws-modules/terraform-aws-s3-object # archived (readonly)
terraform-aws-modules/terraform-aws-security-group
terraform-aws-modules/terraform-aws-sns
terraform-aws-modules/terraform-aws-sqs
terraform-aws-modules/terraform-aws-step-functions
terraform-aws-modules/terraform-aws-transit-gateway
terraform-aws-modules/terraform-aws-vpc
terraform-aws-modules/terraform-aws-vpn-gateway
)

**Terraform in Refactoring.**



//provider "aws" {

//}
//
//resource "random_pet" "this" {
//  length = 2
//}
//
//resource "aws_devicefarm_project" "this" {
//  name = random_pet.this.id
//}
//
//output "this_devicefarm_project_arn" {
//  value = aws_devicefarm_project.this.arn
//
}



