---
layout: post
title: How To Move Small Business Server to Microsoft Azure
tags: [Microsoft Azure, business cloud storage, cloud server for small business, cloud storage solutions, Digital Transformation, Microsoft Partner, Office 365]
comments: true
---

Remember 2010? In technology terms, 2010 was a century ago. Yet, plenty of small businesses around the world still run&nbsp;applications and servers from that era today. Microsoft's Small Business Server 2011 is just one example. 2010 also marks an important milestone in the development of the modern "cloud" we use today as it's the year Microsoft launched Windows Azure and Office 365.

It's fair to say that a lot has changed since 2010. We can now provision entirely reimagined productivity scenarios in seconds. We can give our customers access to their data, applications and&nbsp;<em>their customers</em> anywhere, anytime and on any device. We're very much in the middle of the "digital transformation" movement. The pace of change doesn't appear to be slowing down anytime soon either, with machine learning, artificial intelligence and chat&nbsp;bot technologies all promising to continue to redefine what it means to provide IT services both as a customer and as a partner.

Knowing where to start helping your customers on this journey can be difficult, but I'm sure you'd agree that leaving them where they are today, on rapidly ageing technology, does nobody any favours.
<h2>What is Small Business Server 2011?</h2>
It's worth taking a moment to remind ourselves what Small Business Server 2011 included:
<ul>
 	<li>Designed and priced for small businesses with up to 75 users, very much in the Small and Mid-Sized Business - <em>SMB</em> - space.</li>
</ul>
<ul>
 	<li>Includes <i>Windows Server 2008 R2</i>, <i>Exchange Server 2010</i>, <i>SharePoint Foundation 2010</i>, <i>SQL Server 2008 R2 Express</i>, <i>WSUS 3.0 with SP2</i>.</li>
</ul>
<ul>
 	<li>“Pre-cloud”. Designed for the on-premises world before the public cloud solutions we have today had matured.</li>
</ul>
Small Business Server 2011 offered customers a brilliant "business in a box" that gave them all the services they'd need to be a modern and productive business in a pre-cloud-first-mobile-first world. Unsurprisingly, it was hugely popular.
<h2>Why move from Small Business Server 2011?</h2>
Software has a shelf life. In a cloud world, software gets updated all the time. There are no major migrations or upgrades. Instead, patches and features are continuously integrated so that the end-users always have the latest functionality.

In an on-premises world, it's slightly different. Microsoft has a well-documented product lifecycle for its on-premises services and software. In terms of SBS 2011, the table below shows the lifecycle status for each of the component features:

| Product | Mainstream End | Extended End |
| :------ |:--- | :--- |
| Windows Server 2008 R2 SP1 | 13/01/2015 | 14/01/2020 |
| Exchange Server 2010 SP3 | 13/01/2015 | 14/01/2020 |
| SharePoint Foundation 2010 SP2 | 13/10/2015 | 13/10/2020 |
| SQL Server 2008 R2 SP3 | 08/07/2014 | 09/07/2019 |
| WSUS 3.0 SP2 | 10/07/2012 | 14/01/2020 |

<p style="text-align: left;">Note that this is assuming that each feature is fully patched to the latest service pack; &nbsp;this&nbsp;won't be the case for every customer. Even so, they're all out of mainstream support with the clock ticking for the end of extended support. 2020 might seem like the distant future but when you have several customers all requiring some kind of migration work it's amazing how quickly those deadlines will be on top of us.</p>
<p style="text-align: left;">Lifecycle isn't the only consideration. As trusted advisors and technology partners for small businesses, there's a value element. By allowing customers to continue to use Small Business Server 2011 without a plan to move to a modern cloud platform you could be considered to be ignoring a huge opportunity to add considerable value. You could help them to work anywhere, anytime. Transform their approach to security. Reduce their costs of running IT. From a business perspective, you also miss out on the benefits of building a valuable annuity stream and risk your long-standing customer relationships being usurped by a competitor who'll transform your customers before you get a chance.</p>

