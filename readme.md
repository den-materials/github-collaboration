<!--
Creator: Brianna Veenstra
Location: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

<!--Actually 11:05 WDI2-->
<!-- 11:06 WDI3 -->
<!--WDI4 11:02 -->

<!--11:15 5 minutes -->

# GitHub Collaboration

<!-- Hook: So now that we have the basics of Git collaboration down, let's talk about the workflow we will be using for Project 3, which is a good approximation of the workflow you will have on a development team.  -->

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

- Git is a powerful tool for collaborating on code.

- GitHub is a popular online service for managing git repositories.

- Using git repositories for collaboration will be important throughout a web developer's career.

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- **Create** their own git branches and explain a pattern for using branches to develop a full application.
- **Make** a new repository and add another developer as a collaborator.
- **Resolve** a merge conflict.

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

* **Use** git to stage and commit changes locally.
* **Explain** what the following terms mean for GitHub: pull, push, fork, clone, pull request.

<!--11:09 WDI3 -->
<!--11:20 5 minutes -->

## Branches

In Git, branches are a part of your everyday development process. When you want to add a new feature or fix a bug — no matter how big or how small — you spawn a new branch to encapsulate your changes. This makes sure that unstable code is never committed to the main code base, and it gives you the chance to clean up your feature’s history before merging it into the main branch.

A branch in git is just a label or pointer to a particular commit in a repository, along with all of its history (parent commits).

What makes a branch special in git, is that we're always on a specific branch, and when we commit, the current branch HEAD moves forward to the new commit. Another way to say that is the HEAD always stays at the tip of the branch.

Terminology: HEAD is simply a reference to the current or most recent commit!

### Q. Why is branching an important part of git?

> A. Branches are useful for many reasons, but some of the most common ones:

 1. To allow experimentation. By switching to a new branch, we can experiment,
 and if the experiment fails, we can delete it and easily switch back to master
 (or another branch of our choice). If it succeeds, we can merge those changes
 into master.
 2. To allow work to proceed on multiple features (or by multiple people) without
 interfering. When a feature is complete, it can be merged back into master.
 3. To allow easy bug fixes on a stable version while features are being developed.

<!--Actually 11:12 WDI2-->
<!--11:13 WDI3 -->
<!--11:11 WDI4 -->

<!--11:25 5 minutes -->

