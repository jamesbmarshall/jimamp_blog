---
layout: post
title: How To Configure Regional Settings For All Users In Live@edu
tags: [education, Microsoft Live@edu, Microsoft Office 365, Exchange Online, Outlook Live, Powershell]
comments: true
---
When students and teachers&nbsp;first log in to their Live@edu&nbsp;accounts they are presented with a screen asking them to select their regional settings.&nbsp;They'll only see this screen once; however, many administrators do not want to give their students (and teachers!) the choice to pick the wrong locale!&nbsp;In fact, if they pick the wrong language it might make it practically impossible for them to use without getting some help from IT. Therefore, the question begs: how can I configure regional settings for all my users so that they don’t have to choose?

Happily, the solution is fairly simple. All you need is a few lines of PowerShell...

<h2><strong>Configure Regional Settings For All Users</strong></h2>

It is possible, through <a title="Connect to Exchange Online using remote PowerShell" href="http://technet.microsoft.com/en-GB/library/jj984289(v=exchg.150).aspx" target="_blank" rel="noopener">Windows PowerShell</a> to configure regional and language settings for individual mailboxes. It is also possible to apply this to every user. For example:

<h3><strong>To set an individual user to English (UK), and GMT Standard Time</strong></h3>

```powershell
Set-MailboxRegionalConfiguration -Language en-gb –TimeZone "GMT Standard Time"
```

<h3><strong>To set all users in the tenant to English UK, and GMT Standard Time:</strong></h3>

```powershell
Get-Mailbox –Resultsize unlimited | Set-MailboxRegionalConfiguration –Language en-gb –TimeZone "GMT Standard Time"
```

<h3><strong>To retrieve settings for all users in the tenant:</strong></h3>

```powershell
Get-Mailbox | Get-MailboxRegionalConfiguration
```

Depending on the number of users in the tenant this may take several minutes to process, and some warning messages may be displayed to inform you that you’ve exceeded your Throttling Policy budget; this is just a warning and the command will complete. Once these settings changes have been made users will not have to make these choices at first login, or at any subsequent login. Users will still have the option to manually change them through their Options panel at any time. Simple!

Users created <em>after</em> running this command will still get asked to choose; so it’s probably a good idea to run this every time you create a new batch of users to ensure the new users are set correctly.

<strong>Update: </strong>This process should also work for regular Exchange Online users (for example, in Office 365), since Live@edu used Exchange Online as well as Windows Live services.