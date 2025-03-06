# Static Site Resume

Statement of Purpose

?

## Prerequisites

1. Install Hugo using the following command:
```
winget install Hugo.Hugo.Extended
```
You can verify that Hugo installed correctly using the following command:
```
hugo version
```
2. Install Git using [this link](https://git-scm.com/downloads/win) and clicking "Click here to download"
3. Create a [GitHub](https://github.com/) account
4. Create a resume
5. Optional: [GitHub Desktop](https://github.com/apps/desktop) provides a graphical user interface for working with Git. This guide will use the command line to interact with Git, but GitHub Desktop, or any other UI for Git, could be used in place of any Git commands found in this guide.

## How to Setup a Static Site to Host your Resume

### Create your Resume in Markdown

To host your resume online, it will be best to write it in Markdown. This section provides information about how to do this.

1. Convert your resume into a Markdown (`.md`) file
   - You can use GitHub's guide to writing [found here](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax), the Markdown guide in the [Further Resources](#further-resources), or any other online Markdown tutorial for information on how to write with Markdown.

> [!NOTE]
> According to Etter, lightweight markup languages such as Markdown are the best way to write documentation because they are human-readable, easy to learn, and easy to version control, all of which are important qualities of documentation. For these reasons, and because Markdown is the most widely used markup language, we will be using Markdown in this guide.

### Creating the Site

1. Run the following commands one-by-one to create a new site using Hugo, replacing `<PROJECT NAME>` with what you want to name the directory for the site:
   - Create the directory for the project:
     ```
     hugo new site <PROJECT NAME> --format yaml
     ```
   - Move into the directory:
     ```
     cd <PROJECT NAME>
     ```
   - Initialize the project with Git:
     ```
     git init
     ```
2. Get the PaperMod theme for your site:
   - Run the following command in your site's directory to download the theme into your project:
     ```
     git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
     ```
   - Open the `config.yml` file and add the following text to the end of it to use the new theme:
     ```
     theme: ["PaperMod"]
     ```
   - Optional: Change the mode of the site's home page by adding the following text to the end of `config.yml`:
     ```
     params:
       homeInfoParams:
         Title: "Hello there \U0001F44B"
         Content: Welcome to my statically generated site
     ```
3. Run the following command to start running the site on your computer. It does not have content yet, but this will confirm everything has worked so far:
```
hugo server
```
4. Create a new page for the site
   - Run the following command to create the page:
     ```
     hugo new content content/posts/resume.md
     ```
   - Open the file in your text editor of choice and paste the following text, replacing `<RESUME>` with the copy-pasted contents of your Markdown-formatted resume that you wrote earlier:
     ```
     ---
     date: "2025-03-04T19:10:05-06:00"
     draft: false
     title: "Resume"
     ---
     <RESUME>
     ```
5. Commit your changes:
   - Prepare your changes to be committed:
     ```
     git add -A
     ```
   - Make the commit:
     ```
     git commit -m "Create Site"
     ```
> [!NOTE]
> According to Etter, technical writing be stored in a distributed verson control system, like Git. This is not only for the common reasons, such as backups and offline work, but also because they are what developers prefer, and using the tools developers are comfortable with is important in getting them to contribute to the documentation.

### Publishing the Site

The site has been made, but it is not accessible anywhere. The next few steps will explain how to use GitHub Pages to publish your static site.

1. Create a new public GitHub repository and follow the instructions it provides to link it with your site's repository
2. ?
3. Use the following commands to create and open a new file that will hold the GitHub Action workflow for publishing the site:
```
mkdir -p .github/workflows
notepad .github/workflows/hugo.yaml
```
4. Go to [this repo's GitHub Action](https://github.com/BrettLoewen/Comp-2600-A2/blob/main/.github/workflows/hugo.yaml) and paste the contents into your new file
5. Commit your changes and push them to GitHub
6. Go to your repository's Actions using the top menu bar and you should see a running workflow. When it completes (turns green), you can click into it and see a link to your published site. From now on, whenever you push a change to GitHub, the changes will automatically deploy

### Write a README

The project is done and the website is live, congratulations. But before you move on, you should document what you've done. This section will quickly walk you through creating a README, like this one, for your project.

1. 

## Further Resources
- [Hugo](https://gohugo.io/)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)
- Learn Git
- Learn GitHub
- Learn GitHub Pages
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)

## FAQs

- Change theme
- Draft
- New file
- Clone repo

## Credits

- Written by: Brett Loewen
- Reviewed by: Tomi Bickersteth
- PaperMod theme by: [Aditya Telange](https://github.com/adityatelange/)
