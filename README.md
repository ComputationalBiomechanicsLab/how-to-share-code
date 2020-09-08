# Sharing Biomech Codes

This repo contains notes for a tutorial given during a CBL meeting on
9th September 2020.

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

    - **This tutorial**: uses [TortoiseGit](https://tortoisegit.org/),
      because it's free and one of the oldest clients (so there's
      plenty of guides on the internet for it, etc.).

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
for months, completely torpedoing a study.


### 3.a.2 What if someone thinks the code is low quality?

"Absolute quality" does not exist in software.

Sure, there's extremely hacky and hard-to-read patterns out there, but
there's no such thing as "perfect" quality - especially when it comes
to research codes.

All codebases are a result of their constraints. Code that's rushed to
demo a tech feature at a conference is going to be *a lot* hackier
than the code that keeps your washing machine from shaking itself
apart.

You wouldn't want to write your code the way NASA writes the Mars
Rover software: doing it that way makes development *very* slow. What
you, as a researcher, probably want is to get something working fairly
quickly. You don't really necessarily care about memory layout, or
allocations, or tricky edge cases. That's completely normal - it takes
*years* to learn some of this stuff. Now take the extra "leap" and
realize that it's also completely normal for a codebase to be somewhat
hacky, or somewhat buggy, in its early prototypical phases because the
objective of most research codes is to get something working quickly.

What I'm trying to articulate is that being afraid that your code
isn't "good enough for the internet" kind of ignores the fact that cat
memes are "good enough for the internet". It also ignores the fact
that most closed-source research codes you read about in journal
papers are typically very hacky *and* end up being "good enough for an
international journal". Think about that.


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
public after publishing in a click of a button.

However, don't overestimate competitors *too* much. In my experience,
people are far too lazy to read through other people's code. If your
codebase is even slightly complex, or involves maintenance (all
non-trivial codebases need maintenance) then it will take a fair
amount of effort for an external researcher to maliciously outright
steal it.

What other teams will *probably* realize, after seeing + trying your
open-source project, is that it's much more efficient for them to
collaborate with you. So you might end up in a collaboration in which
you help them run your code, or you agree to enhance your code for
their research.

Being scared of theft mostly only applies to the core
codes/algorithms/results you plan on publishing. This is *usually* a
minority of the code researchers write, because the majority is stuff
like:

- Some script for converting IMU data into a CSV file
- Some other script that converts such-and-such a file into an OpenSim
  model
- Some little framework that's used for downloading datasets over the
  internet

All stuff that's insanely useful for day-to-day research, but probably
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

[🎥 VIDEO: Doing this in Windows with GitHub desktop](https://youtu.be/BhPsfpsw7Ww)
[🎥 VIDEO: Doing this in Windows with TortoiseGit](https://youtu.be/8Pu1_89hPIk)

Any directory can be augmented with a git repository, such that any
changes in that directory can later be comitted to the git repository.

Go to your directory and `Initialize a git repo` (TODO: windows?)
- `init`
- `add`
- `commit`

Once you have comitted the `add`ed files to your local git repository,
you have created an immutable snapshot of your work at a particular
point in time.


## 3.c. Using GitHub

[🎥 video of these steps](https://youtu.be/BOOluANRAlg)

GitHub is an online service for hosting git repositories.

You can use it like a backup system by keeping all of your
repositories private, but the main value-add of GitHub is that it
makes it easier to share codebases.

### 3.c.1. Create a Blank Repository on GitHub

### 3.c.2. Configure your local Repository to use the GitHub Repository as a Remote

### 3.c.3. Push your local changes to GitHub

### 3.c.4. View Changes

### 3.c.5. (bonus) commit diffs, commenting on code, issues, etc.



## 4.c. Collaborating on GitHub

[🎥 video of these steps](https://youtu.be/S6n5HvWy6UQ)

GitHub is specifically designed to make it easy to collaborate on
codebases. It's geared towards software developer teams, but the
features that make it useful for software teams can also make it
useful for smaller research teams.

### 4.c.1. Fork This Repository

### 4.c.2. Clone the Fork

### 4.c.3. Edit Something

### 4.c.4. Create a PR
