# Sharing Biomech Codes

This repo contains notes for a tutorial given during a CBL meeting on
9th September 2020.

[🎥 VIDEO: recording of the tutorial 🎥](https://youtu.be/nPYbb6QO_SA)

The main goals of the tutorial are to:

- Encourage people to share research codes, even if those codes aren't
  yet "ready"

- Show basic git usage

- Show uploading git repositories to github

- Show github PRing, reviewing, etc.



# 1. Overview

- (prerequisite steps)
- Get a `git` client ([list](https://git-scm.com/downloads/guis),
  [recommended](https://tortoisegit.org/))
- Make a GitHub [here](https://github.com/)
---
- (during)
- Create a local repository
- Add your code to your local repository
- Create a GitHub repository
- Push your local repository to GitHub
- View it online
- View someone else's repository online
- Clone someone else's respository
- Modify someone else's code
- Create a PR
---
- Useful Links:
    - [CBL Github](https://github.com/ComputationalBiomechanicsLab)
    - [gist](https://gist.github.com/), for quick one-off scripts
    - [learnxinyminutes](https://learnxinyminutes.com/). Specifically,
      it has a [git](https://learnxinyminutes.com/docs/git/) page for
      more advanced users


# 2. Prerequisite Steps

To save some time, these are things that I will skip over in this
tutorial. You can do these ahead of time (if you plan to go along) or
after:

1. Get `git`

    - [All downloads](https://git-scm.com/downloads). [Windows download](https://git-scm.com/download/win).

    - `git` is the core command-line utility that "does the work".
       Some clients (below) include git, but it's usually best to
       also install standalone `git` also, because some clients do
       not include `git` and some online guides will describe how
       to do things in "pure" `git`, rather than through a UI.

1. Get a `git` client

    - At its core, `git` is a command-line application for creating
      and manipulating repositories. Learning to use the `git`
      command-line directly can be useful, but that takes time. When
      starting out, it's better to use a git client that simplifies
      the process with a nice UI.

    - **List of clients
      [here](https://git-scm.com/downloads/guis)**. Recommendations
      below are just soft guidelines. Almost all clients will be able
      to perform the demonstrated workflow.

    - **This tutorial**: uses the [GitHub Desktop](https://desktop.github.com/),
      because it's free and integrates with GitHub fairly well. Once
      you install it, be sure to log in to your GitHub account in it.

1. Create an account on GitHub

    - Browse to [github.com](https://github.com/)
    - Create an account through the landing page
    - Note: free accounts can create private repositories, and
      academic groups can generally register to have an
      [organization](https://docs.github.com/en/github/getting-started-with-github/types-of-github-accounts#organization-accounts),
      which enables researchers in a group to privately share code
      with each over.



# 3. Tutorial Content


## 3.a. Intro: Don't Be Afraid to Share Code

Sharing code is easy. Overcoming the psychology around sharing code is
hard. You are putting something out there for the whole world to see,
so it's entirely natural to have some reservations. Typical
reservations include:

1. What if someone finds a bug?
2. What if someone thinks the code is low quality?
3. What if someone steals my code?

All completely normal concerns to have. However, let me convince you
that each of those concerns aren't *necessarily* as bad as they feel.


### 3.a.1 What if someone finds a bug?

I'll let you in on a secret: >95 % of code is buggy in *some*
way. Even the most heavily scrutinized codebases contain bugs.

If your code is relevant enough for other people to spend their time
finding bugs in your source code then congratulations: you might not
feel it, but your code is already in the privileged minority of "code
that's important enough to be reviewed".

The vast majority of code on GitHub never gets reviewed--or even
ran--by someone else. It's depressing, but true. So if your concern is
that someone finds a bug, try to take a positive spin on it: someone
was keen enough to understand your work that they found a bug.

Sure, it's mildly embarrassing that someone then (usually, publically,
on a GitHub issue) calls out your bug--critique always feels
awkward--but that mild embarrassment might save you from a later
(major) embarassment, such as the bug going undetected in your code
for months and completely torpedoing a study.


### 3.a.2 What if someone thinks the code is low quality?

"Absolute quality" does not exist in software.

Sure, there's extremely hacky and hard-to-read patterns out there, but
there's no such thing as "perfect" quality - especially when it comes
to research code.

All codebases are a result of their constraints. Code that's rushed to
demo a tech feature at a conference is going to be *a lot* hackier
than the code that keeps your washing machine from shaking itself
apart.

NASA writes extremely high-quality code, but you wouldn't want to write
your code the way NASA writes theirs. They have extremely strict guidelines
on how to write code because (e.g.) a NASA satellite can feasibly be left
running unattended for decades. 

Writing software that way makes development *very* slow, which isn't 
what you, as a researcher, probably want. You *probably* prefer to have
something working fairly quickly. You probably don't necessarily care 
about memory layout, or allocations, or tricky edge cases. This is
actually your strength, because it takes professional developers *years*
to learn some of that stuff.

Once you accept that "quality" is just a tradeoff, and that you're in a
field where `speed > simplicity > quality`, then I'd like to invite you
to take the extra "leap" and realize that it's also completely normal 
for a codebase--your codebase--to be somewhat hacky, or somewhat buggy,
in its early prototypical phases. It's *normal*. Researchers that hide
their code out of embarassment aren't fooling anyone.

What I'm trying to articulate is that being afraid that your code
isn't "good enough for the internet" kind of ignores the fact that cat
memes are "good enough for the internet". It also ignores the fact 
that most closed-source research codes you read about in journal 
papers are typically very hacky *and* end up being "good enough 
for an international journal". Think about that next time you read 
a paper.


### 3.a.3 What if someone *steals* my code

**This is probably the most legit concern I come across**. If you're
writing research code that's:

1. For a competitive research field where the other academics are
   known to be complete dicks who will literally rip you off at any
   opportunity to scoop you before you publish.

2. And the code is so easy to understand that they can just copy +
   paste + modify the code into some other project and entirely cut
   you off.

**Then you should consider--at least pre-publication--putting your
code into a private/organizational repository.** You can make the code
public after you publish.

However, don't overestimate these competitors *too* much. In my 
experience, people are far too lazy to read through other people's code. 
If your codebase is even slightly complex, or requires maintenance (all
non-trivial codebases require maintenance) then it will take a fair
amount of effort for an external researcher to maliciously outright
steal it.

What those researchers will *probably* realize, after seeing + trying your
open-source project, is that it's much more efficient for them to get you
to do it for them. So you might end up in a collaboration in which
you help them run your code, or you agree to enhance your code for
their research.

Being scared of theft mostly only applies to the core
codes/algorithms/results you plan on publishing. That kind of code is
actually *usually* a minority of the code researchers typically write, 
because the majority of the code they write is stuff like:

- Some script for converting IMU data into a CSV file
- Some other script that converts such-and-such a file into an OpenSim
  model
- Some little framework that's used for downloading datasets over the
  internet

All of that code is insanely useful for day-to-day research, but probably
can't be used directly in a publication. That's the kind of code that
benefits most from sharing, because there's probably 10 different
scripts for processing IMU data in the wild.

### 3.b.4. Summary

Hopefully this has convinced you that sharing code isn't a big
deal. Sure, there's going to be bugs and there's going to be things in
your code that can be improved. That's always the case.

The main benefit to focus on is that sharing code makes it *much*
easier to collaborate. If you have a script that (e.g.) processes IMU
data and "mostly works" for your purposes, then when some other
researcher needs to process IMU data you can just give them a GitHub
link to your script.

The script might not work on their computer. They might need to modify
your script a bit. But they might fix those problems. And they might
share those fixes with you, which would be useful. That's open-source
in a nutshell.


## 3.b. Getting Started with Git (Locally)

The main objective of this section is to show you how to use git
locally.

This is useful because, even if you don't want to share your code,
knowing how to use git locally allows you to save snapshots of your
code.

> **Note**: The steps written below are *rough* - you might need to do
>           things slightly differently.. The reason why they are rough is
>           because I'll be going through these steps during the tutorial,
>           and because I have recorded the steps as videos, which (in my
>           opinion) are easier to follow than a written "click here, do 
>           this, do that" guide.

> **Note #2**: Written steps assume you're using GitHub desktop.


### 3.b.1. Put all of your code into one directory

Ignoring more advanced use-cases, a git
[commit](https://git-scm.com/docs/git-commit) effectively snapshots
one directory. So, when writing projects, try to make sure that all
the scripts and configuration files you write and need are in a single
directory.

- This does not mean that every single file you use *needs* to be in
  that directory. It's completely normal to (e.g.) hold large
  experimental data files somewhere else
  (e.g. `C:\Data\Experiment_1\etc`).

- Other guides may say that you should't add any 3rd-party library
  scripts into your repository, and that anyone using your code should
  acquire those scripts separately. **Personal opinion:** When
  deciding on what to include/not include in a repository, be
  practical. If someone can grab all the libraries you use in one step
  (e.g. by running `pip install -r requirements.txt`) then keep the
  libraries separate and do that. If your codebase relies on various
  scripts from random websites, snippet archives, network drives,
  etc. and it's going to take a lot of time for someone to grab those
  libraries, then include them in your repository. In my experience,
  people tend to prefer ease-of-use much more than what's "correct".


### 3.b.2. Create and Use a Local Repository

[🎥 VIDEO: Doing this in Windows with GitHub desktop](https://youtu.be/WVzpaXQSQ50)
[🎥 VIDEO: Doing this in Windows with TortoiseGit](https://youtu.be/8Pu1_89hPIk)

Any directory can be augmented with a git repository, such that any
changes to that directory can later be comitted to the repository.

Steps:

- In the GitHub desktop application (GHDA), try to open your 
  working directory as an existing repository. The app will 
  notice that your directory isn't a repository yet and suggest you 
  create one. Do that.

- The GHDA will automatically record the current state of your directory
  as an "initial commit"

- Any changes you make to that directory will now be detected in the
  GHDA. Experiment with this by changing a file an checking whether
  the change appears in the UI (it should)

- If you want to "commit" those changes to a new snapshot, you can do
  that through the UI in the bottom-right

- The UI also has features for reverting a change back to its original
  state, or checking out earlier versions of the directory (I'm not
  going to write all of that down here - just experiment with a throwaway
  directory, it's fairly intuitive)

Key points:

- Local git repositories collect your **commits** (snapshots) into a
  hidden directory called `.git` in your working directory.

- A commit is effectively a snapshot of your directory's content
  at some point in time, plus some commit metadata (message, who
  committed it, when it was commited, etc.)

- There is no special "behind the scenes" database that git uses. 
  For this reason, you do not need an internet connection to record
  a commit, because local snapshots snapshots effectively just "end 
  up" in the local `.git` directory. 

- So, a "git augmented" directory is not special. It's just a normal 
  directory with a `.git` directory hidden inside it. If you don't 
  quite trust git (you should, though), then you can just continue 
  to just backup by copying your directory as usual. Nothing should
  break if you do that.

- (bonus) The local repository you made is a complete repository, not
  just a small part of one. When you"clone" a remote repository from 
  GitHub (e.g. OpenSim) then you will also end up with a complete--local--OpenSim repository that also has the full history 
  *but* is entirely independent of GitHub.


Other reading:

- [git book](https://git-scm.com/book/en/v2). Specifically, the [overview](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) has a decent explanation of what git is and [recording changes](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository) has a fairly comprehensive overview of the various commit states (don't worry so much about this in the early days)


## 3.c. Using GitHub

[🎥 VIDEO: Doing this in Windows with GitHub desktop](https://youtu.be/9YhbUwqcHzw)
[🎥 VIDEO: Doing this in Windows with TortoiseGit](https://youtu.be/BOOluANRAlg)

GitHub is an online service for hosting git repositories.

Ignoring all of GitHub's features, you could just use it as a 
backup system. However, the main value-add of GitHub is that it
makes it easier to share codebases, changes, comments, etc. 

Without GitHub, you'd have to send code patches via email and - this 
is effectively git was (and still is, on some projects) used. With 
GitHub, you can usually just send a link, or tag someone on something 
(e.g. "hey @adamkewley, what's going on with this `if` statement, huh?").


Steps:

- Open your repository in the GitHub desktop application (GHDA) and 
  click "Publish repository" at the top

- Decide on whether you would like it to be public/private, what name
  you would like it to have, etc.

- Click "publish repository"

- Done. Now you should be able to browse to your GitHub account and
  see the new repository

- For later work, you will continue to change files and then commit
  changes. **However**, those commits are only written to your local
  repository. You need to `push` those changes to GitHub. Usually, after
  you commit something in the GHDA, then a button will pop up asking
  whether you would like to *also* push the changes to GitHub.

- Now that your code is github, you should be able to view the files
  online, link to them, comment on them, add issues, etc.


Key points:

- Git is a *distributed* version control system. What this means practically
  is that multiple copies of your repository can exist on multiple computers.
  There is no *central* git repository. There's just places that can hold
  copies of repositories. Your local repository is one copy. Your GitHub
  repository is another.

- To "copy" commits from one repository (e.g. your local one) to some remote
  location (e.g. GitHub), you need to `push` the changes. Most git UIs have
  this feature.

- Again, GitHub is just one remote location that you can push to. Equally,
  you could set `C:\Dropbox\MyRepositoryMirrors\MyRepo.git` as a "remote"
  and `push` to that.

Other Repository Hosting Services:

- [gitlab](https://about.gitlab.com/)
- [bitbucket](https://bitbucket.org/)
- [azure devops](https://azure.microsoft.com/en-us/services/devops/)
- [sourceforge](https://sourceforge.net/)


## 4.c. Collaborating on GitHub

[🎥 VIDEO: Doing this in Windows with GitHub desktop](https://youtu.be/I649yZ4IAcw)
[🎥 VIDEO: Doing this in Windows with TortoiseGit](https://youtu.be/S6n5HvWy6UQ)

GitHub is geared towards software developer teams, but the features 
that make it useful in software development can also make it useful
in research teams.

You might not actually collaborate on GitHub much, especially if you 
are mostly writing isolated pieces of code that only you care about.
The reason I'm showing this is mostly to show that editing other 
people's code isn't a big deal. 

Pushing changes is effectively five steps (fork, clone, change, push, PR). 
The main barrier in the process is generally organizational (e.g. some 
projects will require a bunch of extra work, or steps, before you can 
PR them). 

Steps:

- Browse to the project you want to contribute to in GitHub

- Create a `fork` by clicking the fork button in the top-right. This
  creates a completely independent remote copy of the project under
  your user account.

- Use the GitHub desktop application (GHDA) to clone your fork locally.
  File menu -> Clone Repository. You now have a local copy of your 
  remote fork

- Edit this local copy as much as you want - it's yours, after all. The
  primitive operations are still the same (change things, commit changes,
  etc.).

- Push your local changes to your github account in exactly the same way
  you did above when publishing/pushing your local repository to GitHub

- Your remote fork now contains your changes, and you want those changes
  to be accepted "upstream" in the original project, so that everyone using
  the upstream project can benefit from your changes

- Browse to your fork in GitHub (typically: go to "My Repositories" and 
  click the fork)

- The UI should notice that your fork is "ahead of OriginalProject by n 
  commits". Click "Create Pull Request" to request that your changes are
  pulled into the original project


Key Points:

- `fork` is a special word that (effectively) means "a copy of some other
  repository". A forked repository is its own, independent, repository. It
  just *also* has (weak) link to the original project, so that changes in
  the fork can be pushed back to the orignal repository (provided they 
  "pull" your "pushed" changes - see ;))

- A pull request (PR) is a special phrase that means "I am requesting that
  you (the original project) pull my changes". PRs typically also contain
  a top-level explanation of what those changes do. 

- Different projects have different PR styles. It's always best to 
  clearly explain what a PR does (e.g. "makes it work on Linux") and 
  why you changed it (e.g. "because we perform experiments on Linux
  a lot").

- There is no enforced writing style or format for PRs. It really depends
  on what project you are PRing and what your PR does. PRing a friend's
  code with a minor change is going to be much more laid-back than PRing
  OpenSSL.
