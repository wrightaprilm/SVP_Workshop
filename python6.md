## Version Control and Sharing Code

So, how many of you tried to fix a borken bit of code and made it worse in the process today? Or erased something important and didn't notice until later?

Enter version control.

Version control is a system of tracking changes made to documents. So, for example, if you write some code in a document and enter it into a version control system, you can manage future edits of that code. Obviously, this is quite handy. If your code is working, and you later make a change to it that causes it to malfunction, you can roll back to a previous change. You can also write and track different versions of the code for experimental development.

There are many different types of version control. Today, we're going to talk about git. Git has become quite popular, due in no small amount to the website GitHub, which has very nice features for information sharing and collaborative coding.

Some of this might be a little challenging without Wi-Fi. Use this as a cheatsheet later on, if you choose to use git for managing your data and code.

In your terminal, if you are still in Python, exit from Python. Before you do this, copy your most recent bit of code from your terminal into a text editor window. Save it as "my_code.py".

First create a new folder, if you haven't already created one for this workshop.

```UNIX
$ mkdir SVP_workshop
```

Move your my_code.py file into the directory:

```UNIX
$ mv my_code.py SVP_workshop/
```

And change directories into your SVP directory:

```UNIX
$ cd SVP_workshop
```

Recall that you can always check where you are in the computer by typing

```UNIX
$ pwd
```

In git, we store our code (or other documents, this is great for manuscripts!) in what we call a 'repository'. A repository will hold all of our code snapshots and all of our other documents. But we want this to be linked to us and our name. So let's make sure git knows who we are:

```UNIX
$ git config --global user.name "Your Name"
$ git config --global user.email "your@e-mail.edu"
$ git config --list
$ git config user.name
```
Now that git knows who we are, we can initialize a repository. 

```UNIX
$ git init
```

This will start a new repository. This should only be used once per project, and git repositories should not be nested within each other. Let's see the status of our repository:

```UNIX
$ git status
```

For you, this should reflect that you have your my_code.py file, and that it is not being tracked - i.e., it is not being version controlled right now. When coding, checking the status of your repository often is good practice.

Let's add our code to the repository - after all, we'd be bummed out if it got messed up somehow, right?

```python
$ git add my_code.py
```

Once added, we can commit our code into git's memory like so:

```UNIX
$ git commit -m 'my awesome script'
```

The -m option allows us to add a 'commit message'. These are very useful for recalling later on, what exactly you added to your repositories and when. They're also helpful for your collaborators to snoop on what all you've been doing (or, to, you know, collaboratively write code).

One of the most useful facets of version control is branching. Let's say you're working on some code to solve complex equations. You want to program in a new equation that takes the output of the another equation and uses to calculate some new values. But you're worried that the code you have planned might cause existing functionality to break. You might want to put this on a separate branch, so that if you do mess up, the mistake are isolated on a separate branch.

```UNIX
$ git branch experimental
$ git checkout experimental
```

This creates a branch called experimental and moves you over onto that branch. You can now make commits along this branch that won't affect the other branch.

To get back onto the other branch:

```UNIX
$ git checkout master
```

OK, so let's say you've been working a bit. Making modifications, coding up a storm. 

```UNIX 
$ git log
```

Git log allows you to see the previous changes you've made to a repository. Want to know when you added that loop? Check your log.

##Sharing code online

This is the part of the hour that we're going to have trouble with without the internet.

GitHub.com allows users to broadcast code to the internet. This can be really useful for sharing information with collaborators and maintaining long-standing versions of your code for others to use.

If you register on GitHub and create a new repository, you can link that to your current repository:

```UNIX

$ git remote add online_repo url/of/repo
```

Once we have a connection between our local an online repos, we can put our code online via a push:

```UNIX
$ git push
``` 

In the simplest version, we can just push to our repository. If we have multiple branches, we may want to push them separately.

```UNIX
$ git push online_repo master
```

For example, pushes all the changes on our master branch to our online repository.

## So my code is on the internet ... 

Yep. It's kind of scary to share code at first. But there are lots of good reasons to do it.

+ Your code is discoverable: People can find you, see the code, and cite the paper to which it is connected!
+ It's open: Science thrives on reproducibility. If your code lives online, people can do science with your work.
+ It's convenient: If I'm without my computer, but want to chat code with someone, I can pull up GitHub on their computer and show them stuff.
+ It's permanent (hopefully)




