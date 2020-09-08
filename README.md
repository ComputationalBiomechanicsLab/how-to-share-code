# Sharing Biomech Codes

This repo contains notes for a tutorial given during a CBL meeting on
9th September 2020.

The main goals of the tutorial are to:

- Encourage people to share research codes, even if those codes aren't
  yet "ready"

- Show basic git usage

- Show uploading git repositories to github

- (if time) Show github PRing, reviewing, etc.



# 1. tl;dr (quickstart)

- Get a `git` client
- Make a GitHub account
---
- Create a local repository
- Add your code to your local repository
- Create a GitHub repository
- Push your local repository to GitHub
- View it online
---
- View someone else's repository online
- Clone someone else's respository
- Modify someone else's code
- Create a PR


# 2. Prerequisite Steps

To save some time, these are things that I will skip over in this
tutorial. You can do these ahead of time (if you plan to go along) or
after:

- Get a `git` client

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

- Create an account on GitHub

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
that each of those concerns aren't necessarily as bad as they look.


### 3.a.1 What if someone finds a bug?

So what?

I'll let you in on a secret: >95 % of code is buggy in *some* way. If
your code is relevant enough for other developers to find bugs in your
source code then you are already in a privileged minority because the
vast majority of code out there barely qualifies as useful enough for
other developers to read.

Sure, it's mildly embarrassing for some other developer to point out
that your code is broken in some way--I hate it when they do that--but
that mild embarrassment might be saving you from a later major
embarrassment when you find, after months of number crunching, that
your code produces sane-looking-but-ultimately-garbage data and you
end up having to redo everything.


### 3.a.2 What if someone thinks the code is low quality?

There is no such thing as "absolute quality" in software.

Sure, there's extremely hacky and hard-to-read patterns out there, but
there's no such thing as "perfect" quality - especially when it comes
to research codes.

The NASA mars rover developers have a bunch of extra guidelines to
ensure that their code is high-quality enough to run remotely on
another planet
([source](https://medium.com/better-programming/the-power-of-10-nasas-rules-for-coding-43ae1764f73d)). Those
guidelines can make the code *uglier* but *more robust*. Effectively,
they sacrifice one quality metric (easiness to read) to gain in
another (robustness). Same goes for whoever's writing pacemaker
firmware, or Facebook, or World of Warcraft, or the software that
makes my phone routinely forget my email credentials.

You wouldn't want to write your code the way NASA writes theirs: doing
that makes development *very* slow. What you, as a researcher,
probably want is to get something working fairly quickly. You don't
really necessarily care about memory layout, or allocations, or tricky
edge cases. Good. That's completely normal. Now take the extra "leap"
and realize that it's also completely normal for a codebase to be
somewhat hacky in its early phases entirely because the objective of
most research codes is to get something working quickly.

What I mean to point out is that being afraid that your code isn't
"good enough for the internet" kind of ignores the fact that cat memes
are good enough for the internet. It also ignores the fact that most
closed-source research codes typically are very hacky *and* end up
being "good enough for an international journal". Think about that.


### 3.a.3 What if someone *steals* my code

**This is probably the most legit concern I come across**.

If you're writing extremely secret code that's:

- For a competitive research field where the other academics are known
  to be complete dicks who will literally rip you off, or scoop you
  before you publish.

- And the code is so easy to understand that they can just copy +
  paste + modify the code into some other project and entirely cut you
  off

**Then you should consider--at least pre-publication--putting your
code into a private/organizational repository.** You can make the code
public later, once everyone's bored by the novelty.

However, don't overestimate other developers *too* much. In my
experience, people are far too lazy to read through other people's
code. If your codebase is even slightly complex, or involves
maintenance (all non-trivial codebases need maintenance) then it will
take a fair amount of effort for an external researcher to maliciously
outright steal the code.

They will probably realize that it's much more efficient for them to
set up a collaboration in which you help them run your code, or you
agree to enhance your code for their research. This is actually handy,
because it means you can dovetail them trying to use your code (by
trying out whatever's in the repo) into a collaboration.

This paranoia only really applies to the core codes/algorithms you
plan on publishing, which is *probably* a minority of the code
researchers write, because the majority of code researchers write is
typically things like "some script for processing IMU data" and "some
other script that converts such-and-such a file into an OpenSim file"
or "some script I used to download all the model files from that
website".

---

So, hopefully this has convinced you that sharing code isn't a big
deal. Sure, there's going to be bugs and there's going to be things
that can be improved. That's always the case.

The main benefit to focus on is that sharing code makes it *much*
easier to collaborate on code-heavy projects. If you have a script
that (e.g.) processes IMU data and "mostly works" for your purposes,
then when some other researcher needs to process IMU data you can just
give them a GitHub link to your script.

It might not work on their computer. They might need to modify your
script a bit. But they might fix those problems so they can move
forward, and they might share those fixes with you. That process helps
the researcher (who doesn't have to start from scratch writing an IMU
processing script) and it helps you (because they made your code a
little bit better).


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
the scripts you write+need are in a single directory.

- This does not mean that every single file you use needs to be in
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
  developers tend to prefer ease-of-use much more than "correctness".


### 3.b.2. Add the directory into a local repository

- `init`
- `add`
- `commit`


### 3.b.3. Try editing things, rollback, etc.


### 3.b.4 (bonus) mirroring, archiving, etc.


## 3.c. Using GitHub

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

GitHub is specifically designed to make it easy to collaborate on
codebases. It's geared towards software developer teams, but the
features that make it useful for software teams can also make it
useful for smaller research teams.

### 4.c.1. Fork This Repository

### 4.c.2. Clone the Fork

### 4.c.3. Edit Something

### 4.c.4. Create a PR


## 5.c. Additional Tools/Notes

- Gist
