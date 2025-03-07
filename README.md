# Static Site Resume

## Statement of Purpose

This document describes the process of creating a static site using Markdown, Hugo, and GitHub Pages. It is directed at people who want a simple strategy to upload documents to the internet, primarily for the purpose of presenting documentation, though the process is not limited to only documentation. This guide expects readers to have a basic understanding of the command line and to be using Windows 10 or later.

## Prerequisites

1. Install Hugo using the following command:
```
winget install Hugo.Hugo.Extended
```
You can verify that Hugo installed correctly using the following command:
```
hugo version
```
2. Install [Git](https://git-scm.com/downloads/win)
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

To host your resume online, this guide will walk you through using the static site generator Hugo. This section covers creating the site's project on your computer and the following section will cover publishing the site.

> [!NOTE]
> According to Etter, documentation should be hosted on a website to avoid it getting outdated or ignored. To do this, he reccommends static sites, and using tools to generate them, because they are a simple and effective way to host content.

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
     git commit -m "Create site"
     ```
> [!NOTE]
> According to Etter, technical writing should be stored in a distributed verson control system, like Git. This is not only for the common reasons, such as backups and offline work, but also because they are what developers prefer, and using the tools developers are comfortable with is important in getting them to contribute to the documentation.

### Publishing the Site

The site has been made, but it is not accessible anywhere. The next few steps will explain how to use GitHub Pages to publish your static site.

1. Create a new public GitHub repository and follow the instructions it provides to link it with your site's repository
   - Additional information on this topic can be found in the [Further Resources](#further-resources) under Adding locally hosted code to GitHub if needed
2. Use the following commands to create and open a new file that will hold the GitHub Action workflow for publishing the site:
   - Create a new folder:
     ```
     mkdir -p .github/workflows
     ```
   - Create a new file `hugo.yaml` which will hold instructions for publishing the site:
     ```
     notepad .github/workflows/hugo.yaml
     ```
3. Go to [this repo's GitHub Action](https://github.com/BrettLoewen/Comp-2600-A2/blob/main/.github/workflows/hugo.yaml) file and paste the contents into `hugo.yaml`
4. Optional: configure your site:
   - Modify the `baseURL` and `title` values in the project's `config.yml` to match your production URL and your intended site title. The production URL can be easily found after step 6 when the site is published
5. Commit your changes and push them to GitHub:
   - Prepare your changes to be committed:
     ```
     git add -A
     ```
   - Make the commit:
     ```
     git commit -m "Add publishing workflow"
     ```
   - Push the commit to GitHub:
     ```
     git push
     ```
6. Go to your repository's Actions using the top menu bar and you should see a running workflow. When it completes, indidcated by it turning green, you can click into it and see a link to your published site. From now on, whenever you push a change to GitHub, the changes will automatically deploy

### Write a README

The project is done and the website is live, congratulations! But before you move on, you should document what you've done. This section will quickly walk you through creating a README, like this one, for your project.

1. Create a new file named `README.md` in the root directory of the project:
```
notepad README.md
```
2. Open and write your README, following the example of a-good-readme-template found in the [Further Resources](#further-resources) section

> [!NOTE]
> According to Etter, a README should summarize the project and provide instructions on how to use it. Good candidates for documentation would be its dependencies, like Hugo, how to run the site locally, using `huso server`, and the GitHub Action workflow created above that publishes the site.

3. Push the changes to GitHub like you did earlier

## Conclusion

And you're done! You wrote a resume using Markdown, created a static site using Hugo, version controlled the project using GitHub, published the site using GitHub Pages, and wrote a README for your project.

## Further Resources
- [Hugo](https://gohugo.io/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [Learn Git](https://www.atlassian.com/git/tutorials)
- [Learn GitHub](https://docs.github.com/en/get-started/start-your-journey/hello-world)
- [Learn GitHub Pages](https://docs.github.com/en/pages/quickstart)
- [Adding locally hosted code to GitHub](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github)
- [a-good-readme-template](https://github.com/PurpleBooth/a-good-readme-template)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)

## FAQs

Q. Can I use a different theme?
A. Yes, you can browse many themes on [Hugo's website](https://themes.gohugo.io/), pick the one you like, and follow its install instructions.

Q. Can I write posts in the project but keep them private until I'm ready?
A. Yes, replace `draft: false` with `draft: true` in your post's header and it will not appear in builds. You can also use the commands `hugo server --buildDrafts` or `hugo server -D` to run the site locally and include drafts if you want to preview what a post looks like before publishing it.

Q. Do I have to use `hugo new content content/posts/<FILE NAME>.md` to make new posts?
A. 

Q. Do I have to create and link a repository from GitHub
A. 


## Credits

- Written by: Brett Loewen
- Reviewed by: Tomi Bickersteth
- PaperMod theme by: [Aditya Telange](https://github.com/adityatelange/)
