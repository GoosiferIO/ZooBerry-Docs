---
draft: true
---

# Making a Rock
by Goosifer

## Introduction

This guide will walk you through the process of making a rock for Zoo Tycoon 1. Although it doesn't sound super exciting, it's a great way to get started with modding the game because they really don't take too much configuration.

## Configuration

Configuration just means editing the game's files to make our own content. We don't actually directly edit the game's files (unless your intention is to modify existing game behavior). Instead, we make copies of them and edit the copies. This way, we can always go back to the original files if we mess up, but mainly our intention for this tutorial is to make new content, not replace the old.

Zoo Tycoon 1 uses text files called `.ini` files to configure the game's entities, but they usually don't carry the `.ini` extension. Blue Fang is an early example of a video game developer who encouraged modding, and so they included a few custom `.ini` file formats just for us to extend the game. The one relevant to rocks is the `.ucs` file format.

To avoid any further confusion, let's leave it at this: the `.ucs` file format is a custom `.ini` file format that Zoo Tycoon 1 uses to configure rocks. You can open these with any text editor, but I recommend using [Visual Studio Code](https://code.visualstudio.com/). We can go over the other file formats in later tutorials.

## Creating Our Workspace

To start, we need a directory where we'll be working. I recommend creating a `Mods` folder inside of your `Documents` folder on your computer. This way, you can keep all of your modding work in one place and it's easy to find. Inside of the `Mods` folder, create a new folder called `zbrock`, but really you can call it whatever you want. This is where we'll be working.

For this guide, I'm simply going to tell you what folders and files to create and how to organize this in the project directory. However, later tutorials will expand on the intuition behind this organization and how to use it to your advantage.

## Gathering The Files

To get started, you'll need to find the files that you'll be working with. In the beginning it will be confusing because the game's files are all over the place, but you'll get used to it and even start to experiment as you get more comfortable. In later tutorials, I'll show you how to extract all of the game's files in one place so you can work with them more easily.

For now, let's go into the game's main install directory and only grab what we need:

`C:\Program Files (x86)\Microsoft Games\Zoo Tycoon`

The files are compressed into `.ztd` files so they'll be easy to spot. You won't need any special hacking tools to open them, they're actually just zip files. I recommend using [7-Zip](https://www.7-zip.org/) to open them.

