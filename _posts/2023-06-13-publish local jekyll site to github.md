---
layout: post
title: Publish Local Jekyll Site to Github
subtitle: A guide to create a Github repository and publish to web.
tags: [github]
---
A guide to create a Github repository and publish to web.

1. **Create a new repository on GitHub:**

   + Sign in to your GitHub account and click on the "+" icon in the top-right corner of the page.
   + Select "New repository" from the dropdown menu.
   + Choose a repository name and optionally provide a description.
   - Make sure the repository is set to "Public" or "Private" based on your preference.
   - Click on the "Create repository" button.  
<br>
2. **Initialize Git in your Jekyll project:**

   - Open a terminal or command prompt.
   - Navigate to the root directory of your Jekyll project.
   - Run the following command to initialize Git:

     ```bash
     git init
     ```  
<br>
3. **Add the remote repository:**

   - Go to the GitHub repository page you created in step 1.
   - Copy the repository's remote URL.
   - In the terminal or command prompt, run the following command to add the remote repository:

     ```bash
     git remote add origin <remote_url>
     ```

     Replace `<remote_url>` with the URL you copied.
<br>
4. **Build your Jekyll site:**

   - In the terminal or command prompt, navigate to the root directory of your Jekyll project if you're not already there.
   - Run the following command to build your Jekyll site:

     ```bash
     bundle exec jekyll build
     ```
<br>
5. **Commit and push your Jekyll site to GitHub:**

   - Run the following command to stage all the changes:

     ```bash
     git add .
     ```
<br>
   - Commit the changes with a descriptive message:

     ```bash
     git commit -m "Initial commit"
     ```
<br>
   - Push the changes to the remote repository:

     ```bash
     git push -u origin master
     ```
<br>
6. **Enable GitHub Pages:**

   - Go to your GitHub repository page.
   - Click on the "Settings" tab.
   - Scroll down to the "GitHub Pages" section.
   - In the "Source" dropdown, select "master branch" or "main branch" based on your repository's default branch.
   - Click on the "Save" button.  
<br>
7. **Access your published Jekyll site:**

   - After enabling GitHub Pages, you will see a message with the URL where your Jekyll site is published.
   - Visit that URL in your web browser to see your Jekyll site live.

Please note that the instructions assume you have Git and Jekyll properly installed on your computer. Additionally, if you encounter any errors or issues during the process, feel free to ask for further assistance.