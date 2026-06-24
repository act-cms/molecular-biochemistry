Abbreviated Lesson Flow for 2024 and 2025 Cohorts
=================================================

The full Lesson Flow described in this tutorial was designed & implemented by
Dom in his new role as the ACT-CMS GitMaster (GM), and is intended to provide
structure and clarity for how to develop, track, collaborate, and deploy _new_
lessons developed by the 2026 cohort of ACT-CMS Fellows. For Fellows in the
2024 and 2025 cohorts, however, whose lessons are already at various stages of
development and who may have used any number of other completely reasonable
workflows to do so, the following is an abbreviated lesson flow which can be
used to get your materials up onto the Portal in advance of BCCE 2026:

## I. Setup

1. Install GitHub Desktop if you haven't already
2. Make a new lesson repository from the `act-cms/lesson-cookiecutter` if you
don't already have a lesson repository in the ACT-CMS organization
3. Clone the lesson repository to your local machine
4. Clone the `act-cms/instructor-materials` and `act-cms/portal` repositories
to your local machine

## II. Lesson Repository

### II.A. Add All Materials to `dev` Branch

1. Using GitHub Desktop, navigate to the local clone of the lesson repository
and check out the `dev` branch
2. Using your file navigator (Windows Explorer, OSX Finder, or the command
line), do the following for each chapter (Jupyter notebook) of your lesson
module that you have developed and piloted with students,
    1. Make a copy the `01_lesson-template` directory named according to the
    convention `XY_short-chapter-name`, where `XY` is the numerical order
    that the chapter comes in your lesson module
        * Examples: `01_blah-blahblah`, `02_yadda-yadda-yadda`, ...
    2. Copy **both** the instructor and student versions of your chapter
    notebook from wherever it currently lives into the newly created chapter
    directory, as well as any associated data/image/etc. files required by
    the lesson chapter
        * ***It does not matter what state you think the materials are in.***
        If you have piloted them, they are getting pushed!
        * Rename the instructor version of the chapter notebook
        `instructor-key.ipynb`
        * Rename the student version of the chapter notebook `student.ipynb`
        * Test that the notebooks execute properly on your local machine!
    3. Edit the chapter directory's README file to provide the indicated lesson
    information
    4. Edit the `instructor-notes.ipynb` notebook for the chapter to include
    any implementation notes/commentary/advice/etc. that you learned from
    your pilot that could benefit a future adopting instructor (you, another
    Fellow, or a member of the community at large)
4. Using GitHub Desktop, commit your changes on the `dev` branch of your local
clone of the repo
5. Using GitHub Desktop, push your commits to `origin:dev` (i.e.,
`act-cms/<lesson-repo>:dev`)

### II.B. Merge Student Materials into Main Branch

Using GitHub Desktop,
1. Checkout the `main` branch of your local clone of the lesson repo
2. From the "Branch" dropdown menu, select the option "Merge into Current Branch"
3. Choose to merge into `main` from the `dev` branch
4. Choose "rebase" as the merge strategy
5. Choose "overwrite file history" (or equivalent) when merge is rejected
because of disparate histories

Using your file navigator,
6. **Delete all instructor materials from the main branch**, including:
    * Complete instructor keys (`instructor-key.ipynb`)
    * Notes to adopting instructors (`instructor-notes.ipynb`)
    * Any other sensitive files you don't want to deploy to students

Back on GitHub Desktop,
7. Commit the change of deleting the instructor materials from the main branch
8. Force-push the new history from `local:main` to `origin:main`

## III. Instructor Materials Repository

1. On GitHub Desktop, checkout the `dev` branch of your local clone of the
lesson repository
2. On GitHub Desktop, navigate to the `instructor-materials` repository and
ensure the `main` branch is checked out
2. Open two windows of your file navigator of choice
    1. Window A: Navigate to your local clone of the lesson repository
    2. Window B: Navigate to your local clone of the `instructor-materials`
    repository
3. Create a new directory in your local clone of the `instructor-materials`
repository whose name _exactly matches_ the name of your lesson repository
4. Copy **the entire contents of the `dev` branch of your lesson repo** into
your new lesson directory on the main branch of your local clone of the
`instructor-materials` repository
6. On GitHub Desktop, commit your changes & push them to
`act-cms/instructor-materials:main`

## IV. ACT-CMS Lesson Portal Repository

1. On GitHub Desktop, navigate to the local clone of the `portal` repository
and ensure the `main` branch is checked out
2. Using your file navigator, make a copy of the `template.yml` file
3. Rename the copy of the `template.yml` file to _exactly_ match the name
of your lesson repository
4. Move your newly renamed `my-lesson.yml` file into the `lessons` directory
5. Edit the `my=lesson.yml` file to provide the information required for
the ACT-CMS Lesson Portal
6. Using GitHub Desktop, commit your changes to the `main` branch of your local
clone of the `portal` repository
7. Push your commit(s) to `act-cms/portal:main`


