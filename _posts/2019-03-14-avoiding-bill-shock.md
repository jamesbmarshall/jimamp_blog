---
layout: post
title: Avoiding Azure Bill Shock
subtitle: Tools for your Azure management kit bag
summary: Tools for your Azure management kit bag
share-img: /img/shock_twitter_card.jpg
image: /img/shock.jpg
tags: [CSP, cloud distribution, indirect CSP provider, 2-tier CSP, Cloud Solutions Provider, Microsoft Azure, Azure Governance, bill shock, Azure Advisor, RBAC, Azure Policy, cost management]
comments: true
---
One of the great advantages of a service like Microsoft Azure is its scale. I don't have to worry about ordering a physical server, setting it up, and living in fear that the cleaner might [accidentally unplug it so they can use their vacuum cleaner](https://www.theverge.com/2017/6/2/15728276/british-airways-power-supply-turned-off-reports "British Airways flight disruption was caused by someone unplugging the power"). At the click of a button I can provision anything Azure has to offer and it'll be ready in seconds. Of course, with great power comes great responsibility. Just because I can, doesn't mean I should... Yet, some of the feedback I hear from Microsoft resellers is that their customers are sometimes caught out by 'bill shock' as they use more Azure compute resources than they'd expected. Sometimes it's not the customer - it's not unheard of for a partner engineer to spin up more than their fair share of resources in the name of training, research or development! 

In this post, we'll look at a few of the Azure features and services you can use to banish bill shock to the history books and improve your Azure-powered solutions offerings.

### Azure Governance

Announced in [September 2018 by Jeremy Winter, Partner Director, Azure Management](https://azure.microsoft.com/en-gb/blog/get-speed-and-control-with-new-free-azure-governance-services/ "Get speed and control with new free Azure governance services"), [Azure Governance](https://docs.microsoft.com/en-us/azure/governance/ "Azure Governance") is a set of services designed to give you the speed and control over Azure that you need to be successful.

{% include youtubeplayer.html id="MhGbKjlmuRs" %}

Including Management Groups, Resource Graph, Policy and Blueprints, anyone working with Azure should be using the Governance services to apply the necessary protections to a subscription to avoid unexpected resource provision.

#### Azure Policy ####

Azure Policy is particularly useful when it comes to controlling what can be used within a subscription. Unlike RBAC, which we'll cover later, Policy allows you to define rules that can do useful things such as:

- **Defining a list of 'not allowed' resource types.** This is useful if you're working on a very specific project for your customer. For example, you may be doing some initial virtual machine migrations. You may want to disallow the creation of other types of resources on that subscription so that individuals cannot accidentally spin up other solutions that haven't been defined in the scope of your project.

- **Allowed Virtual Machine SKUs.** Simlar to the 'not allowed' list, defining a list of allowed VM SKUs gives back some flexibility to the administrator, but in a way that means you can provide consistent support. For example, you may decide that you will only work with a handful of VM types such as the B, D and A series. All others would be disallowed, avoiding the scenario where someone spins up the rather chunky [memory optimised M series](https://azure.microsoft.com/en-gb/pricing/details/virtual-machines/series/ "Virtual Machine series") by mistake.

- **Allowed Locations.** Some customers have strict requirements about where their Azure resources sit. By defining a policy to only allow certain locations, such as in the UK, you can be assured that resources can't spring up in regions you haven't sanctioned.

Azure Policy can do a tremendous amount when it comes to applying structure that helps you provide a managed service. The examples above are just a flavour of what's possible. There are also no charges for Azure Policy, making it a no-brainer for every Microsoft Partner to be using with their Azure solutions.

### Role-Based Access Control (RBAC) ###

[RBAC](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview "What is role-based access control (RBAC) for Azure resources?") allows you to control who has access to Azure resources and what they can do with them. A good thing to do when working with Azure is to define roles and responsibilities both in your Partner business and with the customer, and define good RBAC structure to reflect them. Giving everyone access to everything, everywhere, is a recipe for disaster. 

When planning, it's useful to keep the idea of 'least privilege' in mind. A well defined RBAC strategy in conjunction with a robust Azure Policy will take you a long way towards avoiding bill shock as you'll have successfully reduced the number of people who can create or delete resources within a subscription, and limited what they can work with to just the right resources to achieve the solution design.

### Azure Advisor ###

A hidden gem of a service, [Azure Advisor](https://docs.microsoft.com/en-us/azure/advisor/advisor-overview "Azure Advisor Overview") should be part of every Azure deployment in my opinion - it's just too useful to leave out. Described as a "personalised cloud consultant" it gives you insights and recommendations which can not only help with performance and security, but in the spirit of avoiding bill shock, also [cost effectivness](https://docs.microsoft.com/en-us/azure/advisor/advisor-cost-recommendations) advice!

In an ideal world, you'd have done the analysis to right-size a VM instance prior to provisioning it. In the real world, that's not always possible. Running Azure Advisor as part of a deployment will give you the insights as to whether you could benefit from resizing or shutting down VMs, eliminating idle resources and more. My top tip would be to run your solution 'as is' for a while before using Azure Advisor to establish whether any efficiences can be realised and _then_ applying any Reserved Instances.

This avoids the situation where an RI is purchased up front but has to be terminated due to it being for the wrong type or size of VM. RI's carry a penalty for early termination so it's best to get the Azure Advisor insight first and then lock in with an RI once you're happy. 

### Your Indirect CSP Provider ###

As well as the tools I've covered in this post, your Indirect CSP Provider should be able to support you with cost management tools, insights and analytics which can help you predict bills based on subscription burn rate, and historic useage. They should also be able to help you get up to speed on the best way to apply the Azure Governance tools, RBAC and Azure Advisor to support the development of your first solutions or projects on Azure.

If they can't, now might be the perfect time to take a look at my mini-series on the types of [questions you might want to ask of your Microsoft Cloud Distributor](http://localhost:4000/2019/01/27/choosing-a-cloud-disti/).

### A New Solution Opportunity ###

There's a school of thought which says that incorporating the use of these tools and others like [Azure Security Center](https://azure.microsoft.com/en-gb/services/security-center/) should be baked in as part of the solutions you build, or the projects you deliver on Azure. That said, building an 'optimisation-' or 'monitoring-as-a-service' solution and turning it into a billable offering could be attractive to some partners. Particularly if you're inheriting somebody else's environment. Being able to go to market with a strong message around driving efficiency, cost effectiveness, and security can be a powerful differentiator from other Partners who just use Azure as a basic IaaS platform.