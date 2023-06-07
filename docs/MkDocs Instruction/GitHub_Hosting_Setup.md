# Set up Doc Site on GitHub

## Load Doc Site To Repo

1. **Create a GitHub repository**:  
	If you don't have one already, create a new GitHub repository. This will be the place where you'll store all the files for your MkDocs site.
    
2. **Initialize your MkDocs project**:  
	If you have not done so already, you'll need to initialize a new MkDocs project in your local directory. You can do this with the command `mkdocs new [project name]`. This will create a new directory with the necessary files to start a new MkDocs project.

3. **Push your MkDocs project to GitHub**:  
	Once your MkDocs project is set up, you can push it to your GitHub repository. You can do this by navigating to your project directory and using the following commands:

	```bash
	git init
	git add .
	git commit -m "First commit"
	git branch -M main
	git remote add origin https://github.com/yourusername/[repo name].git
	git push -u origin main
	```

This command will build your site, create (or update) the gh-pages branch in your local repository, copy the built site to this branch, and then push the branch to GitHub.

## Create Doc Site Page

1. **Build your site and push it to the gh-pages branch**:  
	By default, GitHub Pages uses a branch named gh-pages in your repository to serve the website. You'll need to build your MkDocs site and push the built site to this branch. MkDocs comes with a built-in deployment command for this. In your project directory, use the following command:

	```bash
	mkdocs gh-deploy
	```

	This command will build your site, create (or update) the gh-pages branch in your local repository, copy the built site to this branch, and then push the branch to GitHub.

2. **View your site**:  
	After you've pushed your site to the gh-pages branch, it should be available at `https://[username].github.io/[repo name]/`. Replace "yourusername" and "yourrepository" with your GitHub username and the name of your repository respectively.