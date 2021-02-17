---
Title: Phishing 
Description: What is phishing, how to detect it. 
Date: 06-07-2020
Tags: #mail, #phishing, #security
References:
Editor: markdown
---

# Phishing 

## Intro
Phishing is the fraudulent attempt to obtain sensitive information such as *usernames, passwords and credit card details* by disguising as a trustworthy entity in an electronic communication. Typically carried out by email-spoofing or instant messaging, it often directs users to enter personal information at a fake website, the look and feel of which are identical to the legitimate site. Phishing is an example of social engineering techniques being used to deceive users. Users are often lured by communications purporting to be from trusted parties such as social web sites, auction sites, banks, online payment processors or IT administrators.

We obviously have a very competent spamfilter in place that will block most of these before they end up in your mailbox. Nevertheless, technical solutions aren't always airtight and one day a very well crafted phishing mail might end up in your mailbox.

As will be re-iterated throughout this document: If there's any doubt or suspicion about an email, let us know at emielvanseveren@outlook.com

## How to spot a phishing email

Below you'll find some critical questions you can ask yourself to evaluate the validity of an email.

### Are you expecting the email?

Questions to ask yourself:

Have I given my email address to this company before? Do I have an account with this company?

If you haven't ordered anything lately or haven't used your company email-address to place an online order. A valid delivery-mail is highly unlikely to arrive in your company-mailbox. Same goes for any account really. If it isn't linked to your company-mailbox, any mail coming from such a source should be treated with caution.

### Does the content look suspicious?

- **Check for obvious spelling mistakes**
Are there obvious grammar errors? Is there awkward sentence structure, like perhaps it was written by a computer program or someone whose second language is English? Take a closer look as companies very rarely send out emails riddled with spelling-mistakes.

- **Don't give up personal information**
Rest assured that a Bank or any other legitimate company will never ask you for credentials or other personal information via email.

- **Beware of urgent or threatening language in the subject line**
Invoking a sense of urgency or fear is another common phishing tactic. Beware of subject lines that claim your “account has been suspended” or your account had an “unauthorized login attempt.”

- **Review the signature**
Lack of details about the signer or how you can contact a company strongly suggests a phish. Legitimate businesses always provide contact details.

- **Check the general formatting**
Does the formatting and design look different from what you usually receive from an organization? Maybe the logo looks pixelated or the buttons are different colors. Or possibly there are weird paragraph breaks or extra spaces between words. If the email appears sloppy, proceed with caution...

### Does the email come from a valid source?
**Don't trust the display-name!**
As this is a free-to-use field in an e-mail, potential attackers can fill in whatever works best to mislead their target. Always check if the source-address of an e-mail is valid. Almost all major brands will use their main domain-name to send out mails.

Example: If LinkedIn is sending you an email it will most likely be from an address ending in @linkedin.com. In this case it is coming from members-linkedin.com, which should already raise some red flags.
<br/>

![450px-mail-from.png](/attachments/phishing/450px-mail-from.png)

Also, make sure you read it correctly. Phishing-campaigns usually use a domain that is very similar to the real one, to try to mislead you. (cf.: skyline-c.be or linkedin2.com could easily be mistaken for the real thing)

![450px-c-skyline.png](attachments/phishing/450px-c-skyline.png)

If you have any doubts about the domain-name, you can always lookup the registered owner of it at: https://www.whois.com/.

<br/>

### Does the email contain any malicious links?
Make sure you check any links in the e-mail before clicking them. You can check the links in an e-mail by hovering your mouse over them.

Should the suspicious mail contain a shortened link, you can check the full link trough this page: http://www.checkshorturl.com/

Make sure the link points to where you assume it is going and keep an eye out for any spelling mistakes in the domain name.

Example: Microsoft would never send me an e-mail containing links to the mailer.co.com domain. Notice in this case you'll have to look carefully, because the campaign uses the link onedrive.live.com.mailer.co.com, which closely resembles the valid onedrive.live.com domain.

![450px-link-in-mail.png](/450px-link-in-mail.png)

As a general rule of thumb: always double-check the url when entering credentials. It should be a valid domain for the platform you are logging on to. And it should ideally start with https://


### Does it have any attachments?
Any attachments coming from an email failing even one of the checks above should be treated with great caution. Attachments that are inside a password-protected zip file or attachments containing macro's will almost always be malicious, as will any executable. If there is any doubt, treat it as a phishing attempt and proceed to notify infosec.

## When you receive a potential phishing attempt

If you suspect or can verify that you've received a phishing attempt, always notify the InfoSec group (emielvanseveren@outlook.com). Don't worry about us receiving too many notifications about a single mail. We would rather receive 15 then none...

If you would be so kind as to always send us the spammail as an attachment (Open a new e-mail and drag the spammail into it). This way IT can see the headers of the e-mail and we are much better equipped to finetune the spamfilter

Please let us know as soon as possible in case:

- You've clicked a potentially malicious link
- You've opened a suspicious attachement
- You've entered your credentials through a link in a phishing mail. (in this case please also reset your password asap)

In certain cases timing can be essential. The sooner we are notified the better...