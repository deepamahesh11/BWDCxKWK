# Deepa Mahesh's KWK Scrollytelling Project


## Demo
See a live demo of the page [here](https://deepamahesh11.github.io/BWDCxKWK/)!

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## How to clone the repo
On this repo's homepage in GitHub, click the `Use this template` button. Select the option to create a new repository. This will create a new repo under your GitHub account.

Navigate to your new copy of this template in your GitHub profile. 

Clone your new repo locally and `cd` into it. 

Run `npm install` and then `npm run dev` to spin up the project locally. Then, start making changes! You can use this repo as a starting point for your own final project or simply as an example. 

## Credit
Repo created using vite (`npm create vite@6`)

##use of AI 
In DeepIntro.svelte I was struggling to make the article-text css dissapear as I wanted it to be invisible (so it would act as a marker for my text bubbles to appear). I was struggling on how to make it invisible because everything I tried did not work. I used AI as guidance to figure out to use the command "!important" and ":global(___)"
<style>
 :global(.observer-hidden) :global(.article-text) {
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    color: transparent !important;
    margin: 10vh auto !important; 
    padding: 0 !important;
    pointer-events: none;
  }
</style>
