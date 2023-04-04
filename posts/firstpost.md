---
title: Creating your Website and Hosting it on AWS
description: A walkthrough of how I deployed this website.
date: 2023-03-31
tags:
  - AWS
  - CI/CD
layout: layouts/post.njk
---
Welcome to my first blog post where I share how I created my first website and deployed it using AWS! I have been wanting to make a website for a while but I was overwhelmed with options and it was lower on my priority list. But then while studying for the AWS Solutions Architect Certification exam I came upon a lecture on how to use Amazon S3 to host static websites. This then became the perfect project to learn more about AWS while also doing something creative.

<br>I knew how I wanted to host my website but then I wasnt sure where to start with the code. I knew some CSS and HTML but I didnt want to start completely from scratch. After doing some research I came upon Eleventy and saw some really cool websites created using this static site generator and I was sold! Elventy also provided a basic template that allowed me to focus on first just getting my website pipeline going and then eventually I would slowly adapt the template to make it my own.

<br>Here is an overview of the applications I used:
* <strong>Eleventy</strong>: The static site generator I used to build my website.
* <strong>Github</strong>: In addition to storing the website code, I also created a development pipeline using Github Actions.
* <strong>Google Domains</strong>: A domain name registrar operated by Google. This is where I registered the domain name for the website (eg. migipatel.dev). I used this instead of using Amazons Route 53 because I wanted a website with the .dev ending which they did not offer.
* <strong>Amazon Web Services (AWS)</strong>: Used to host the website.


## Fundamentals
Here I will review some information and definitions relevent to our process to deploy our website.


<br>What is a <strong>static website</strong>?<br>
A website with fixed content.

<br>What is a <strong>static site generator?</strong><br>
A static site generator will take in the code we write and process it into a folder with the resultant pages. The static site generator generates the static web pages.

<br>What is a <strong>domain name</strong>?<br>
The domain name is the website address, for example Google.com. However, computers will interpret the domain name through a series of numbers called the IP address. To translate the text-based domanin name to the IP address the DNS (Domain Name System) is used. A good reference for understanding this concept is this AWS video: [What is DNS? - Introduction to Domain Name System](https://www.youtube.com/watch?time_continue=5&v=e2xLV7pCOLI&source_ve_path=MjM4NTE&feature=emb_title) . 

## Setting up the Development Environment
I prefer developing in the Linux environment so I used Ubuntu 18.04 on WSL 2 (Windows Subsystem for Linux). WSL allows developers to run a Linux environment easily on a windows machine. The installation instructions can be found online ([Install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)) but I have also included them here:
1. Open a command prompt
2. Install WSL
```diff-js
wsl --install
```
3. Install whatever Linux distribution you want using: wsl --install -d
* For Ubuntu 18.04
```diff-js
wsl --install -d Ubuntu-18.04
```
* To see a list of distributions: wsl --list --online
4. Type wsl into the command prompt and this will open a wsl session with the set distribution

## Creating the Website using Eleventy 
Eleventy provides a helpful template that I used to initially develop my website. You dont have to use this but if you want to here are the instructions:
1. Go to https://github.com/11ty/eleventy-base-blog and click "Use this template" and create a repo under your account with this repo as the base name and name it.
2. Open command prompt and enter a wsl session.
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

## Now you have your site, we can move on to hosting!
You will need an AWS account for this part. You can sign up for the free tier here [AWS Free Tier](https://aws.amazon.com/free).

### Part 1: Register your domain name with Google Domain
In this step feel free to research different platforms to register your domain name. I chose Google Domains because I wanted a .dev website which was not available through AWS. So you can search for free domain names and buy one from [Google Domains](https://www.domains.google). It will warn you about the SSL certificate but just ignore that for now because we will handle it later through AWS.

### Part 2: Create a bucket on Amazon S3 (FURTHER INSTRUCTIONS IN PROGRESS)
Now you will need to enter your AWS account console and set up an S3 Bucket.
1. Log into you AWS account
2. Search for S3
3. Start creating the S3 bucket by selecting <strong>Create Bucket</strong>.
<br><img src = "/img/createWebsitePost/createS3Bucket.png" /> <br>
4. Name your bucket the name of your website.
<br><img src = "/img/createWebsitePost/nameBucket.png" /> <br>
<img src = "/img/createWebsitePost/editStaticHostingWebsite.png" /> <br>
<img src = "/img/createWebsitePost/editBucketPolicy.png" /> <br>

### Part 3: Setting up the SSL Certificate
Go back to the AWS console and search for Certificate Manager. Click <strong> Request a Certificate </strong>

### Part 4: Set up AWS Cloudfront 
Now that we have the certificate, we can use AWS Cloudfront to tell our site to use that certificate.

### Part 5: Create a Code Pipeline

### Review of Billing







