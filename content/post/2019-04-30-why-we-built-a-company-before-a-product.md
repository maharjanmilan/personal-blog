---
title: Build a custom Contact Form for your static website
date: 2019-04-30
hero: "/images/1_sSWNVHPWeBDZni5waZm9rQ.png"
excerpt: In this tutorial we will learn how to use google sheet as a backend to store
  the data submitted from a contact form
timeToRead: 3
authors:
- Milan Maharjan

---
If your website doesn’t change that often and all the features you need can be implemented with a static site, then there is no point building a bulky dynamic site. After all static sites are fast, simple, costs low, easier to scale and more secure.

Being said that, sometimes we need some features that a static sites can’t offer. Getting data from a contact form is one of them. But there’s a very easy way to do that.

In this tutorial we will learn how to use google sheet as a backend to store the data submitted from a contact form.

We’ll be using

* [GitHub Pages](https://pages.github.com) to host my static contact form (_free_)
* Contact form template by [Colorlib](https://colorlib.com/download/160/) (_also free_)
* [Google App Script](https://developers.google.com/apps-script/guides/sheets) to use [Google Sheet](https://docs.google.com/spreadsheets) as data storage (_also free_)

***

We’ll first create a url to submit the contact form to. Let’s begin !

1. Open [Google Sheet](https://docs.google.com/spreadsheets) and create a new sheet.
2. Add the names of the input fields in your html form in the first row of the sheet. We’ll add `sn, name, email, subject` and `message` Field `sn` is auto generated serial number and this is not included in the html form.

![](https://cdn-images-1.medium.com/max/1600/1*891xJWYtiC2d6-16w7_NHg.png)
<img src="https://cdn-images-1.medium.com/max/1600/1*891xJWYtiC2d6-16w7_NHg.png" alt="drawing" width="200"/>

3\. Click `Tools` in menu bar, then click `Script Editor`

![](https://cdn-images-1.medium.com/max/1600/1*cJtymE7LU3TaJzVVUb3wqQ.png =250px)

4\. This will open a script editor page. Copy the following code and paste it in the script editor. This script will listen for a `POST` request and add the submitted data as a new row in the google sheet.

Google Sheet script

5\. Save the script. Then click `Run > Run function > setup` It will then ask for permission to access your google sheet. Just allow it. Then click `Publish > Deploy as web app` Set project version as `new`, execute the app as `me` and who has the access to app as `Anyone, even anonymous.` Then click deploy and it will display a web app url. Copy this url, we’ll need this later.

![](https://cdn-images-1.medium.com/max/1600/1*I5IGS_gfa-zCB9WO4_o0hA.png)

That is all we need to do in google sheet. Now let’s setup our frontend.

***

6\. In your html form, let’s add few jQuery script to submit a POST request to the url we generated in step 5 above. Add following codes between script tag in your html. Replace the url in below code with your google script url and also replace the form class name.

jQuery code to submit the form data to google script url

Whenever you submit the contact form, this jQuery function will do ajax request to the google script url with the form data as payload.

Remember that the input field names of the form should be defined in the google sheet’s first row. You can add any number of input field in the form. Just define the field names in the google sheet and the submitted values will be populated in the sheet automatically.

I have hosted my contact form using Github Pages. Check it out here [https://maharjanmilan.github.io/contact-form](https://maharjanmilan.github.io/contact-form "https://maharjanmilan.github.io/contact-form").

Once you submit the form, if the data submission was successful you’ll see a success popup. You can also replace this popup with other beautiful alternatives.

![https://maharjanmilan.github.io/contact-form](https://cdn-images-1.medium.com/max/1600/1*D1aG9FOdm0bK-UdVUIEzAw.png)[https://maharjanmilan.github.io/contact-form](https://maharjanmilan.github.io/contact-form "https://maharjanmilan.github.io/contact-form")

7\. Now you can see the contact details submitted from the form in you google sheet.

![](https://cdn-images-1.medium.com/max/1600/1*zRAIkWAkw2Hl6ro74_hSgA.png)

If you need a date column to record the submitted date just add `Timestamp` header right beside `message` This field will auto-populate the submitted date.

That’s it. As simple as that.

Modify it slightly and you can create a newsletter form or even build a product order form. The possibilities are limitless.

You can also clone my project [https://github.com/maharjanmilan/contact-form/](https://github.com/maharjanmilan/contact-form/ "https://github.com/maharjanmilan/contact-form/") and see the implementation there.

If you want to learn how to deploy your static site to Github Pages see [here](https://pages.github.com/). It is very easy. You can even use your custom domain name for free.

There are lot of other free static hosting services like [Netlify](https://www.netlify.com/), [Firebase](https://firebase.google.com/), [Amazon S3](https://aws.amazon.com/s3/), [Zeit](https://zeit.co/), [Forge](https://getforge.com/). Check them out as well.

Btw you can also trigger the google sheet to send email with the form data. But that’s for another tutorial :)

I hope this was helpful.

![](https://miro.medium.com/max/1400/1*sSWNVHPWeBDZni5waZm9rQ.png)