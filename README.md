# deploy-a-streamlit-app-on-streamlit
yet another streamlit deployment on streamlit!

**Caution: rename branch from main to master to have a clean url**



## Extra Infos for Streamlit

- If your app has name streamlit_app.py and your branch is master, your app is also given a shortened URL of the form `https://share.streamlit.io/[user_name]/[repo_name]`e.g `https://github.com/bflaven/deploy-a-streamlit-app-on-streamlit`. The only time you need the full URL is when you deployed multiple apps from the same repo. So you can also reach the example URL above at the short URL `https://share.streamlit.io/bflaven/deploy-a-streamlit-app-on-streamlit`

- The default branch is considered the "base" branch in your repository, against which all pull requests and code commits are automatically made, unless you specify a different branch.

- Source: [https://docs.streamlit.io/streamlit-cloud/community](https://docs.streamlit.io/streamlit-cloud/community)


## How-to deploy to Streamlit

**It requires few requirements before starting to deploy both on Heroku or on Streamlit:**

- Install Homebrew locally and make it accessible through the Mac console (Free) at [https://brew.sh/](https://brew.sh/)
- Install Git locally and make it accessible through the Mac console (Free) at [https://git-scm.com/download/mac](https://git-scm.com/download/mac)
- Create an account on Github (Free) at [https://github.com/](https://github.com/)
- Create an account on Heroku (Free) at [https://signup.heroku.com/](https://signup.heroku.com/)
- Create an account on Streamlit (Free) at [https://share.streamlit.io/](https://share.streamlit.io/)



### 1. Install Homebrew for Mac

```bash
# It supposed that Homebrew is already installed on your computer. 
# https://brew.sh/
# to launch the Homebrew install, you can run the following command
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# check the install
brew --version


```


### 2. Install Git Using Homebrew

To install Git, we will use Homebrew, the package management system for Mac.

Run the following brew command in the terminal:

```bash
brew install git
# Then, check the Git version to verify the installation:

# to check the git install
git --version
```

### 3. Create your environment with Conda

**Go to the dir**
It is just I found easier to be in same git directory to create my environment with Conda because I know better what are the packages required by the streamlit app.

```bash
# go to your directory
cd /Users/brunoflaven/Documents/03_git/deploy-a-streamlit-app-with-heroku/

```

**Create your dev env with conda**
```bash

# listing the envs
conda info --envs

# create the env for your streamlit app
conda create --name deploy_getting_started python=3.9.7
```

**Get into your dev env**

How to create a development environment and also list and deactivate some dev env.


```bash

# go into the env
conda activate deploy_getting_started


# Let's say you create a environment with this version of python (3.8.3) if you need yo update the python version of your env
# upgrade python version in your env heroku_python_getting_started_3a
conda create --name heroku_python_getting_started_3a python=3.8.3
conda install python=3.9.7

# listing the envs
conda info --envs
conda remove --name heroku_python_getting_started_3b --all


# get from the current env
conda deactivate

```

**Install packages in your dev env**
```bash
# install the packages in the env
pip install streamlit
pip install watchdog
```

**Save python requirements in a file name `requirements.txt`**
```bash
# show what the requirements
pip freeze > requirements_1_heroku_python_getting_started_3.txt
pip freeze > requirements_2_heroku_python_getting_started_3.txt
pip freeze > requirements_3_heroku_python_getting_started_3.txt

# rename the last version with the correct name requirements.txt, heroku only accept the filename requirements.txt
mv requirements_1_heroku_python_getting_started_3.txt requirements.txt

```

**Install other packages in your dev env required by your app**
```bash
pip install pandas
pip install numpy
pip install matplotlib
pip install plotly-express
pip install matplotlib
pip install altair
```

**Extra info for the app**

```bash
# install the packages required to work with the streamlit app
numpy==1.18.4
pandas==1.0.3
seaborn==0.10.1
matplotlib==3.4.2
plotly-express==0.4.1
altair==4.1.0
```


### 4. Deploy to streamlit (tiny-streamlit-dashapp)
The app name is `tiny-streamlit-dashapp`. We will perform 2 actions:

- build your app with streamlit
- update in github.com
- deploy to streamlit

**5.1 Build your app with streamlit**

It does not have to be sophisticated app as for the moment we want to learn how to deploy on platform such as Heroku or Streamlit.

**An advice: grab any simple app on GitHub, create your own Streamlit app or take the one in this directory but stay simple for the moment.**

**5.2 Commit on GitHub with Git**


```bash
# go to your dir
cd /Users/brunoflaven/Documents/03_git/deploy-a-streamlit-app-with-heroku/

# checkout status
git status
# output the changes in files

git branch
# main 

# commit changes example
git add .
git commit -am "update README.md"

# first push to git
git push origin master

```


**5.3 Deploy on streamlit**




**Caution: one thing to remember it is the branch name that you are using to push both on github, heroku**

```bash
# CAUTION depend if your branch on github is master or main

### GITHUB and STREAMLIT
# push to github if your branch on github is master
git push origin master

```

In the file runtime.txt, add the correct version of python you are using.

```
python-3.9.7
```


## Some extra GIT commands

- **how to remove a directory or a subdirectory from a git directory**
```bash
# This deletes from filesystem
git rm -r one-of-the-directories
# Make the commit
git commit . -m "Remove duplicated directory"
# Git push (typically 'master', but not always)
git push origin <your-git-branch> 
```

- **simple example to delete a directory**

```bash
rm -r deploy-a-streamlit-app-with-Heroku
git add .
git commit -m "add deploy-a-streamlit-app-with-Heroku"
git commit -m "add files"
git push
```

- **to add, commit and push**

```bash
git add .
# Adds the file to your local repository and stages it for commit. To unstage a file, use 'git reset HEAD YOUR-FILE'.
```

```bash
git commit -m "Add existing file"
# Commits the tracked changes and prepares them to be pushed to a remote repository. To remove this commit and modify the file, use 'git reset --soft HEAD~1' and commit and add the file again.
```

```bash
git push origin main
# Pushes the changes in your local repository up to the remote repository you specified as the origin
# git push  <REMOTENAME> <BRANCHNAME> 
# git push origin main
```

- **to check the remote branch**
```bash
git branch
# output
# * main
```



# RESSOURCES
- [https://www.jquery-az.com/list-branches-git/](https://www.jquery-az.com/list-branches-git/)

- [https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)

- [https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository](https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository)

- [https://tiny-streamlit-dashapp.herokuapp.com/](https://tiny-streamlit-dashapp.herokuapp.com/)

- [https://www.geeksforgeeks.org/deploy-python-flask-app-on-heroku/](https://www.geeksforgeeks.org/deploy-python-flask-app-on-heroku/)

- [https://pythonforundergradengineers.com/streamlit-app-with-bokeh.html](https://pythonforundergradengineers.com/streamlit-app-with-bokeh.html)

- [https://dash.plotly.com/deployment](https://dash.plotly.com/deployment)

- [https://devcenter.heroku.com/articles/git#deploying-code](https://devcenter.heroku.com/articles/git#deploying-code)

- [https://elements.heroku.com/buildpacks/heroku/heroku-buildpack-python](https://elements.heroku.com/buildpacks/heroku/heroku-buildpack-python)

- [https://github.com/TannerGilbert/Tutorials/tree/master/Streamlit/Deploy-Application-with-Heroku](https://github.com/TannerGilbert/Tutorials/tree/master/Streamlit/Deploy-Application-with-Heroku)





