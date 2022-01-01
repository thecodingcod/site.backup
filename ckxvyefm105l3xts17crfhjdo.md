## The Branch & Merge Game

## What is Version Control?

Version control is a system that allows you to keep track of your work and helps you to easily explore the changes you have made no matter what are you changing **data**, **coding scripts**, **notes**, etc. any file in general.

It also allows the collaboration between developers on a single project easily through branching & merging.

---

## Benefits Of Version Control

- Makes it easy for you to keep track of collaborative and personal projects - all files necessary for certain analyses can be held together and people can add in their code, graphs, etc.
- As the projects develop. each file being tracked by git has a history, making it easy to explore the changes that occurred to it at different time points.
- Easily navigate among the many versions of the files you create
- Enables reviewing other people’s code and also the collaborative code review for collaborative projects.

---

## Version Control Systems

Our main focus in this article is Git as version control. But, we have to mention other available solutions for version control that are being used widely in Enterprise projects and Individual One.

- Git — Most Popular & Used among the Enterprise and Individuals
- AWS Code Commit
- Azure DevOps Server (TFS)
- Subversion (SVN)

There are many solutions for version control, but I've mentioned the popular ones according to the [G2 Survey](https://www.g2.com/categories/version-control-systems?tab=highest_rated).

## The Way Back Machine — Before Version Control
![The Way Back Machine](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049303899/15eGkofHAV.png)


An obvious question a 21st-century developer might ask, **How did people develop software before git or version control?**

As a 21st-century developer, I made very tiny research trying to answer that question and most of them seem to have a common way of doing "**Version Control**" which was a **Shared Drive. It's** either mapped to your pc through a network or being accumulated on a single portable hard disk.

