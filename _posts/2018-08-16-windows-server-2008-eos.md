---
layout: post
title: Windows Server 2008 End of Support
subtitle: What to do if you're still running Windows Server 2008
image: /img/servers-in-rack.jpg
share-img: /img/servers-in-rack.jpg
tags: [windows server 2008, SQL server 2008, end of support, Microsoft Azure]
comments: true
---

<p>How sure are you that none of your customers are running Windows Server 2008? If you're the one who's still got Small Business Server 2011 knocking about, or that Windows Server 2008 box at the back of the server room, then this post is for you. <em>What to do if you're still running Windows Server 2008 (and a little bit about SQL Server, too!)</em>.</p>

<p>A lot has changed since February 27th, 2008, the day Windows Server 2008 became generally available. Back then, I was still managing a server cupboard with giant 5U servers, rejoicing at the installation of a shiny new Exchange 2003 server. Office 365, Azure, 'the cloud', none of these things existed in the mainstream. I was still in the world of on-premises infrastructure. So were many businesses from SMBs through to the largest enterprises.</p>

<p>Wind the clock forward to 2018 again. We're surrounded by cloud technologies. The thought of buying a physical server on which to install Exchange seems crazy. It's so simple to spin up an Office 365 tenant instead. Increasingly, we're turning our attention to advanced technologies like Artificial Intelligence, Machine Learning, to aid and enhance our productivity. Those old physical servers have long been virtualised. Many line-of-business applications have moved to a cloud delivery model, using Software-as-a-Service. Of course, many of those VMs are still running Windows Server 2008 or SQL 2008. It's what to do with those aging servers that is now very much an urgent question to answer.</p>

<p>By now, you'll hopefully have noticed that there are some important dates on the horizon. These will have an impact on you and your customers if you're still running either Windows Server 2008 or SQL Server 2008. I <a href="https://jamesbmarshall.com/2017/03/24/moving-small-business-server-to-microsoft-azure/">wrote about this last year</a> when looking at what to do with Small Business Server 2011:</p>

<ul><li><strong>2020-01-14</strong> - <a href="https://www.microsoft.com/en-us/cloud-platform/windows-server-2008">Windows Server 2008 end of support</a></li><li><strong>2019-07-09</strong> - <a href="https://www.microsoft.com/en-gb/sql-server/sql-server-2008">SQL Server 2008 end of support</a></li></ul>

<h2>What does 'end of support' mean?</h2>

<p>End of support means the end of regular security updates. This is bad news if you're still running either software. There may be vulnerabilities exposed in future which present a risk to you or your customers for which Microsoft will not automatically issue a patch. This leaves you and your customers exposed from a technology perspective. Potentially, you could end up in breach of contract if you work within frameworks or regulations which require the infrastructure you provide to be supported by the vendor.</p>

<h2>Get out of jail free!</h2>

<p>Now, I'm sure you're all being conscientious IT managers, service providers, CTOs, and this is not news to you. You did all your Windows Server and SQL Server migrations years ago, right? 😉 The truth is, life gets in the way. Other projects take priority. Whether it's budget, time, or frankly just interest, it's easy to let this have slipped. Happily, Microsoft has your back, to an extent. In a recent announcement, Microsoft <a href="https://www.microsoft.com/en-gb/cloud-platform/windows-sql-server-2008">unveiled a few options to help</a> those of you in need of a "get out of jail free" card.</p>

<ol><li><strong>Migrate the existing Windows Server 2008 servers to Azure and get three years of Extended Security Updates at no additional charge.</strong> This buys you a lot of extra time to decide what to do. You can also use your existing Windows licenses, and bring the Azure Virtual Machine costs down by up to 80%. (If you use the Azure Hybrid Use Benefit and Reserved Instances.)</li><li><strong>Upgrade the servers to Windows Server 2016 and buy up to three years of Extended Security Updates.</strong> You can only the servers you need while you upgrade.</li></ol>

<p>Obviously, modernising the workload is the ideal outcome. It's not sustainable to keep running an aging operating system (I'm looking at you, Windows XP). Having three years of breathing space is undoubtedly useful in giving you time to complete this work.</p>

<p>On the SQL Server 2008 side, there are similar options.</p>

<ol><li><strong>Re-host SQL Server 2008 and 2008 R2 with no application code changes in Azure Virtual Machines to unlock three years of Extended Security Updates at no additional charge</strong>. Again, bring the costs down by up to 55% using migrations to Azure SQL Database with Azure Hybrid Use Benefit.</li><li><strong>Upgrade to SQL Server 2017 and buy up to three years of Extended Security Updates.</strong> You can cover only the workloads you need while you upgrade.</li></ol>

<h2>First steps onto Azure and a recurring revenue business</h2>

<p>For many Microsoft Partners, maybe even you, these options represent the first opportunity for your customers to move to Azure. It's the ideal way to demonstrate how the public cloud can seamlessly take responsibility for powering a business. Moving a VM from on-premises to Azure is a simple process. It can form the basis of future work, such as providing identity services through Azure Active Directory, backup services, file storage and archiving, web hosting, app hosting, dev/test and all sorts of other workloads.</p>

<p>The beauty of doing it this way, as well as the immediate benefit of three years Extended Security Updates, is that you begin to build a stream of recurring revenue every month through the consumption of Azure services. This has a positive impact&nbsp;on you as a Microsoft Partner. You can begin to earn rebates and incentives and work towards important recognition like a Silver or Gold <a href="https://partner.microsoft.com/en-gb/membership/cloud-platform-competency">Cloud Platform competency</a>.</p>

<h2>The infamous 'rule of 78'</h2>

<p>Once you begin to feel comfortable moving those 'veteran' Windows Server 2008 and SQL Server 2008 workloads to the public cloud, you can start to get a taste for how to build a very successful monthly-recurring-revenue (MRR) business. By understanding the old '<a href="https://www.intelliverse.com/blog/what-is-the-rule-of-78-and-how-does-it-apply-to-sales/">rule of 78</a>', it becomes clear that by adding new customers to your Azure business - some by moving these older workloads, some by offering packaged services, and so on - every month, you can generate a big revenue stream relatively quickly.</p>

<p>Take the example of adding one new customer spending $400 of Azure per month. This could consist of a few virtual machines, some backup, maybe some site recovery, some storage, any number of very simple and easily understood workloads. By applying the 'rule of 78', this equates to the addition of $31,200 during the&nbsp;year, and by month 12, $4,800 per month (or $57,600 annualised run-rate)! From here, you have a perfect platform through which to build a strong relationship with your customers. Upon which you can add more services, incrementally adding business value to the customer and increasing your MRR on Azure.</p>

<p>Factor in your own IP and services margins on top, and suddenly you've transformed your customers and built yourself a lucrative, predictable and successful Microsoft cloud practice. If you want to learn more about cloud profitability or how to build Microsoft cloud practices, I'd strongly encourage you to check out the <a href="https://partner.microsoft.com/en-cy/campaigns/cloud-practice-playbooks">cloud practice playbooks</a>.</p>

<h2>What to do if you're still running Windows Server 2008</h2>

<p>If you've read this far, it should be obvious: get your customers three years of Extended Support Updates. Start building your super amazing Azure business!</p>