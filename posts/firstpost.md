---
title: Using AWS to Deploy your Website
description: A walkthrough of how I deployed this website.
date: 2023-03-31
tags:
  - AWS
  - CI/CD
layout: layouts/post.njk
---
Hello everyone, welcome to my first blog post! I am super excited to share how I made this website using AWS, Eleventy, and Google Domains.

## Fundamentals
What is a <strong>static website</strong>?
A website with fixed content

What is a domain name?
The domain name is the website address, for example Google.com. However, computers will interpret the domain name through a series of numbers called the IP address. To translate the text-based domanin name to the IP address the DNS (Domain Name System) is used. A good reference for understanding this concept is this AWS video: [What is DNS? - Introduction to Domain Name System](https://www.youtube.com/watch?time_continue=5&v=e2xLV7pCOLI&source_ve_path=MjM4NTE&feature=emb_title) . 

## Setting up the Development Environment
I prefer developing in the Ubuntu environment so I used Ubuntu 18.04 on WSL.

## Creating the Website using Eleventy 
Eleventy provides a helpful template that I used to initially develop my website. You dont have to use this but if you want to here are the instructions:
1. Go to https://github.com/11ty/eleventy-base-blog and click "Use this template" and create a repo under your account with this repo as the base name and name it.
2. Open command prompt and enter wsl:
```diff-js
wsl
```
3. Cd into the directory where you want to have your github repo with your website.
4. Clone the newly created repo into the current directory and cd into it 
5. Install npm
```diff-js
npm install
```
Now you can use the following commands:
* To run Eleventy: `npx @11ty/eleventy`
* To build and host locally: `npx @11ty/eleventy --serve`
* To build automatically when a template changes: `npx @11ty/eleventy --watch`
* Or in debug mode: `DEBUG=* npx @11ty/eleventy`

## Now you have your site, we can move onto hosting!
You will need to create an AWS account for this part. You can sign up for the free tier here https://aws.amazon.com/free.

### Part 1: Register a custom domain with Route 53
* For registering a new domain, see [register a new domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html#domain-register-procedure).
* For an existing domain, see [Making Amazon Route 53 the DNS service for an existing domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html).
* For moving a domain to another registrar, see [update nameservers when you want to use another DNS service](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html#domain-register-other-dns-service-procedure).

NOTE: only certain top-level domains (TLDs) can be used to register domains with AWS (the TLD is what follows after the final dot of the domain name, ex. .com and .net)

### Part 2: Create a bucket on Amazon S3
<img src = "/img/createWebsitePost/editStaticHostingWebsite.png" /> <br>
<img src = "/img/createWebsitePost/editBucketPolicy.png" /> <br>

### Part 3: Setting up the SSL Certificate
Go back to the AWS console and search for Certificate Manager. Click <strong> Request a Certificate </strong>

### Part 4: Set up AWS Cloudfront 
Now that we have the certificate, we can use AWS Cloudfront to tell our site to use that certificate.

### Part 5: Create a Code Pipeline

### Review of Billing







