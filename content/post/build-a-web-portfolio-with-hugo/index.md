---
title: "Web Lesson 1: Build a web portfolio with Hugo"
subtitle: &subtitle Build a web portfolio based on the Hugo Academic theme.
summary: *subtitle

authors: [blake]
date: "2020-11-16T00:00:00Z"
categories: [Web Lessons]
---


## 1. Introduction

This is a Gist, hosted on <https://gist.github.com>. This guide is written in Markdown, a simple language that facilitates formatting with paragraphs, headers, bulleted lists, tables, equations, links, and images without needing to type raw HTML. This file is automatically rendered in the GitHub Flavored Markdown (GFM) specification, which makes it look pretty. If you click the "Raw" button at the top-right, you will see how this file was originally typed.

Why is this important? Well, we want to be able to build a simple website without having to learn HTML, CSS, and JavaScript. A simple site, like a portfolio or blog, is considered "static". This is contrasted with "dynamic" sites like storefronts, social media, and web apps. We will use Hugo, a "static site builder", to build our website. Hugo takes a series of folders and Markdown files and renders it into a website according to a theme that you select.

This guide will walk you through the various bits of software you need to accomplish this task on your own computer. Some of the specifics of this guide are Windows-oriented, but each step can be performed on Mac or Linux as well with minor modification. We will go through setup first, then we will clone this very Gist and open it in VSCode, and finally we will make a local build of an example site with Hugo.

## 2. Setup

### 2.1. Install PowerShell 7

Navigate to the [PowerShell releases] page and click to download the latest version for your system. At the time of writing, `PowerShell-7.1.0-win-x64.msi` was the latest for 64-bit Windows. Run the installer to install. I don't recall all of the installation options, but in general enable any "context menu" options, and don't worry about the "remoting" option.

<!--! links -->
[PowerShell releases]: https://github.com/PowerShell/PowerShell/releases

### 2.2. Set up VSCode

[Download and install VSCode]. During the installation, enabling the "context menu" option will let you right-click on folders to open them in VSCode.

