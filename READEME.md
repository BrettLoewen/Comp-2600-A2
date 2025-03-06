# Static Site Resume

Statement of Purpose

?

## Prereqs

1. Install Hugo using the following command:
```
winget install Hugo.Hugo.Extended
```
You can verify that Hugo installed correctly using the following command:
```
hugo version
```
2. Install Git using [this link](https://git-scm.com/downloads/win) and clicking "Click here to download"
3. Create an [GitHub](https://github.com/) account

## How to Setup a Static Site to Host your Resume

### Create your Resume in Markdown

1. ?

### Creating the Site

1. Run the following commands one-by-one to create a new site using Hugo, replacing `<PROJECT NAME` with what you want to name the directory for the site:
```
hugo new site <PROJECT NAME> --format yaml
cd <PROJECT NAME>
git init
```
2. Get the PaperMod theme for your site:
   - Run the following command in your site's directory:
    ```
    git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
    ```
    - Open the `config.yml` file and add the following text to the end of it:
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
      hugo new content content/posts/my-first-post.md
      ```
    - Open the file in your text editor of choice and paste the following text:
      ```
      ---
      date: "2025-03-04T19:10:05-06:00"
      draft: false
      title: "My First Post"
      ---
      ## Introduction
      
      This is **bold** text, and this is *emphasized* text.
      
      Visit the [Hugo](https://gohugo.io) website!
      ```
5. Commit your changes
```
git add -A
git commit -m "Create site"
```

### Publishing the Site

5. Create a new public GitHub repository and follow the instructions it provides to link it with your site's repository
6. ?
7. Use the following commands to create and open a new file that will hold the GitHub Action workflow for publishing the site:
```
mkdir -p .github/workflows
notepad .github/workflows/hugo.yaml
```
9. Go to [this repo's GitHub Action](https://github.com/BrettLoewen/Comp-2600-A2/blob/main/.github/workflows/hugo.yaml) and paste the contents into your new file
10. Commit your changes and push them to GitHub
11. Go to your repository's Actions using the top menu bar and you should see a running workflow. When it completes (turns green), you can click into it and see a link to your published site. From now on, whenever you push a change to GitHub, the changes will automatically deploy

## Further Resources
- [Hugo](https://gohugo.io/)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)
- ?
- ?

## FAQs

- ?
- ?

## Credits

- Written by: Brett Loewen
- Reviewed by: 
- PaperMod theme by: [Aditya Telange](https://github.com/adityatelange/)
