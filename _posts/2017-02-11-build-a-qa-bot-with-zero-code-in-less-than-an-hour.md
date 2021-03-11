---
layout: post
title: How To Build A Q&amp;A Chat Bot
subtitle: With zero code, in less than an hour
tags: [Azure Bot Service, Cognitive Services, Digital Transformation, Microsoft Azure, QnA Maker, programming]
comments: true
bigimg: /img/botshot1.jpg
share-img: /img/botshot1.jpg
image: /img/bot-framework.svg
---

It's just gone 5:00am where I am in Seattle, WA. I fly home later tonight after soaking up a week with thousands of other members of Microsoft's technical community at an internal event called TechReady. Needless to say, the content shared is highly confidential but is motivating, inspirational and truly awesome. It's as a result of this shot of technical excitement that I decided to build a Q&amp;A chatbot. What's even better? I did it in less than an hour with zero code and so can you! Read on to find out how...

<!--more-->
<h2>Disclaimer</h2>
I am not a proficient developer. In fact, I find code scary. I can be dangerous with HTML, CSS, Python, and I've even been known to toy with VisualBASIC and C# in the past but one thing I don't call myself is a developer. This is important to note because when I first looked at this I naturally assumed it would be technically complex, time-consuming, and require a PhD in machine learning. As you'll see, it doesn't.

I'm expecting to update this post several times with more context and detail. When I built the chatbot I didn't have writing a blog post in mind and therefore didn't write out the steps or take screenshots. Since a few people have asked how I did it, I'm writing it up. There may be gaps, and if there are please let me know in the comments.

Lastly, the chatbot I've built is rudimentary. It's awesome and fully working, but to take it to the next level I can see the need to start adding some custom code and development. I provide what I did here purely "as-is" to help you get started.
<h2>Introducing my chatbot:&nbsp;jamesbmarshallbot</h2>
I needed a purpose to build a chatbot, and since I'm often asked fairly simple and common questions and am often setting an "OOF" (Out of Office) response I thought that a "virtual James" that people could ask questions of would be a great proof of concept and might even help keep my inbox manageable whilst I'm out with customers and partners.
<h3>Ways to interact</h3>
Right now you can speak to the chatbot in three main ways:
<ul>
 	<li><strong>Skype</strong> - as a contact you chat within the client.</li>
 	<li><strong>Microsoft Teams</strong> - as a bot you chat with via the web or desktop app.</li>
 	<li><strong>Web chat</strong> - a simple web portal chat interface.</li>
</ul>
It's actually very simple to support channels like FaceBook Messenger, Slack, Telegram and even services like Twilio but I haven't activated those for now.
<h2>You will need...</h2>
Actually, you won't need very much but here's a list that might help:
<ul>
 	<li><strong>An Azure subscription.</strong> Don't worry if you don't have one, you can get £150 of free credit by <a href="https://azure.microsoft.com/en-us/free/" target="_blank" rel="noopener">signing up for a trial</a>.</li>
 	<li><strong>Questions.</strong>&nbsp;This isn't strictly required, but if you have a bunch of URLs to FAQ pages it's very easy to train the chatbot on those questions automatically. As you'll see, you can add your own but a pre-existing bank of "question and answer pairs" can save some time.</li>
 	<li><strong>Refreshments.</strong> Diet Coke is my preference, but grab yourself a drink.</li>
</ul>
<h2>High-level Steps</h2>
I will cover these steps in more details as I update this post. In summary, the steps you're going to take are:
<ul>
 	<li><strong>Create the initial Q&amp;A bot</strong> using <a href="https://qnamaker.ai/" target="_blank" rel="noopener">QnA Maker</a>.</li>
 	<li><strong>Train the Bot</strong> with pre-existing FAQs and customer questions, and we'll test to make sure they're being answered correctly.</li>
 	<li><strong>Create a Bot using the <a href="https://azure.microsoft.com/en-us/services/bot-service/" target="_blank" rel="noopener">Azure Bot Service</a></strong> (in preview), to which we'll hook up the Q&amp;A chatbot we just made.</li>
 	<li><strong>Configure the Azure Bot Service and Q&amp;A Bot to work together</strong>, it's a few clicks and some copy-and-paste.</li>
 	<li><strong>Configure Channels</strong> for the chatbot to be interacted with.</li>
 	<li><strong>Start chatting!</strong></li>
 	<li><strong>[Optional] Create an Azure Web App</strong> to host a simple page with the web chat embedded in it.</li>
</ul>
At a high level, it's "as simple as that". You can <a href="http://chat.jamesbmarshall.com">chat to mine</a> if you like! Some questions to ask:
<ul>
 	<li>"How are you"?</li>
 	<li>"What is CSP?"</li>
 	<li>"Are you single?"</li>
