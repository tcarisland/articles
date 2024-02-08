# Web3 101

## Setting up a web3 website

> "NFTs: The Biggest Scam of our Times"  
> -- Apparently everyone on the Internet right now.

## Step 1: GitHub
By hosting a copy of the website on GitHub, we can use *actions* to automatically deploy to Fleek.

It'll also function as a simple backup and content management system (CMS).


## Step 3: Next.JS

Now clone your repository and cd in to create a Next.JS application. In my case the commands were:

>gh repo clone tcarisland/colorfonts  
>cd colorfonts  
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

This is where [Pinata](https://pinata.cloud) would have entered in to it if it wasn't for the fact that [Fleek](https://app.fleek.co) came along and made it possible for us to easily create automatic deployment scripts, publishing new changes on IPFS whenever you made a commit or otherwise triggered the deployment pipeline.

## Step 4: Fleek

