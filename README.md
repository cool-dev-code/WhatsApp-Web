<div align="center">
  <img src="src/assets/images/128.png" alt="WhatsApp Web Logo" width="150">
  
  <h1>Welcome to the WhatsApp Web repository</h1>
  <strong>Any contribution would be appropriated 💻</strong>
  <h6>Made with ❤️ by developers for developers and productive users🧑</h6>
</div>
<br>


<p align="center">
  <a href="https://chrome.google.com/webstore/detail/daily-20-source-for-busy/jlmpjdjjbgclbocgajdjefcidcncaied">
    <img src="https://img.shields.io/chrome-web-store/users/jlmpjdjjbgclbocgajdjefcidcncaied?color=EA4335&logo=google-chrome&logoColor=white" alt="Chrome Web Store users">
  </a>

  <a href="https://addons.mozilla.org/en-US/firefox/addon/daily/">
    <img src="https://img.shields.io/amo/users/daily?color=orange&logo=mozilla" alt="Mozilla Web Store users">
  </a>

  <a href="https://twitter.com/dailydotdev">
    <img src="https://img.shields.io/twitter/follow/dailydotdev?color=26A0ED&label=Follow&logo=twitter&logoColor=white&style=flat" alt="Twitter">
  </a>

  <a href="https://storybook.daily.dev">
    <img src="https://img.shields.io/badge/%20-storybook-502ab0?logo=storybook&logoColor=white" alt="Storybook">
  </a>

</p>




## 🗞 About

> WhatsApp-Web is an open-source Chrome browser extension which help users to switch full screen

It does not read your messages or expose your privacy

We care about:

* 🌟 **Maintenance**: We are working to introduce new features, fix bugs, and improve user experience.
* 🧵 **Open-source**: This extension is completely open-source. We believe in transparency and giving back to the community, so we decided to publish the source code to GitHub. Suggest a feature, report a bug, or even contribute. Everyone is welcome!😊

## 📌 Get WhatsApp Web Extension

This extension is currently available for Google Chrome, and Microsoft Edge. 
<p align="center">
    <a href="https://r.daily.dev/chrome">
    <img src="https://img.shields.io/badge/%20-Chrome-red?logo=google-chrome&logoColor=white" alt="Download for Chrome" />
    </a>
	
    <a href="https://microsoftedge.microsoft.com/addons/detail/dailydev-news-for-busy/cbdhgldgiancdheindpekpcbkccpjaeb">
    <img src="https://img.shields.io/badge/%20-Edge-blue?logo=microsoft-edge&logoColor=white" alt="Download for Edge" />
	
    <a href="http://go.daily.dev/">
    <img src="https://img.shields.io/badge/%20-Mobile-502ab0" alt="Download for Mobile" />
    </a>
</p>

## 📯 Philosophy

We, as developers, spend a lot of time looking for valuable articles and blog posts. Please Fork 🍴 this repository to contribute us.

That's why built daily.dev, to help you:

* 🖥 Chat on big screen
* 👨‍💻 Stay up-to-date
* ⏳Save time

## 🚀 Installation Method of WhatsApp-Web Extension

Let's setup WhatsApp-Web locally. Follow up the setups below to quickly get started.

## ⚙️ Setting Up in Chrome

### → STEP #0

