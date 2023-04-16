---
title: "Useful Git Commands You Should Know 🎢"
datePublished: Sat Apr 15 2023 22:17:07 GMT+0000 (Coordinated Universal Time)
cuid: clgijgah600000amo2cf9erhh
slug: useful-git-commands-you-should-know
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/0d65bbbfd1adb037358473b009e38824.jpeg
tags: tutorial, github, opensource

---

Git and GitHub play a vital role in every developer's life. If you are tech enthusiastic and want to grow in your career, then you must be familiar with Git commands.  
Today in this blog I will be talking about some useful git commands every developer should know. So without wasting any time let's get started.

* **git status:** git status commands let you see the status of all the changes you made. Which files are staged, which aren't and which are not tracked by git yet everything can be viewed by this command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681592645601/398e3992-b556-46bd-89fd-29ab9b926195.png align="center")
    
    As you can see with the git status command I can see index1.js file is not added to staged yet. We will add it there with the next command
    
* **git add:** *git add* command adds new or changed files in your working directory to the Git staging area.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681592748622/52f61f11-7256-4886-b5a5-5020d932a59c.png align="center")
    

Here I created two files index1.js and index1.js but added only index1.js. So you can see only index1.js is staged and ready to be pushed.

* **git clone:** It helps you to download a local copy of any git repository through the command line.
    
* **git checkout:** In github you have to work with many branches. git checkout command helps you to switch between different branches. Also, you can create and switch to a new branch with only one command `git checkout -b newBranch`
    
* **git commit:** git commit is adding a specific commit message with every commit you made. It will help you and other fellow developers to understand what was the specific commit for.
    
* **git commit --amend:** It will help you to edit your last commit message and replace it with a new one.
    
    `git commit --amend -m "New Commit Message"`
    
* **git log:** git log will help you to see the history of every commit ever made ( `git log`)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681593260508/e28a76d1-7b9f-4fab-a3a7-fe36df2567f2.png align="center")
    

Here I first added index1.js file then index2.js file, and then removed index2.js file. So you can see every log is there. Also, you can see a long string those are committed hash which can identify each commit uniquely. If you want to modify a specific commit in future you can do that by mentioning the commit hash. You can also see all the logs in one line using this `git log --oneline` command

* **git stash:** Assume you are working on a specific task and you have to switch back to a different one. You can't switch as it will mess up the current changes. so you want to move aside whatever changes you did to a separate place, work on the other changes and then came back and start working on the previous changes. One thing you can do is commit your current changes and then switch branches and work on other changes. That will be a bad practice as it will mess up git history.  
    so here git stash will help you. It will stash all your current changes with `git stash` command, now you can work on new changes and if you need your old changes back just do `git stash pop`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681594338167/779ffd6e-fad8-4a7a-8bbf-578ad71f51b6.png align="center")

* **git rebase:** This command helps you to modify any changes which were committed earlier.  
    You can put a specific commit hash like `git rebase -i caewe23d` or rebase last 4 commits like `git rebase -i HEAD~4`. Here -i stands for interactive mode.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681595471108/23fba114-d900-49f1-9840-9a9446c10b80.png align="center")
    
    Here in the below image, you can see I have dropped this specific 476c7f5 commit. It removed all the changes done in that specific commit.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681595575306/a325c5b5-b7b4-4180-8387-9c11f6d32c06.png align="center")
    

There are many commands in rebase mode like you can pick, drop, edit, squash with previous commit and many more.

* **git pull:** When you are working with many developers on a specific branch you want your local to be updated with the latest changes. You can do that by git pull command. It will fetch all the changes from remote to your local.
    
* **git push:** This command helps you to upload all the content in the local repository to the remote repository, so other developers also can see the changes.
    

I hope you enjoyed reading this and learnt something new. Hoping to bring more useful content in future.

  
If you enjoyed this article you can support me by [**buying me a coffee**](https://www.buymeacoffee.com/rijusougata13) and following me on [**twitter**](https://twitter.com/rijusougata13) **🤩**