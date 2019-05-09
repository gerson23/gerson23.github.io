---
layout: post
title:  "SMTP mail in Python"
date:   2019-05-09 07:30:00 -03:00
categories: mail smtp python teams
---

I was writing a little bot in Python to automate some build handling -- we have large builds that are stored remotely and, as our network is not as fast as it needed, the bot downloads them as they get available -- and I wanted to integrate it with Microsoft Teams. One easy way available is to configure a team channel to receive e-mails, so I needed to send them from the Python bot.

Really thought it was gonna be harder, but Python already has a standard library `smtplib`[1] and it gets the job done.

{% highlight Python%}
import smtplib

server = smtplib.SMTP("smtp.office365.com", 587)
server.starttls()
server.login(USERNAME, PASSWORD)
server.sendmail(from_address, to_address, "Hello World")
server.quit()
{% endhighlight%}

Where `to_address` will be something random that Teams created, like "123asdf@amer.teams.ms".

This will get a message going, the content will be left empty though. So there's a helper class on `email` standard library that can help fill the all the voids.

{% highlight Python%}
from email.message import EmailMessage

mail = EmailMessage()
mail['From'] = from_address
mail['To'] = to_address
mail['Subject'] = "Pictures from the party"
mail.set_content("Hello world!!")
{% endhighlight%}

With the mail object in our hands we just need to change the `sendmail` line in the first snippet to:

{% highlight Python%}
server.send_message(mail)
{% endhighlight%}

And we will have a fully functional mail sender in Python.

***

[1] [smtplib official documentation](https://docs.python.org/3/library/smtplib.html)