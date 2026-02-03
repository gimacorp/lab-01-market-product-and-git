# Instructions for TAs

## Grading

Points are given as follows:

<!-- TODO provide a weight for each task -->

## Process

> [!IMPORTANT]
>
> There are 30 students and they'll presumably start submitting their works in the last two hours of the lab.
>
> A TA has only approximately 4 minutes for each student.

- There's a table where:
  - each student provides:
    - their GitHub username;
    - collaborator's GitHub username;
    - links to task issues;
    - statuses of tasks.
  - TA marks accepted tasks.

- TA walks around the class and tracks progress for tasks in that table.

- Student:
  - completes one or more tasks;
  - marks in the table that these tasks are waiting for a TA's review;
  - raises a hand to call the TA.

- TA:
  - comes to the student;
  - answers questions, if any;
  - checks tasks using the [Checklist for TA](#checklist-for-ta);
  - asks additional questions to check student's understanding (remember the time limit for each student);
  - suggests improvements;
  - marks the task as accepted in the table when the task is complete.

- After the lab, [automated checks](#automated-checks) will run.

## Checklist for TA

### [Required tasks](#required-tasks)

### [Lab setup](./README.md#lab-setup)

- Student shows that there's a collaborator in the repo `Settings` -> `Collaborators and teams`.

### [1. Pick a product and study its architecture](./README.md#1-pick-a-product-and-study-its-architecture)

- Student can explain what's on the component diagram in `./docs/architecture.md`.

### [2. Tech roles involved in the selected product](./README.md#2-study-the-market-for-your-product)

- In `./docs/roles-and-skills.md`, skills (`## Common skills across roles`) seem to be related to the identified roles (`## Roles and responsibilities`)

### [3. My tech skills and the market: roadmap.sh and job postings](./README.md#3-my-tech-skills-and-the-market-roadmapsh-and-job-postings)

- Student shows their roadmap with marked items on `roadmap.sh`.
- Student can name one skill they chose to improve this semester and explain why they chose it.

### [Optional tasks](#optional-tasks)

### [1. Merge conflicts & resolution](./README.md#1-merge-conflicts--resolution)

- PR shows that it had conflicts and was later fixed.
- PR description contains `Conflict resolution note`.

### [2. Add a CI check (GitHub Actions)](./README.md#2-add-a-ci-check-github-actions)

- Workflow file exists under `.github/workflows/`.
- PR has a green check for the lint job.

### [3. Tag and release notes (shipping mindset)](./README.md#3-tag-and-release-notes-shipping-mindset)

- A GitHub Release exists for tag `v0.1.0` and contains release notes.

### [4. Skill spotlight (from job market → deep learning → teach-back)](./README.md#4-skill-spotlight-from-job-market--deep-learning--teach-back)

- `./docs/skill-development-strategy.md` exists and contains a realistic plan (`## Planning`) and progress tracking (`## Tracking`) descriptions.

## Automated checks

### Check - [Lab setup](./README.md#lab-setup)

- Student repo is a public fork of the lab repo.
- The repo has a classmate as a collaborator (check the table).

### [PR reviews](./README.md#pr-reviews)

- Student has reviewed at least 2 PRs.
- Student's PRs have been reviewed.

### Required tasks

#### Check - [1. Pick a product and study its architecture](./README.md#1-pick-a-product-and-study-its-architecture)

- roles per component are outlined (`./docs/roles-and-skills.md`).

#### Check - [2. Tech roles involved in the selected product](./README.md#2-study-the-market-for-your-product)

#### Check - [3. My tech skills and the market: roadmap.sh and job postings](./README.md#3-my-tech-skills-and-the-market-roadmapsh-and-job-postings)

- Job posting links are real.
- `./docs/roles-and-skills.md` has the `## Job market snapshot` section filled in.

### Optional tasks

<!-- TODO -->