</ul>
I've built mine to have learned from the <a href="https://partner.microsoft.com/en-GB/Solutions/cloud-reseller-FAQ" target="_blank" rel="noopener">CSP FAQ</a>. In theory, any of the questions there should get an answer from the chatbot. My next task is to go through and re-train the chatbot to understand more "natural" questioning, and of course, add more question-and-answer pairs to make it even more useful!
<h2>Creating the Q&amp;A chatbot</h2>
The first step is to sign up for the <a href="http://qnamaker.ai" target="_blank" rel="noopener">QnA service</a>. Once you're in, head to "Create new service". You should see a simple form to fill in that looks like this:

<img width="778" src="../../../../img/fireshot-capture-1-qna-maker-https___qnamaker-ai_create.png" alt="fireshot-capture-1-qna-maker-https___qnamaker-ai_create">

If you've got an existing FAQ page / pages that you want to include as part of creating the bot then you can list them out in the form. This saves a&nbsp;<em>huge</em> amount of time and means you have a great starting point from which to train your chatbot. You can also upload up to 5 files to the service if you have them stored in a&nbsp;.tsv, .pdf, .doc, or .docx format.
<h2>Training and testing the chatbot</h2>
After creating the bot, you'll be able to view all the question &amp; answer pairs that have been detected. This view below shows the ones picked up from the<a href="https://partner.microsoft.com/en-GB/Solutions/cloud-reseller-FAQ" target="_blank" rel="noopener"> CSP FAQ page</a>. There are over 200 pairs!

<img width="778" src="../../../../img/fireshot-capture-2-qna-maker_-https___qnamaker-ai_edit_knowledgebase.png" alt="fireshot-capture-2-qna-maker_-https___qnamaker-ai_edit_knowledgebase">

It's here that you can remove any questions that you don't need, add extra ones, re-word any answers and change the question language to be more "natural". Once you're happy with the questions you can click "Test" (on the left side of the screen) to start interacting with your bot!

<img width="778" src="../../../../img/qna.gif" alt="qna">

The interface is quite intuitive and you can make edits to questions and answers on the fly. I found this particularly useful as I'd type questions in a "real life" fashion, and if I didn't get the answer I was expecting I could correct it immediately. Just remember to click "Save and retrain" to implement your changes!
<h2>Creating an Azure Bot Service</h2>
I'll assume that if you're this interested in creating a bot you'll have signed up for an Azure subscription or you'll have an existing one that you can use. If you don't, you can get <a href="https://azure.microsoft.com/en-gb/free/" target="_blank" rel="noopener">£150 free Azure credit by signing up</a>. Once you're into your Azure portal, create a new Bot Service by searching the Azure marketplace for "bot service", you should see it listed in the results:

<img width="778" src="../../../../img/fireshot-capture-4-everything-microsoft-azure_-https___ms-portal-azure-com_blade_.png" alt="fireshot-capture-4-everything-microsoft-azure_-https___ms-portal-azure-com_blade_">

Follow the wizard to create the service, noting that you can add it to an existing Resource Group or create a new one. Once provisioned, navigate to the chatbot service where you'll see that you need to configure your App ID unique keys.

<img width="778" src="../../../../img/fireshot-capture-5-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_.png" alt="fireshot-capture-5-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_">

Again, follow the guides here - they're very simple and just involve some copy and pasting into the right window. I'm not sure why this isn't simpler, but I'm sure in time this won't be such a faff! Once you've configured your App ID you'll find the greyed out content activated and you'll want to select "Question and Answer" from the array of options.

This should pop up a box that'll allow you to select your QnA Maker bot:

<img width="778" src="../../../../img/fireshot-capture-6-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_.png" alt="fireshot-capture-6-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_">

<h2>Configuring the channels</h2>
Once you're connected up you'll go to the Bot Service configuration page that'll default to the code view. Don't worry, this is a zero code walkthrough so you won't need to fiddle here (unless you want to!). We're interested in the "Channels" tab:

<img width="778" src="../../../../img/fireshot-capture-7-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_.png" alt="fireshot-capture-7-bot-service-microsoft-azure_-https___ms-portal-azure-com_blade_">

Since I've already built my chatbot, a number of channels are already activated. It's in this section that you can select which channels you want, and turn them on or off as required.
<h2>Start chatting!</h2>
<img src="../../../../img/chatbot.gif" alt="chatbot" width="336" height="491">

You don't actually need to publish your chatbot to start interacting with it through your favourite channels. If you just want the chatbot for private or internal use then you can leave it unpublished; however, if you want it for public access, listing in directories etc. then it'll need to be subject to a quick review by Microsoft to ensure it meets the review&nbsp;guidelines.
<h2>Further Reading</h2>
It goes without saying that I'm not a genius. I did reference some online materials to help put this all together:
<ul>
 	<li><a href="https://blogs.msdn.microsoft.com/bluesky/2016/12/22/introduction-to-qna-maker-en/" target="_blank" rel="noopener">Create Bot from FAQ page with no coding</a>&nbsp;- a little light on detail, but the last step helped me make the bridge between QnA Maker and Azure Bot Service.</li>
</ul>