![doc brown](http://www.gamedev.ru/files/images/doc-brown1-git.jpg)

## `git fetch`, `git merge`, and `git pull`

Fetching, merging, and pulling are related commands that you will frequently use to update your local repository to include your collaborator's work.

[`git fetch`](https://git-scm.com/docs/git-fetch) gets all of the updates from the remote repositories without changing the location of the local HEAD.

[`git merge`](https://git-scm.com/docs/git-merge) joins two different places in your development tree. This is frequently used to bring together your changes with the changes you just fetched. If you were on branch `add-auth` and you had just `git fetch`'d updates from the remote, you could then `git merge origin/add-auth`. This would join your changes and the changes that had been made to this branch on origin. You also commonly use merge to pull changes from one branch into another so that your current branch doesn't become out of date while you work.

[`git pull`](https://git-scm.com/docs/git-pull) is the combination of fetching and merging to the newly fetched version of the current branch.

![image](https://cloud.githubusercontent.com/assets/6520345/15020568/663aa804-11d7-11e6-83f6-774e43bc2ea6.png)
<!--WDI4 11:14 -->


<!--11:17 WDI3 -->
<!--11:30 5 minutes -->



## Merge Demo
You're going to role play two people. One person working on master, the other on a branch. We're going to demonstrate a simple `merge` scenario in Git.

1. Make a new directory and `git init` it.
2. `Touch` a new HTML file.
3. Add a code to it.
4. Commit it.
5. Create a new branch, but don't hop over to it yet. You can do a `git branch {branch-name}` to create a branch without hopping over to it.
6. Modify and commit your original code from step 3.
7. Hop over to the branch you created in step 5.
8. Edit the same line of code you added in step 3 and commit it.
9. Do a `git merge master` to merge the most recent commits in master over to your current branch.

> When you have a merge conflict, Git inserts some text in your file where it didn't know how to combine the changes from master with the code you're currently working on. Resolve it, save it, commit it, and move on.

10. Get rid of the `<<<<<HEAD` stuff Git inserts, and figure out the best way to combine your code with the code from master.

11. When you think you're done, test it, manually, via Mocha, whatever your team's protocol is. 
12. Commit it.
13. Hop back over to master and merge in your feature branch.

> WARNING: There are good kinds of newbs and bad kinds. To keep on the good side, avoid putting problems into master. Deal with merge conflicts in your own branch and make sure everything works like a shiny new DeLorean before you allow for a merge into master.


## Collaboration Workflows

There are two main scenarios for collaborating on coding projects:

1. You **fork** another developer's project and make pull requests from *your remote fork* to the *project's remote*.  We will review this workflow later, and it is very common in open-source projects, but we will NOT use this workflow for this project.
2. Another developer makes you a **collaborator** on a project they own, giving you the ability to make pull requests directly from the project's *remote feature branches* to the project's *remote master*. (Note that as a collaborator on a project, you also have the ability to push directly to the master branch, which you should NEVER do.)

![github-collab-diagram](https://cloud.githubusercontent.com/assets/7833470/12072895/69abd404-b0b1-11e5-8d8c-4ff54c13b0a0.png)

**For this next project, you should be collaborators!**

<!--Actually 11:28 when devs reading -->
<!--11:37 to get started on lab -->
<!--WDI3 11:39 to get started on lab, because I decided to model a merge conflict...I think we should add this as its own section -->
<!--WDI4 11:21, 11:26 turning over to devs -->
<!--11:35 45 minutes -->

## Practice: Create and resolve a merge conflict

What happens if two people on a team change the same file?  Merge conflicts (often)!  That might sound like a big deal, but it's easy to handle with your team.  Let's practice resolving a merge conflict.  


1. Pair up. Pick one person to be Partner1 and one to be Partner2 throughout this exercise.
2. Have Partner1 create a brand new repository on GitHub.
2. Partner1 should now create a new project directory locally (don't clone), generate a boilerplate `index.html` file, create a `readme.md` with some content, and push the new app to the remote repository.
4. Partner1 should [add Partner2 as a collaborator](https://help.github.com/articles/adding-collaborators-to-a-personal-repository/)
3. Partner2 (the collaborator) should then clone this repository.
4. Each partner should create and checkout a new feature branch.  (Name them different things, like `better-readme` and `best-readme`.) You can check that you have the new branches with `git branch`-that will print all of the branch names.  Make sure you **do all your work on your own branch**, NOT on `master`.
5. Each person should now change the README significantly, and add 2 elements to `index.html`.  
6. Now, have Partner1 (repo creator) commit and push the work to GitHub on *their* branch. (E.g., `git push origin better-readme`.)  Open a pull request from the new branch to the master branch.
7. Partner2 (the collaborator) should commit their changes and push the work to GitHub on *their* branch. (E.g., `git push origin best-readme`.) Open a pull request from the new branch to the master branch.
8. Accept Partner1 (repo creator)'s pull request first. It shouldn't have any merge conflicts with the master branch, so you can just merge it in on GitHub.
9. The second pull request should be a little more interesting. We hope that we have created at least one merge conflict.  Partner2 (the collaborator) should get the latest code by `pull`ing the latest code from `origin master` (with Partner1's recently pulled-in changes).  Then they should start at step 3 of [this guide for resolving the merge conflict locally](https://github.com/SF-WDI-LABS/shared_modules/blob/master/how-to/github-collaboration-workflow.md#resolving-merge-conflicts-locally)
10. Partner2 should push the fixed version to GitHub.  
11. Finally, go back to the GitHub repository and accept Partner2's pull request (there should not be any merge conflicts any more).
12. Feel free to delete this practice repository from your local machine and from GitHub. This workflow was intentionally sloppy and I'm hoping that you learned a little bit of what *not* to do.

### Bonus

If you have time, try the following:

1. Have Partner1 make yet another change to the `README` file, and push their branch up to GitHub.
2. Open a Pull Request for Partner1's changes.
3. Resolve the conflicts in the Pull Request dialog.
4. Merge the Pull Request into `master`.

<!--WDI4 Folks started talking to their squads between 12 and 12:05 on their own-->
<!--Actually 12:21 WDI2-->
<!--12:07 WDI3 -->

<!--12:20 5 minutes -->

## Talking Points for Teams

1. Set guidelines for merging pull requests before you start. How many people should review the pull requests before they're merged?  What branch should they be merged into? (Consider making a "develop" or "staging" branch to merge into instead of merging into the master branch. Once your app is complete, then you can merge your development branch into the master branch as your first major "release.")

2. Make very descriptive commit messages! The team members who are reading them should be able to tell at a glance what you were working on.

3. Clearly delineate who's working on what, and keep an updated task list. (Trello is great for this!) Things will go much more smoothly if team members work on features that don't overlap. This is especially important if you're not all working in the same physical location. It's quite common for wires to get crossed!

4. Don't have multiple team members working on the same feature branch at one time, on different computers. If you're pair programming with someone, only use one computer to avoid having differing code on the same branch. 

5. When merge conflicts arise, it's up to the individual contributor to resolve them. But work with your team! Follow the steps for [resolving merge conflicts locally](#resolving-merge-conflicts-locally), make sure to delete any merge junk from your code, and then push your cleaned-up branch to GitHub.  

<!--12:25 5 minutes -->

## Resources

* **[WDI In-depth Guide for Teams Using GitHub](https://github.com/SF-WDI-LABS/shared_modules/blob/master/how-to/github-collaboration-workflow.md)**
* <a href="https://help.github.com/articles/adding-collaborators-to-a-personal-repository" >Adding collaborators to a personal repository</a>
* <a href="http://nvie.com/posts/a-successful-git-branching-model" >A successful Git branching model from industry</a>
* <a href="https://help.github.com/articles/using-pull-requests" >Using pull requests</a>

## Tutorials

* **We recommend you try Levels 1-3 of this [git branching tutorial](http://pcottle.github.io/learnGitBranching/).** Stop at 4: "Rebase Introduction". Take your time:
  * Read all the dialogs. They are part of the tutorial.
  * Think about what you want to achieve.
  * Think about the results you expect before you press enter.
  * Whenever you see/type `git commit`, you can assume some changes have been made and staged.
* <a href="https://www.codeschool.com/courses/try-git" >Try Git - Code School</a>
* <a href="https://github.com/Gazler/githug" >githug</a>
