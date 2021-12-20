---
layout: default
title:  "Making spam manageable"
date:   2021-09-26
categories: blog
---

*This blog entry was originally posted to [sue.nl](https://sue.nl/making-spam-manageable-by-using-email-aliases/)*

**Nowadays, spam and data breaches seem to be the default. In this article I will explain how to use email aliases to help cut down on spam more effectively and how email aliases avoid the pitfalls of “the + sign trick”.**

# The what and why

An alias is an alternative email address that also gets delivered to your mailbox. There are different implementations of this. Some aliases can be replied from, some not. Some people implement "aliases" by simply using multiple mailboxes, others use the + sign trick (yourname+service@example.com), or they forward it. In this post, we will be using a mechanism which sends emails – sent to any of the aliases – to our main mailbox, but which still allows us to respond using the alias itself to hide our main mailbox’ address.

# Multiple benefits

Using aliases instead of one single mail address has multiple benefits.

First of all, it allows you to know where the email is coming from. 

By using a different alias on every website, you will be able to tell where someone found the email address they are contacting you from. This enables you to tell if the spammer found your email address on your website, or if they somehow got access to the email address you gave to that one online store – that just seemed slightly sketchy but not sketchy enough to not give it a try. Being able to tell the source is very useful. It makes it visible if any of the places you gave your alias to are leaking your personal information or using it for something they shouldn’t be using it for. It ensures that you can hold the companies you do business with accountable. It also enables you to more easily tell apart well-designed scam emails. After all, it would make no sense for GitHub to be sending that "unexpected login" alert to the email you gave to Twitter. It would thus be very obvious that this is a scam email.

Secondly, in some configurations, the alias could forward the email to multiple recipients. That way, you and your team lead could both be kept into the loop on a specific subject. This is one of the ways aliases are often used within Sue, allowing employees to keep their main email account to themselves but still easily and automatically share relevant emails.

Most importantly though, it allows for a separation. Instead of getting hundreds of spam mails to your real email address, spam will end up in just a single alias. When the spam arrives, you just throw away that single alias. That way you can finally cut off the spam without cutting off everyone else.

# Avoid the + sign trick

Some readers may wonder, why not just use the + sign trick as it is supported by many providers natively? Sadly, the + sign trick has a few important issues that makes it a weak alternative to aliases. Firstly, many services incorrectly reject email addresses with the + symbol in them, marking them as invalid email addresses. However, even if the + sign trick is allowed (because the format is so standardized) spammers can easily turn yourname+service@example.com into yourname@example.com, removing all separation and easily spamming your main address. The + sign trick is therefore not a viable alternative to aliases when it comes to spam protection.

# Implementing it

Frankly, there are many ways one could go about this. For my personal usage I have gone with the Open Source service SimpleLogin. If SimpleLogin is not your vibe, there are alternatives such as AnonAddy. Alternatively, you could also set it up yourself or by using tools of your domain’s hosting provider if these exist. In this post I will talk about SimpleLogin, simply because I have more experience with that specific provider. The setup we will be going with is one secret email and many aliases, one per service, using our own domain. We will add a bit of secrecy to each service’s email, to avoid impersonation. Our end goal is to have all our email arrive in a secret mailbox, but never let this secret mailbox be known to anyone. We will be making use of SimpleLogin’s official instance, but it is possible to instead self-host the platform.

First things first we need to notice that SimpleLogin is not an email provider, but a forwarding service. They will not store our actual emails, so we will need a destination mailbox. This can be on a custom domain, but an email from a free provider such as Outlook or Gmail will work just fine too. After we have our destination mailbox set up, we can create an account on SimpleLogin. We can either create aliases on some of the domains they have provided for free, or opt for more control by using our own domain name. Do note that custom domains are not free on the official instance, so you will have to buy their premium membership or self-host.

Now we can start creating aliases. For example, I would personally create a new Custom Alias for Twitter using a random prefix. This would become something like twitter.zed81@example.com and set up our main mailbox as the destination mailbox. The random prefix (zed81 in this case) allows us to prevent this email from being guessed. We then give this email address to Twitter instead of our main mailbox. If we respond to an email sent to us by Twitter, SimpleLogin will ensure the email is translated correctly to use the alias as sender information so Twitter will still not know our main address. Simple, yet effective.

# Summarizing

Using email aliases is really not as complicated as it may sound, but they are an amazing tool to keep spam under control. I personally followed this approach for roughly a full year now and don’t see myself going back any time soon. I hope this blog post has convinced you of the benefits as well. If you have not yet, give it a try yourself!