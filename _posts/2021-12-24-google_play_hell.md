---
layout: default
title: "Your app is not compliant with Google Play Policies: A story from hell"
date: 2021-12-24
categories: blog
---

# The current state of my apps

For those who don't know me, I am a Linux system administrator who codes a lot, mostly as a hobby. During my hobbies I wrote a few Android apps too, my most known one being [Catima](https://catima.app).

Catima is only available on Google Play and F-Droid and will probably remain exclusive to these platforms for the forseeable future.

But why isn't Catima on other app stores, like the Samsung Galaxy Store, Amazon AppStore or Huawei App Gallery, one may ask. Is there something wrong with those stores? The answer may surprise you:

**The reason Catima isn't on alternative app stores isn't because there is something wrong with them, it's because there is something wrong with Google Play**.

# What is wrong with Google Play

Everyone knows Google Play. It is pre-installed on every Android device bought in stores, so it is the way to reach as many users as possible. That, however, is pretty much where the good parts end.

Unlike F-Droid, publishing on Google Play is not free but requires a one-time payment of 50 Euros to register a developer account. This account can then be used to publish as many apps with as you want, so the cost is not insane given the amount of users you reach, but still worth mentioning.

The real problem with Google Play, however, is not the money. **It is the incompetence of their support and moderation staff**.

# The beginning of the end

On October 2nd 2021, I received an email titled: ["Action Required: Your app is not compliant with Google Play Policies"](https://github.com/TheLastProject/Catima/issues/439#issue-1014074229).

![The initial e-mail](/assets/images/blog/2021-12-24-google_play_hell/135721623-9df9ad54-81f3-4dac-8410-658413e47b9e.png)

I was confused, because I actually always do read the rules and was pretty sure I wasn't breaking any policy.

After several mails back and forth, I started to get a hunch: **Google was using Google Translate incorrectly**.

You see, Google doesn't accept apps saying they're free in the title (most likely to keep the app list clean, as this info is already readable on other places), and if you naively throws the Dutch word "vrij" (meaning "free as in freedom") into Google Translate, you get "free" in English. While the word "free" in English is ambigious, it is possible to use it to refer to things as being at no cost, which would break the policy.

Google never truly explained which word they had a problem with, just kept repeating vague statements like "your app's title in nl_NL and no_NO locales currently contains text that indicates price and promotional information", but this was my best guess as to what was wrong. After 4 full days of trying to teach Google staff how a dictionary worked, [I caved in and changed the Dutch and Norwegian titles](https://github.com/TheLastProject/Catima/issues/439#issuecomment-935645288). Not even 24 hours later, I got another email.

**"Action Required: Your app is not compliant with Google Play Policies"**

# The relentless gut-punching

The new compliance email did not focus on just Dutch and Norwegian, it marked 9 new languages:

![The second email](/assets/images/blog/2021-12-24-google_play_hell/136173470-2f77fa5b-da67-4a19-99ef-bb69c7ee5449.png)

Annoyed, [I changed all those translations and hoped for it to end](https://github.com/TheLastProject/Catima/commit/ddccbad0202aaa88a567ee5bc931840ed0231331).

Again, not even 24 hours later, I got another email:

![The third email](/assets/images/blog/2021-12-24-google_play_hell/136180398-e6051aa6-4765-4aac-bc54-b6a2cdadd8c0.png)

Fine, small change, so [I'll just update the Chinese translation](https://github.com/TheLastProject/Catima/commit/017034a78804eb092917086376192796587e373e).

At this point, we're on October 7th and I got a promising email: "Your update is live in the store":

![Translations approved](/assets/images/blog/2021-12-24-google_play_hell/136434121-02f7a4f4-1729-4587-8b6e-8be3360c0290.png)

While this was less than ideal, it seemed like the end of this hell, and like I could move on to focus on actually making the app better.

After "only" 5 days, the issue was "resolved" by pure guessing on my side. Well, mostly at least. There was just some last annoyances on [November 7th](/assets/images/blog/2021-12-24-google_play_hell/140650588-0be275bd-7cda-46ed-893e-ecef5ccb2ccd.png) and [November 20th](/assets/images/blog/2021-12-24-google_play_hell/142705625-64eaa677-f78c-4f5b-a8a9-8b2e79a9ad90.png), until something truly interesting happened.

# Google accidentally proves my theory

On November 23rd, I got another mail. Another "Action Required". This one, though, was somewhat different.

![The nonsensical mail](/assets/images/blog/2021-12-24-google_play_hell/142989964-b7fb84c0-c053-4d58-81f3-a4a7c5d06119.jpg)

Yes, you read that right. Google was upset that I used the word "Free" in my app titles. The only problem? I [never](/assets/images/blog/2021-12-24-google_play_hell/142989934-d05f6fc0-2dfd-4955-934b-780501213019.png) [used](/assets/images/blog/2021-12-24-google_play_hell/142989953-672361c8-a7b2-4827-a932-3a164f4fec6e.png) [them](/assets/images/blog/2021-12-24-google_play_hell/142989955-d5cd3aeb-4bb5-416f-800c-816711f6419d.png). This proved my theory: **Google was using Google Translate to translate the app titles instead of reviewing them with native speakers**.

I'll be honest, I pretty much had a mental breakdown that day. It was just... too insane for words.

# One last punch in the gut: a stupid Google Play Console bug

I got one last such e-mail on December 17th, this time talking about the Bulgarian translation. I [removed it](https://github.com/TheLastProject/Catima/commit/d84ce6ff8207752561ad7385de667cbcc0aa0182), thinking this was hopefully finally the end.

Sadly, a bug in the Google Play Console causes all fields of all languages to be revalidated if you make any change. Because Google recently [lowered the title length from 50 to 30 characters](https://android-developers.googleblog.com/2021/04/updated-guidance-to-improve-your-app.html) and not all Catima translators have changed their translations yet, I literally cannot edit the "non-compliant" title, as all fields of all languages need to follow the rules at the moment you hit save, even if you are not making changes to that specific field or language.

![Google Play Console bug](/assets/images/blog/2021-12-24-google_play_hell/FG0nEC0WYAUiU39.png)

As I write this, I have just received another email from Google after I told them I literally cannot comply due to this bug telling me to... make sure all my titles are 30 characters or shorter.

**Despite all I tried, it's now almost 3 full months later, and I am still "not compliant"**.

# Further reading

If you want to see all my frustration, take a look at [Catima GitHub issue #439](https://github.com/TheLastProject/Catima/issues/439) and [all these tweets](https://twitter.com/SylvieLorxu/status/1471875608636444675).
