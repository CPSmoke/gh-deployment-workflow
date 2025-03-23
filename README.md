# gh-deployment-workflow
https://roadmap.sh/projects/github-actions-deployment-workflow

This repository contains a simple website using GitHub Pages and GitHub Actions. 
The site displays the message "Hello, GitHub Actions!".

Step 1: Create a Repository
Create a repository named gh-deployment-workflow on GitHub.

Create a file index.html with the following content:

    <!DOCTYPE html>
    <html lang="ru">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Hello, GitHub Actions!</title>
    </head>
    <body>
        <h1>Hello, GitHub Actions!</h1>
    </body>
    </html>
    
Create a file README.md with a brief description of the project.

Step 2: Install Hugo
For Windows:

    winget install Hugo.Hugo.Extended
    
For Linux:

    sudo apt install hugo
    
Step 3: Set Up Hugo
Make sure Hugo is installed on your local machine. You can follow the instructions on the official Hugo website.

Create a new Hugo project inside your repository:

    hugo new site .
    
Copy index.html into the layouts/_default/ folder of your Hugo project. This will make it the main page.

Step 4: Create a GitHub Actions Workflow
Create a directory .github/workflows.

Create a file deploy.yml in this directory with the following content:

    name: Deploy to GitHub Pages
    
    on:
      push:
        branches:
          - main
        paths:
          - index.html
    
    jobs:
      build:
        runs-on: ubuntu-latest
    
        steps:
        - name: Checkout repository
          uses: actions/checkout@v2
    
        - name: Setup Hugo
          uses: peaceiris/hugo-actions/setup-hugo@v2
          with:
            hugo-version: 'latest'
    
        - name: Build
          run: hugo
    
        - name: Deploy to GitHub Pages
          uses: peaceiris/actions-gh-pages@v3
          with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_dir: ./public
Step 5: Set Up GitHub Pages
Go to the settings of your repository on GitHub.
Scroll down to the GitHub Pages section.
In the Source section, select the gh-pages branch for publication.

Step 6: Running
Now, every time you make changes to index.html and push them to the main branch, the workflow will be triggered, rebuilding the site with Hugo and deploying it to GitHub Pages!

https://CPSmoke.github.io/gh-deployment-workflow/