Once VSCode is installed, open it. Press **Ctrl+,** (that's a comma) to open Settings, then click ![settings] on the right side of the tab bar to **Open Settings (JSON)**. Paste the contents of [settings.json] *from this Gist* (between the `SNIPs`) to *your* `settings.json` and press **Ctrl+S** to save the file. Then you can close it if you wish. The settings will use PowerShell 7 as your default terminal and soft-wrap `*.md` (Markdown) files for when we start looking at Markdown files a bit later.

**Ctrl+,** is one of the first keyboard shortcuts you should know in VSCode. And you should also become comfortable with editing your `settings.json` directly. You can also edit settings in the helpful GUI, but it just puts keys in your JSON file in the order that you modified them, making a mess. You really want to organize your `settings.json` with comments (the lines with `\\`) so that you remember why you made certain changes.

<!--! links -->
[Download and install VSCode]: https://code.visualstudio.com/
[settings]: https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/settings.png
[settings.json]: https://gist.github.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94#file-settings-json

### 2.3. Install Git

[Download and install git]. Choose the following configuration options when installing on Windows. You may deviate from these options if you know what you're doing, this is just how I have configured my Git installation.

- Select components
  - Windows Explorer integration
    - Git Bash Here
    - Git GUI Here
  - Git LFS
  - Associate .git* configuration files with the default text editor
  - Associate .sh files to be run with bash
  - Check daily for Git for Windows updates
- Choosing the default editor used by Git
  - Use Visual Studio Code as Git's default editor
- Adjusting the name of the initial branch in new repositories
  - Override the default branch name for new repositories
    - main
- Adjusting your PATH environment
  - Git from the command line and also from 3rd-party software
- Choosing HTTPS transport backend
  - Use the OpenSSL library
- Configuring the line ending conversions
  - Checkout Windows-style, commit Unix-style line endings
- Configuring the terminal emulator to use with Git Bash
  - Use Windows' default console window
- Choose the default behavior of `git pull`
  - Default (fast-forward or merge)
- Choose a credential helper
  - Git Credential Manager Core
- Configuring extra options
  - Enable file system caching
- Configuring experimental options
  - *Don't select anything here.*

<!--! links -->
[Download and install git]: https://git-scm.com/downloads

## 3. Preview Markdown in VSCode

### 3.1. Clone this Gist

Let's practice using git and VSCode together to preview Markdown content. Copy the link in the box when **Clone via HTTPS** is selected.

![clone](https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/clone.png)

Now, open VSCode and bring up the Command Palette with **Ctrl+Shift+P**. This is another keyboard shortcut you should learn, since almost *anything* that you can do in VSCode can be done from this dialog. In this case, we're looking for the **Git: Clone** command. You can just start typing **clone** and the command should be the first one you see. Press **Enter** to select the  command, then **Ctrl+V** to paste in the link you just copied and press **Enter** again.

{{% callout note %}}
If you are getting errors like "command not found", or you don't have **Git: Clone** in your VSCode Command Palette, you may need to reboot before continuing.
{{% /callout %}}

Select `Desktop` in the next dialog. A folder named `064a7e2891e7f9398e6db28fa872ee94`, containing a clone of this Gist, will appear on your `Desktop`. When prompted whether you would like to open the repository, click **Open**. If you miss your chance to click this notification, you can just **right-click** on the folder and select **Open with Code**. If you don't have the context menu entry to **Open with Code**, you can also use **File > Open Folder** in any VSCode window.

![open](https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/open.png)

### 3.2. Preview Markdown

You should now see the source for the very guide you are reading in the VSCode **Explorer** (**Ctrl+Shift+E** or click on the two-pages icon in the sidebar). The file is titled `$ Build a web portfolio with Hugo.md` (the `$` is a trick to get this file to appear at the top of the Gist). Click on `$ Build a web portfolio with Hugo.md` to open it. Then, click ![preview] in the right side of the tab bar to preview it.

Try typing somewhere in the file, and see how the preview changes simultaneously. This is essentially how you will generate content for your website. The raw file is just plain text, but certain symbols have special meaning. You can review the [Markdown Guide] (the [Cheat Sheet] is especially handy) to learn Markdown syntax.

<!--! links -->
[Markdown Guide]: https://www.markdownguide.org/
[Cheat Sheet]: https://www.markdownguide.org/cheat-sheet/

### 3.3. Install Extensions

Keep the Markdown preview visible. Now, install the following extensions by clicking on the links *from within the VSCode Markdown preview*. That's because they don't link properly in <https://gist.github.com>, due to variation in Markdown flavors mentioned earlier.

- [Markdown All in One](vscode:extension/yzhang.markdown-all-in-one)
- [markdownlint](vscode:extension/DavidAnson.vscode-markdownlint)
- [Markdown+Math](vscode:extension/goessner.mdmath)
- [Markdown Preview Github Styling](vscode:extension/bierner.markdown-preview-github-styles)

Notice how the Markdown preview changed to more accurately reflect how it looks on GitHub? This was from the last extension we installed. You can always disable that extension (from the Extensions sidebar tab) if you want to get back the default preview. If any of the extensions has a "Reload" prompt after installing, you may click it to reload the instance of VSCode.

<!--! links -->
[preview]: https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/preview.png

## 4. Build a website with Hugo

### 4.1. Set up Hugo Extended

Download the latest release of [Hugo Extended] for your system. We want the *Extended* version so that we can use more advanced templates like Hugo Academic. At the time of writing, the latest release was `hugo_extended_0.78.2_Windows-64bit.zip`. If you get a warning that this file is not commonly downloaded, bypass it by opting to **Keep** the file.

{{% callout note %}}
You can type `%USERPROFILE%` (with the `%` symbols) directly into the Start menu search, or Windows Explorer, to jump to your `C:\Users\You` folder. It's an environment variable that points to that folder on any Windows machine, regardless of the user folder name. We will use it to make it easier to modify environment variables.
{{% /callout %}}

Extract the contents to `%USERPROFILE%\Hugo\bin` (creating intermediate folders if necessary) and add it to the user's `Path` environment variable. You can do this by pressing **Start/Windows** and starting to type "environment", click on "Edit the system environment variables", click "Environment Variables", then select "Path" in the top half of the dialog and click "Edit", then click "New" and enter `%USERPROFILE%\Hugo\bin`. The following image illustrates this process.

![environment](https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/environment.png)

You can update Hugo by periodically downloading the latest *Extended* release and replacing the contents of your `%USERPROFILE%\Hugo\bin` folder with the new release.

<!--! links -->
[Hugo Extended]: https://github.com/gohugoio/hugo/releases

### 4.2. Set up Go

[Download and install Go]. You can accept the default options during installation. The installer should automatically add the appropriate entry to the `Path` environment variable. By the way, you will often see **Go** referred to as **Golang**, as in "The *Go* programming *language*", which is a slightly more search-engine friendly term. You can update Go by periodically downloading the latest version and running the installer.

<!--! links -->
[Download and install Go]: https://golang.org/doc/install

### 4.3. Build a local preview with Hugo

We're going to be using the [Hugo Academic theme]. We can *clone* this repo to our `Desktop`, much like we previously did with the Gist. Copy the link when **HTTPS** is selected in the **Clone** dialog.

![clone2](https://gist.githubusercontent.com/blakeNaccarato/064a7e2891e7f9398e6db28fa872ee94/raw/44ccf6defd76a4b1641cb90e5cc464ad0b181cd1/clone2.png)

Now, open VSCode and find **Git: Clone** in the Command Palette (remember the keyboard shortcut?). Paste the link into the dialog and press **Enter**. We *don't* have to open it in VSCode this time. Instead, let's open the folder in Windows Explorer. Select the `exampleSite` subfolder and **Ctrl+C** to copy it. Then **Ctrl+V** to paste it in `%USERPROFILE%\Hugo\sites`, creating the `sites` folder if necessary.

Now we can **right-click** on the `exampleSite` folder we just pasted and click **Open with Code**. VSCode shows us the folder structure of our example website. The VSCode terminal appears on the bottom half of the screen. If the terminal isn't already open, let's toggle it by pressing **Ctrl+\`** (that's a "backtick", on the same key as the "tilde" or ~). The terminal allows us to command the computer to do things with the utilities we have installed. Let's type the following and press **Enter**.

```PowerShell
hugo server
```

This will install the required Go modules and build your website locally. You can preview your website by navigating to <http://localhost:1313/> in your web browser. If this step fails, try running `hugo mod clean` before `hugo server`. This is a locally-hosted preview of your website.

<!--! links -->
[Hugo Academic theme]: https://github.com/wowchemy/starter-academic

### 4.4. Modify the example website

You can actively modify files in VSCode, and the website should automatically refresh to reflect your changes. For example, try searching for content you see on the website in the VSCode folder structure. Scroll to the Biography section in your browser. Press **Ctrl+Shift+F** or click the magnifying glass in the sidebar, then search for "Nelson Bighetti is a professor of artificial intelligence". Click on the search result. You should arrive at `content\authors\admin\_index.md`, a Markdown file that informs this portion of the website. Modify the paragraph, then check the <http://localhost:1313/> tab in your browser. The browser preview will automatically update after you press **Ctrl+S** to save the file.

Also in this folder is settings like `title`, `interests`, and `education`. Changing any of these will change the respective section on the website. This is Hugo's way of representing [Front Matter], in this case in YAML format. It allows you to enter information that will be specially handled by whatever template you're using.

Now, press **Ctrl+Shift+E** to navigate to VSCode **Explorer** and look at the folder structure. Here is the result of running `tree content` in the terminal (annotated).

```PowerShell
exampleSite\content
├───authors       # the authors of this website
├───courses       # populates "Courses"
├───home          # populates the front page with widgets sorted by the "weight" setting
├───post          # populates "Posts"
├───project       # populates "Projects"
├───publication   # populates "Publications"
├───slides        # Markdown-based slideshows, linked to posts/projects
└───talk          # populates "Recent & Upcoming Talks"
```

You can navigate the site while walking through folders and files in VSCode to familiarize yourself with the layout. This example can be particularly overwhelming, since it includes a little bit of *everything*. Play around with the content, using **Ctrl+Shift+F** to find strings of text from the website and see where they are in the folder structure. Modify things in the template and see how the website changes. Also, you can use the [Wowchemy Academic theme documentation] to learn about all the features of the template.

<!--! links -->
[Front Matter]: https://gohugo.io/content-management/front-matter/
[Wowchemy Academic theme documentation]: https://wowchemy.com/docs/page-builder/

## 5. Conclusion

~working~
