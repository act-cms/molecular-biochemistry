Chapter 2: Setup for ACT-CMS Fellows
====================================

1. Online Accounts
    * ACT-CMS Community: Discord
    * OER Development & Distribution:
        - ChemCompute
        - GitHub (send username to Dom)
2. Local Machine
    * `git` CLI and/or GH Desktop
    * GH Repository Clone
        - `act-cms/portal`
        - `act-cms/instructor-materials`
    * Lesson Creation on GH
        - Create lesson repo from `GH/act-cms/lesson-cookiecutter`
    * Python Environment
        - Download & install miniconda
        - Build `chemcompute` conda env

## 2.1 Online Accounts

The first things that needs set up for new ACT-CMS Fellows are various online
accounts. Most likely, you have been directed to do this by Marie in an email;
however just in case, here's what needs done:
1. Join the Discord Server
2. Sign up for an account on GitHub using your university email address
    * Join [GitHub Education](https://github.com/education/teachers) & verify
    your educator status to get all of the features available at the Team level
    for free!
    * After your account has been created, add your username to the [Mentor Match & Fellow Info Sheet](https://docs.google.com/spreadsheets/d/1w7NQgEzYhT3kPA5IgK84WGAyBFqnbtIujlttAdk_Vak/edit?usp=sharing)
    so the GitMaster can add you as a member of the `GH/act-cms` organization
3. Log into [ChemCompute](https://chemcompute.org/) using your university email
    * If your institution uses InCommon or CILogon for authentication, you won't
    need to create an account --- instead, you'll just be able to sign in directly
    using your institutional sign-in!
        - Look for your institution in the list, if it's there then click & sign in!
        - If your institution is not listed but you are a Microsoft or Google campus,
        just click on the corresponding button to be redirected to a login page.
    * If your institution does not use CILogon for authentication, sign up for a
    local account using your university email address and verify your email.

## 2.2 Local Machine

After setting up your online accounts, the only thing left to set up before you
can begin developing your lesson(s) is your personal computer (called `local`
throughout this tutorial). 

### 2.2.1 Download & Install Version Control Software

There are two options for version control software that are recommended for ACT-CMS
Fellows: the `git` command line interface (CLI) and GitHub Desktop application (GHD).
For installation instructions/links and more information about each, see the tabs
below:

#### Option A (RECOMMENDED): GitHub Desktop (GHD)
Version control via the GitHub Desktop graphical user interface (GUI).

| Pros | Cons |
|:-----|:-----|
| Only minor learning curve | **ONLY** available for OSX & Windows machines (NO HPC!) |
| Just as fully featured as `git` CLI | |

> [!NOTE]
> See the [GitHub Desktop installation instructions](https://github.com/apps/desktop)
> for your local machine's operating system. Once you have GHD installed,
> complete the steps outlined in the [GHD Setup Instructions](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/setting-up-github-desktop)
> before moving on!

> [!TIP]
> ***GM Note:*** This is the recommended approach for all ACT-CMS Fellows, unless
> you're already comfortable with UNIX and the `git` CLI! 

#### Option B: `git` Command-Line Interface (CLI)</summary>
Version control using `git` commands on the UNIX/Linux command line.

| Pros | Cons |
|:-----|:-----|
| Works on command line in every UNIX-based OS (Linux/OSX) | Must learn UNIX first, so somewhat steep learning curve |
| The only option when there is no graphical desktop (HPC clusters etc.) | |

> [!NOTE]
> See the [Git-SCM installation instructions](https://git-scm.com/install/) for
> links & instructions for your local machine's operating system.

> [!WARNING]
> ***GM Note:*** For Fellows who are UNIX/`git` novices, this is not the
> recommended approach! If you are already comfortable with `git` and UNIX,
> feel free to use this method --- however be aware that only GHD instructions
> are provided in this tutorial.

> [!IMPORTANT]
> Any time a chapter of this tutorial directs you to take an action with
> version control, it will be assumed that you are using GitHub Desktop (GHD)
> to do so and relevant links to [the GHD Documentation](https://docs.github.com/en/desktop)
> will be provided.

### 2.2.2 Clone ACT-CMS Repositories

Now that you have `git`/GHD installed, you can create local copies of remote
repositories which are owned by the ACT-CMS organization. To do so, follow the
steps from the ["Clone a GitHub Repo" page of the GHD
documentation](https://docs.github.com/en/desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop)
for each of the following repositories:
* [`act-cms/portal`](https://github.com/act-cms/portal)
* [`act-cms/instructor-materials`](https://github.com/act-cms/instructor-materials)

### 2.2.3 Create Your Lesson Repository from the `act-cms/lesson-cookiecutter` Template Repo

After cloning the `act-cms/portal` and `act-cms/instructor-materials` repositories
to your local machine, it's time to create your lesson repository!

To do so,
1. Navigate to the [the ACT-CMS organization homepage on GitHub](https://github.com/act-cms)
2. Under the "Repositories header", click on the green "New" button to open
the repository creation form.
3. Fill out the form according to the directions below to create your repository!
    1. General
        * Leave the `act-cms` organization as the repository owner
        * Choose a short but descriptive name for the repo, using a hyphen `-`
        instead of spaces to separate words.
        * Leave the "Description" box blank.
    2. Configuration
        * Set your repo to be Public using the "Visibility" dropdown. If your repo
        is private, you won't be able to deploy your materials to ChemCompute for
        your students to use!
        * Choose to start your repository from the `act-cms/lesson-cookiecutter`
        template repository to ensure you have everything set up for you automatically!
        * Toggle the "Include All Branches" option to "On"
        * Click the green "Create repository" button to create your lesson repo!

> [!IMPORTANT]
> From this point forward, we will refer to the lesson repository hosted on
> GitHub as `origin`, because it is the "origin" of your lesson!

### 2.2.4 Clone Your Lesson Repository 

Finally, after you are redirected to your newly created lesson repository,
clone it to your local machine! For the rest of the Tutorial, we will refer
to this local clone of your lesson repository as `local`.

### 2.2.5 Setting Up Your Local Python Environment

1. Python Installation
    * Recommended: [the Anaconda Distribution](https://www.anaconda.com/download/success?reg=skipped)
    * Minimal installation: [Miniconda](https://www.anaconda.com/download/success?reg=skipped)
2. Build `conda` environment mirroring ChemCompute 2.5 using `environment.yml`
    * To build the environment [using Anaconda Navigator, follow these instructions](https://www.anaconda.com/docs/tools/anaconda-navigator/tutorials/manage-environments#importing-an-environment)
    * To create the environment on the command line, navigate to the top-level
    directory of the `local` clone of your lesson repository, and execute the
    following command:
        ```bash
        (base) user@local:~/path/to/local/repo (contrib)$ conda env create --file environment.yml
        ```
    * The environment which is created will be called `chemcomp2.5`
3. Activate the `chemcomp2.5` environment
    * To activate the `chemcomp2.5` environment [using Anaconda Navigator, follow these instructions](https://www.anaconda.com/docs/tools/anaconda-navigator/tutorials/manage-environments#activating-and-using-an-environment)
    * To activate the `chemcomp2.5` environment on the command line, execute the
    following command:
        ```bash
        (base) user@local:~/path/to/local/repo (contrib)$ conda activate chemcomp2.5
        ```
4. After the `chemcomp2.5` environment is activated, Launch JupyterLab from
your lesson repository
    * [Instructions for launching JupyterLab from Anaconda Navigator](https://www.anaconda.com/docs/getting-started/guides/how-to-open-jupyterlab)
    * To launch JupyterLab from the command line, navigate to the top-level
    directory of the `local` clone of your lesson repository and execute the
    following command:
        ```bash
        (chemcomp2.5) user@local:~/path/to/local/repo (contrib)$ jupyter-lab
        ```


