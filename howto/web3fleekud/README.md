# Web3 101

## Setting up a web3 website

> "NFTs: The Biggest Scam of our Times"  
> -- Apparently everyone on the Internet right now.

Cryptocurrency sentiment might be low, and NFTs get a bum rap, but what if I told you NFTs aren't just monkey pictures and web3 is so much more than just blockchains?  

That's what this article is about.  

Web3 is decentralized, peer to peer, and hopefully more open and uncensorable than the increasingly walled gardens of social media and secretive search engines who think it's their job to tell you what you can read and can't read.  

In fact, the tech in this tutorial has just as much to do with the early days of Napster and Torrents as it has to do with Bitcoin.  

Today we'll be looking at how to set up a website breaking with the client-server architecture of old. Hosted on IPFS and accessed through a quirky little smart contract on the Polygon Blockchain.  

And how will we do this? Through GitHub, Next.JS, IPFS, Fleek and Unstoppable Domains that's how!

## Step 1: Buy an Unstoppable Domain or an ENS domain

This is entirely optional, as you can follow the steps and deploy to IPFS without necessarily linking the domain to an IPFS hash, but if you want your website to be "easily" accessible for those Brave and Opera users who happen to have the Unstoppable Domain extention installed and IPFS activated (which is really a rather big caveat at the moment, hopefully the guys at Opera, Brave and Unstoppable Domains are working to sort this out in the long run) , then getting a domain will give you the "full experience" of a web3 website.

## Step 2: GitHub
There are lots of ways to get working with web3 and hosting it on IPFS. We could for example write a static index.html by hand and just upload it to [Pinata](https://pinata.cloud/) or some other pinning service and then link it on Unstoppable Domains, or we could use Unstoppable Domains own website builder, but due to reasons that'll become clearer over time, we want some way of saving, storing backups and easily upload our website. We also want some way of creating larger, more functional websites. And because of the static nature of websites hosted over IPFS, [GitHub](https://www.github.com) will serve as a CMS solution for working with out website.

For this project, I have bought myself a web3 domain by the name of [colorfonts.nft](colorfonts.nft) and so naturally, I'll name the new project Colorfonts.

Take note that keeping the README.md checked will create a README.md file that will have to be deleted before we create our Next.JS project.

https://user-images.githubusercontent.com/11506194/222984483-80479cbf-c68d-4b57-973c-9ecfe928cf64.mov

## Step 3: Next.JS

Now clone your repository and cd in to create a Next.JS application. In my case the commands were:

>gh repo clone tcarisland/colorfonts  
>cd colorfonts  
>rm README.md # Only necessary if you've created a README.md in the previous step  
>npx create-next-app .  

Answer yes to Typescript, ESlint and for creating a src directory when prompted.  

https://user-images.githubusercontent.com/11506194/222985487-83a05e18-0a07-436f-bb3e-ee277fb485cd.mov

You can then start your application by first installing dependencies and running the project.

>npm i  
>npm run dev

If you open it up in localhost:3000 you'll see a demo application.  

![nextjs-screenshot](https://user-images.githubusercontent.com/11506194/222985522-2216a905-cb9e-4bdc-a433-a071a63b90e4.png)

By opening src/pages/index.tsx and clearing out nearly all the html, we can write a simple Hello message for our custom page.

![index-tsx-screenshot](https://user-images.githubusercontent.com/11506194/222985976-48473b58-0907-417c-b36c-a4fb25e1529a.png)  

This gives us an unassuming webpage with our hello message.

![hello](https://user-images.githubusercontent.com/11506194/222986017-95a25b99-c311-4d7b-a4e2-eb5cb713833e.png)

Now we're ready to commit and push and share it on IPFS.  

>git add .  
>git commit -m "initial next.js"  
>git push

## Side note on IPFS

So what is this all about?  

Traditionally, with the original web and web2, websites follow the client-server architecture where dedicated hardware running server software such as apache and nginx provided html upon request using the hypertext transfer protocol, also known as HTTP, but what if we could share this information on a network where each computer is both a client and a server? Both consuming and providing information to others by using it?

This has already been the case with BitTorrent and has been around for already 20 years to share large files (all though you couldn't "visit" these files the way you'd visit a website).  

Now IPFS provides a somewhat similar network where webpages can be stored in an analogous fashion and opened with an IPFS enabled browser such as Brave or Opera.  

But what's the catch?  

The catch is that all though users of the IPFS network might also share that data, we need to make sure that the data is "pinned" either by running our own IPFS node or pin it using a pinning service.  

This is where [Pinata](https://pinata.cloud) would have entered in to it if it wasn't for the fact that [Fleek](app.fleek.co) came along and made it possible for us to easily create automatic deployment scripts, publishing new changes on IPFS whenever you made a commit or otherwise triggered the deployment pipeline.

## Step 4: Fleek