![screen shot](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049306264/RsD86KJ6_.png)
source: [http://www.dev.to](https://dev.to/pandaquests/how-did-people-develop-software-before-git-or-version-control-1564)

> **Disclaimer:** I tried to find a way to contact Mr Douglas to ask his permission to mention his words in this SS but I failed.

**Was it the only way of doing that, copy & paste on a shared hard drive?** No, they used what is so-called [tarball](https://www.gnu.org/software/gnuastro/manual/html_node/Release-tarball.html) to version their software which was mainly used by GNU to deliver their open-source software. 

A tarball is a snapshot of one particular moment in the application development history along with all the necessary files to configure, build, and install the application easily.

---

## Why Git?

Aside from the fact that it's the most commonly used version control system, It has several advantages. So let's highlight the most epics or features that make it a good-to-go choice especially according to SVN.

![Git](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049308176/tKvJqjXWb.png)

1. **Git utilizes multiple repositories**: a central repository and a series of local repositories which are exact copies of the central repository complete **with the entire history of changes.**
2. **Git has a staging area.** This just means that if you made 100 new changes to your code, you can break these 100 changes into 10 or 20 or more commits each with their own comments and their own detailed explanation of what just happened!
3. **It’s faster to commit.** 
   - Because you commit to the central repository more often in SVN, network traffic slows everyone down.
   - Whereas with Git, you’re working mostly on your local repository and only committing to the central repository every so often.
4. **No more single point of failure.** 
   - With SVN, if the central repository goes down or some code breaks the build, no other developers can commit their code until the repository is fixed.
   - With Git, each developer has their own repository, so it doesn’t matter if the central repository is broken. Developers can continue to commit code locally until the central repository has been fixed, and then they can push their changes.
5. **It’s available offline.**, Unlike SVN, Git can work offline, allowing your team to continue working without losing features if they lose connection.
6. **It’s open-source and cross-platform.**

> - Hey! I guess you forgot to mention that SVN repos are far bigger in size than Git!
>   = mmm, Nope I didn't forget But: 
>
> 1.  This claim is actually [a Myth](https://svnvsgit.com/)! they are close in size since they both are using a delta compression algorithm. 

2. I'm not trying to compare Git vs SVN here, it's not the purpose of that article!

---

## A Break!

By reaching this point, you might consider taking a 5-minutes break!

![break](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049312187/WapTQijmfz.png)

---

## What is a repository?

![repository](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049314699/aaLgg0aKEH.png)

A repository is a special type of directory that contains all of your project's files and each file's revision history. 

With Git, that repository must contain a `.git` hidden directory that holds all information that Git needs to: **keep track of changes**, **maintain history**, **commits**, **remote repository information to push to**, .. and so on. **Meaning**, if you delete the `.git` directory, then you delete your project’s history.

**So why a repository is a special type of directory again?** simply because it contains the `.git` directory.

A repository can hold any type of files and multiple directories. By default, it will keep track of all changes that affect all the files and maintain their history, but you can choose to ignore some files or directories that you believe are not important to exist in the remote repository -being held by a Git service provider like GitHub- by listing these files or directories in the `.gitignore` file.

---

## What is branching?

![branching](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049317132/A2LSO1IQb.png)

Branching means you diverge from the mainline of development and continue to do work without messing with that main line. In many VCS tools, this is a somewhat expensive process, often requiring you to create a new copy of your source code directory, which can take a long time for large projects.

## What is a git branch?

![git branch](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049319098/cN-47VjYb.png)

**A branch in Git is simply a lightweight movable pointer to one of these commits.** The default branch name in Git is master. As you start making commits, you’re given a master branch that points to the last commit you made. Every time you commit, the master branch pointer moves forward automatically.

The way **Git branches are incredibly lightweight**, making branching operations nearly instantaneous, and switching back and forth between branches generally just as fast. and Unlike many other VCSs, Git encourages workflows that branch and merge often, even multiple times in a day. Understanding and mastering this feature gives you a powerful and unique tool and can entirely change your development.

The “master” branch in Git **is not a special branch.** It is exactly like any other branch. The only reason nearly every repository has one is that the `git init` command creates it by default and most people don’t bother to change it.

## The Branching Strategy

![https://cdn.hashnode.com/res/hashnode/image/upload/v1641049320708/GHtqdxlOF.jpeg](https://images.unsplash.com/photo-1532622785990-d2c36a76f5a6?ixlib=rb-1.2.1&q=85&fm=jpg&crop=entropy&cs=srgb)

### What is meant by a branching strategy?

A “branching strategy” refers to the strategy a software development team employs when writing, merging, and shipping code in the context of a version control system like Git. 

### Why do we need a branching strategy?

Have you ever wondered how to manage and maintain your remote repository in the case of a team, not individuals, even multiple teams? how would you **handle the changes**? make sure that the remote repository is **always updated**?  how would you **deliver certain features** and ignore others? 

These issues are solved by making what is so a **branching strategy but** don't panic there are existing strategies for general purpose usage, check [branching flows]() for fast-forward.

A branching strategy also ensures everyone on the team is following the same process for making changes to source control. The right strategy **enhances collaboration**, **efficiency**, and **accuracy** in the software delivery process, while the wrong strategy (or no strategy) leads to hours of lost effort.

### Our Goal

The goal of any branching strategy is to solve the previous problem and to enable teams to work together on the same source code without trampling on each other. if you achieved that you've simply made a working strategy!

### Considerations

There are several things to consider handling while designing a branching strategy, here are the common issues

![Considerations](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049323258/IaBg5-jKX.png)

#### Typical development workflow

The typical day-to-day flow includes normal changes that developers make to the code. These changes are ordinary in terms of size and complexity for your codebase and, generally, will make up the bulk of all the changes your developers make. Since this flow will be used the most frequently, your strategy here must ensure proper coordination among the developers and support all relevant policies such as automated testing, pull requests, and deployments.

#### Emergency hotfixes

An emergency hotfix is when a particular incident or issue has been expedited to deal with some emergent situation, normally bug fixes. Your flow must account for a developer who needs to make an urgent change and get it all the way through your process and into production while still aligning with your typical development workflow.

#### Small vs. large changes

As the industry has evolved, the emphasis on developers working on smaller changes and limited batch sizes has increased due to the broader use of flow-based delivery practices. However, there are still times when you must make large, complex changes, and your branching strategy must accommodate those situations.

#### Standard vs. experimental changes

Developers feel greater certainty about how standard code changes will perform than with experimental code changes. For example, if you’re evaluating a new library or framework, you may feel uncertain about how well it integrates with your codebase. In that case, your change may or may not actually go to production but still needs to be shared with other developers. Your branching strategy must account for these types of experimental changes.

### Common types of branches

![types of branches](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049325176/cPPU_q2dc.png)

#### 1. Main branch

Every Git repository has a main (also referred to as mainline or the master branch). When a Git repository is created, the main exists automatically as the implicit first branch. The use of a main and the timing of changes landing on it vary depending on the exact branching strategy being used. In main-based development, the main is the central branch to which all developers send their code changes.

#### 2. Development branch

The development branch is a long-lived feature branch that holds changes made by developers before they’re ready to go to production. It parallels the main and is never removed. Some teams have the development branch correspond with a non-production environment. As such, commits to the development branch trigger test environment deployments. Development and main are frequently bidirectionally integrated, and it’s typical for a team member to bear the responsibility of integrating them.

#### 3. Release branch

A release branch can be either short-lived or long-lived depending on the strategy. In either case, the release branch reflects a set of changes that are intended to go through the production release process.

#### 4. Feature branch

A feature branch can be short- or long-lived depending on the specific branching flow. The branch often is used by a single developer for only their changes, but it is possible to share it with other developers as well. Again, the branching strategy will determine how exactly you define a “feature branch”.

#### 5. Hotfix branch

A hotfix branch is a branch that’s used generally to hold changes related to emergency bug fixes. They can be short-lived or long-lived, though generally, they exist as long-lived branches split off from a release branch. They tend to be more common in teams with explicitly versioned products, such as installed applications.

### Popular Branching flows

#### GitFlow

[GitFlow](https://nvie.com/posts/a-successful-git-branching-model/) was introduced by Vincent Driessen in 2010 to share insight into the use of Git for source control as its use became more widespread. GitFlow relies essentially on every type of branch that was discussed previously with the bulk of the development workflow centring on the long-lived development branch as a shared integration branch for all the developers. The main branch, in this case, essentially reflects a history of all the changes that have gone to production.

#### GitHub Flow

[GitHub Flow](https://guides.github.com/introduction/flow/) was popularized by GitHub as a simpler alternative to GitFlow. It calls for the following workflow:

- The main branch is always releasable, and in fact, releases are generally done directly from it.
- Each developer creates a new branch, the feature branch, for their changes from the main branch.
- Feature branches can be deployed to a testing environment for verification or pushed directly to the main branch and deployed to a non-production environment from there.
- A short-lived release branch may be used off the main branch to prepare for and execute a release.

#### **Challenges**

Both of these branching strategies can work for the right environment, but they have similar downsides. The biggest downside is neither flow adequately supports Continuous Integration. And Continuous Integration is becoming an essential modern development practice. By relying on feature branches, it’s too easy to focus on the benefits of change isolation and ignore the costs. Instead, a better strategy would support Continuous Integration, wherein developers integrate code regularly (i.e., at least every day). Fortunately, there is a branching strategy able to meet all these needs: **trunk-based development.**

## What's Next?

![What's Next?](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049327384/rG7uaIKGa.jpeg)

This is not an in-detail article, it's a high-level one that allows people to discover the missing parts in their strategy. and since I've started that just to enable reaching the point where we can set up our version control system in a way that would support Continuous Integration. my next writing will be dedicated to Trunk-based Development along with any other alternative technique that I might find out while researching.

For now, thanks for giving me your precious time. I'll gladly accept comments that aim to enhance the content quality or correct mistaken info that I wrote here.

## Resources

- [https://www.gnu.org/software/gnuastro/manual/html_node/Release-tarball.html](https://www.gnu.org/software/gnuastro/manual/html_node/Release-tarball.html)
- [https://www.g2.com/categories/version-control-systems?tab=highest_rated](https://www.g2.com/categories/version-control-systems?tab=highest_rated)
- [https://backlog.com/blog/git-vs-svn-version-control-system/](https://backlog.com/blog/git-vs-svn-version-control-system/)
- [https://blog.hackbrightacademy.com/blog/svn-vs-git/](https://blog.hackbrightacademy.com/blog/svn-vs-git/)
- [https://svnvsgit.com/](https://svnvsgit.com/)
- [https://launchdarkly.com/blog/git-branching-strategies-vs-trunk-based-development/](