* Go to <a href="chrome://extensions/"><img src="https://img.shields.io/badge/%20-Chrome-red?logo=google-chrome&logoColor=white" alt="Download for Chrome" /></a>
* Make sure docker-compose is installed on your machine. Take a look at the [official guide](https://docs.docker.com/compose/install/) for installation. After installation, run the following command in your terminal for a double check.

```sh
docker-compose -v
# docker-compose version 1.29.2, build 5becea4c     // Expected result
```

### → STEP #1

Clone the [apps](https://github.com/dailydotdev/apps) repo.

### → STEP #2

> Daily services are fully dockerized and publicly available on a Google Cloud Registry (GCR) repository. We are going to use them!

The first step is to **pull and run the docker images**, thanks to docker-compose network and environment variables are preconfigured and ready-to-go.

Navigate to the cloned repository and make sure Docker is running on your machine. After that run the following command to run all daily services:

```sh
docker-compose pull && docker-compose up
```

The command will take a while depending upon your internet speed.

### → STEP #3

Now we need to apply the migrations on our databases so they will have the latest schema:

```sh
docker exec apps_daily-api_1 node ./node_modules/typeorm/cli.js migration:run

# ... // Expected result
# Migration PostToc1623847855158 has been executed successfully.
# query: COMMIT

docker exec apps_daily-gateway_1 yarn run db:migrate:latest

# Using environment: development   // Expected result
# Batch 1 run: 23 migrations
# Done in 1.57s.
```

### → STEP #4

The last step is to populate your database using the seed data. All you need to do is, run the following command in your terminal:

```sh
docker exec apps_daily-api_1 node bin/import.js

# importing Source              // Expected result
# importing Post
# importing Keyword
# importing PostKeyword
# done
```


That's it! 🥂

Now you have all the required services running. Each project's repo explains what services are needed and how to get started with them.

> Note that currently, not all services are ready (or needed) for local environment so Daily Redirector and Daily Monetization services are not available for you.
>
> It means that if you click on an article you will get error 404 and that you will not see ads on your local environment.

## 🎨 Setting Up Daily Apps

Now, let's quickly set up daily.dev apps.

### → STEP #1

Run the following commands in your terminal to bootstrap.

Yes, we use `lerna` for this purpose.

```sh
npm i -g lerna
lerna bootstrap

# ...     // Expected result
# lerna success Bootstrapped 5 packages
```
### → STEP #2

Go to `packages/webapp` in the `apps` folder. Run the following command to start the webapp in development mode. It will watch for all the file changes.

```sh
npm run dev
```
### → STEP #3

Go to `packages/extension` in the `apps` folder. Run the following command to start the extension in development mode. It will watch for all the file changes and generate the output in `dist` folder.

```sh
npm run dev:chrome
```
### → STEP #4

By now, you will have unpacked daily.dev extension in your `dist` folder. Follow the steps listed below to load the extension.

1. Go to `chrome://extensions` path in your Chrome browser.
2. Enable `Developer mode` from the top right section.
3. Click on `Load Unpack` button and select your `dist` folder.

That's it! Your extension has been loaded in your browser. Happy hacking! ✌️

## 🙌 Want to Contribute?

We are open to all kinds of contributions. If you want to:
* 🤔 Suggest a feature
* 🐛 Report an issue
* 📖 Improve documentation
* 👨‍💻 Contribute to the code

You are more than welcome. Before contributing, kindly check our [guidelines](https://github.com/dailydotdev/.github/blob/master/CONTRIBUTING.md).

## 🤔 FAQs

We have compiled a list of FAQs. You can find it [here](https://daily.dev/support).

## 🎩 Core Team

Meet the core team of daily.dev:
* [@idoshamun](https://twitter.com/idoshamun)
* [@nimrodkramer](https://twitter.com/NimrodKramer)
* [@tsahimatsliah](https://twitter.com/TsahiMatsliah)

Feel free to reach us out and say hi 👋.


## 💬 What Do You Think of daily.dev?

<div align="left">
    <p><a href="https://twitter.com/dailydotdev/"><img alt="Twitter @dailydotdev" align="center" src="https://img.shields.io/badge/twitter-%231DA1F2.svg?&style=for-the-badge&logo=twitter&logoColor=white" /></a>&nbsp; Tweet us @dailydotdev to share your thoughts and stay up-to-date. </p>
    <p><a href="https://facebook.com/dailydotdev/"><img alt="Facebook @dailydotdev" align="center" src="https://img.shields.io/badge/facebook-%231877F2.svg?&style=for-the-badge&logo=facebook&logoColor=white" /></a>&nbsp; Like us to know what's happening at daily.dev and share your reviews.</p>
    <p><a href="https://www.producthunt.com/posts/daily-dev"><img alt="daily.dev at ProductHunt" align="center" src="https://img.shields.io/badge/producthunt-%23DA552F.svg?&style=for-the-badge&logo=product-hunt&logoColor=white" /></a>&nbsp; Checkout our ProductHunt page and let us know what you think.</p>
    <p><a href="https://daily.dev"><img alt="daily.dev Website" align="center" src="https://img.shields.io/badge/Daily Website-%233693F3.svg?&style=for-the-badge&logo=icloud&logoColor=white" /></a>&nbsp; Visit our home for all useful links.</p>
    <p><a href="https://chrome.google.com/webstore/detail/daily-20-source-for-busy/jlmpjdjjbgclbocgajdjefcidcncaied"><img alt="daily.dev at ChomeStore" align="center" src="https://img.shields.io/badge/Chrome Web Store-%234285F4.svg?&style=for-the-badge&logo=google-chrome&logoColor=white" /></a>&nbsp; See our Chrome Store page to grab the extension or share your feedback.</p>
      <p><a href="https://microsoftedge.microsoft.com/addons/detail/dailydev-news-for-busy/cbdhgldgiancdheindpekpcbkccpjaeb"><img alt="daily.dev at EdgeAddons" align="center" src="https://img.shields.io/badge/Edge Addons-%230078D7.svg?&style=for-the-badge&logo=microsoft-edge&logoColor=white" /></a>&nbsp; Check us out on Microsoft Edge Addons and let us know your thoughts.</p>
    <p><a href="https://addons.mozilla.org/en-US/firefox/addon/daily/"><img alt="daily.dev at Firefox" align="center" src="https://img.shields.io/badge/Firefox Addons-%23FF7139.svg?&style=for-the-badge&logo=firefox-browser&logoColor=white" /></a>&nbsp; Check our Firefox Add-on and share your thoughts.</p>
</div>


## 📑 License
Licensed under [AGPL-3.0](https://github.com/dailydotdev/daily/blob/master/LICENSE).