<h2 style="text-align: left;">You've got three options</h2>
In my view, there are three ways to respond to this opportunity:
<ol>
 	<li><strong>Do nothing.</strong> This would be bad. It ignores both the impending problem and the opportunity. It under serves your customers and discredits you as a partner.</li>
 	<li><strong>Do it yourself.&nbsp;</strong>All the tools are there, across Office 365 and Azure to be able to build an SBS equivalent service in the cloud. This takes time and effort, and a degree of risk. Understandably, many partners don't have the resource to take that risk and therefore end up back at option 1.</li>
 	<li><strong>Script and template.</strong> Automating and building repeatable IP is the sweet spot for partners. We'll explore further on in this post an example of some scripts you can use to take the pain out of moving customers to the cloud. Using them can reduce your time-to-value, can de-risk projects and crucially help you create a predictable, packaged set of offerings for your customers.</li>
</ol>
<h2>The SMB Solution Template</h2>
The SMB Solution Template was created by Microsoft in collaboration with Inovativ. It pulls together a simple user interface running a selection of PowerShell scripts and JSON templates to easily guide you through the process of provisioning a fully working Office 365 and/or Azure environment.

This freely available solution allows you to take some very basic customer information, select from a choice of pre-defined packaged options (which you have control over), and in just a few minutes have the scripts build the framework. Once they're done you're left in a position to be able to perform a content migration, finish any specific customisations for the customer and then deliver a completed project.

The solution was designed to be easy to use, and highly reusable but they aren't meant to be the end of the support you get. There are other resources to help:
<ul>
 	<li>SMB Cloud Enablement Guide: <a href="https://aka.ms/cloudenablementguide">https://aka.ms/cloudenablementguide</a></li>
</ul>
<ul>
 	<li>Follow the online learning materials on the UK Partner Upskill site: <a href="https://aka.ms/upskill">https://aka.ms/upskill</a></li>
</ul>
<ul>
 	<li>Azure Mentor Program: Access to pre-sales support. Work with your PSE or PCDM Microsoft contact for info.</li>
</ul>
<h2>Template Walkthrough</h2>
Hans Demeyer, one of my colleagues from Microsoft's Western Europe subsidiary has recorded a great 5-minute walkthrough of the solution:

{% include youtubeplayer.html id="Iw2HYlMo2r0" %}

<h2>Next Steps</h2>
Now that you've seen the template in action, it's time for you to grab it and try it out yourself. It's available from a couple of different sources:
<ul>
 	<li><a href="https://github.com/Inovativ/SMBblueprint-Docs">https://github.com/Inovativ/SMBblueprint-Docs</a> - GitHub repo.</li>
 	<li><a href="https://www.powershellgallery.com/packages/SMBBlueprint/8.1.0.2">https://www.powershellgallery.com/packages/SMBBlueprint/8.1.0.2</a> - PowerShell Gallery</li>
</ul>
You'll need to ensure that you have all the PowerShell modules installed to manage Office 365, SharePoint Online, Azure, etc. In addition, you'll need to ensure that you have the necessary subscription information and delegated administration rights in order to run the scripts successfully.

Once you have all of this in place, you're all set to start building your own packages. You may want to consider your own small, medium and large deployment offerings based on some standardised infrastructure and pricing. You can then go to market with a simple offer along the lines of "your entire small business in the cloud for £X per user, per month".

Customers appreciate a clear cost model that's predictable and offers them high value for money.&nbsp;From these starting points, you can cross-sell and upsell additional services and premium add-ons that enhance your value as a partner, and empower the customer to be more successful in how they use the technology available to them. This is particularly true as you look towards newer services like <a href="https://www.microsoft.com/en-us/dynamics365/first-look" target="_blank" rel="noopener">Dynamics 365</a>, and new features like <a href="https://products.office.com/en-us/business/scheduling-and-booking-app" target="_blank" rel="noopener">Microsoft Bookings</a>, <a href="https://staffhub.office.com/" target="_blank" rel="noopener">Staff Hub</a> and <a href="https://products.office.com/en-gb/microsoft-teams/group-chat-software" target="_blank" rel="noopener">Microsoft Teams</a>.

I'd really like to hear how you get on with these templates&nbsp;or any questions you may have, in the comments!