# Welcome to the IXI Lab GitHub Organization

This document is the official guide for all members of the IXI Lab on how we use GitHub to conduct our research. Our goal is to make our work more **collaborative**, **reproducible**, and **transparent**.

This guide is divided into four parts:
1. **Onboarding Guide for All Members:** Essential first steps for everyone.
2. **The Team Member Handbook:** The day-to-day workflow for contributing to a research project.
3. **The Team Leader Guide:** Responsibilities for those managing a specific project.
4. **The Owner's Manual:** Administrative tasks for the PI and lab managers.

---

## Part 1: Onboarding Guide for All Members

Welcome to the lab! This section will get you set up and ready to contribute.

### Our Roles

We have three main roles in this organization to keep things running smoothly:

* **Member:** The standard role for all researchers. You will be added to specific project teams to contribute to repositories.
* **Team Leader:** A senior researcher or postdoc responsible for managing a specific project team and its repositories. They are your first point of contact for project-specific questions.
* **Owner:** The PI and designated lab managers. They handle organization-wide settings, billing, and the creation of new projects.

### Your First Steps: A Checklist

1. **Accept Your Invitation:** You will receive an email invitation to join the IXI-Lab organization. Please accept it.
2. **Enable Two-Factor Authentication (2FA):** 🔐 This is **mandatory** for all members. Before you can be added to any projects, you must enable 2FA on your GitHub account for security. Go to your GitHub **Settings > Password and authentication** to enable it.
3. **Get Assigned to a Team:** Once your 2FA is active, an Owner or Team Leader will add you to your project team (e.g., `project-neurovision-team`). This will grant you access to the project's repositories.

### The Golden Rule: Issues and Pull Requests

All work, discussions, and requests in this lab are handled through GitHub Issues and Pull Requests.

* **Issues:** Used to track tasks, report bugs, ask questions, or propose new ideas. Think of it as our lab's task list and discussion forum.
* **Pull Requests (PRs):** Used to submit your work (code, analysis, manuscript edits) for review before it is merged into the official `main` branch of a project. **Directly pushing to the `main` branch is disabled.**

This system ensures every change is reviewed and documented, which is critical for scientific integrity.

---

## Part 2: The Team Member Handbook

This is your guide to the daily research workflow.

### The Standard Workflow

Every piece of work, from fixing a typo to adding a new analysis, follows this five-step process:

1. **Find or Create an Issue:** Go to your project repository's "Issues" tab. Find the task you need to work on. If it doesn't exist, create one using our templates (e.g., "🐞 Bug Report"). You will be assigned to the issue.
2. **Create a Branch:** From the repository's main page, create a new branch. Name your branch descriptively, including the issue number. For example: `feature/12-add-new-visualization`.
3. **Do the Work & Commit:** Make your changes locally on your new branch. As you work, make small, logical commits with clear messages (e.g., `git commit -m "feat: Add plotting function for trial data"`).
4. **Open a Pull Request (PR):** When your work is ready for review, push your branch to GitHub and open a Pull Request.
   * The PR template will appear automatically. Please fill it out.
   * In the description, link the issue it resolves by writing `Closes #12`.
   * Assign your Team Leader as a reviewer.
5. **Participate in the Review:** Your Team Leader or another member will review your code. They may approve it or request changes. Respond to comments, make necessary edits, and push the changes to your branch. The PR will update automatically. Once approved, your work will be merged into `main`.

### Data Management Policy

❗️ **Never commit large data files, credentials, or sensitive information to Git.**

* **Raw Data:** Raw data should be stored on the university server or another designated permanent storage location. The `README.md` in the `/data/` folder should explain how to access it.
* **Large Files:** For medium-sized files that need to be versioned (like a trained model), ask your Team Leader about using Git LFS (Large File Storage).
* **Credentials:** API keys, passwords, and other secrets should never be in your code. Ask a Team Leader about using environment variables or other secure methods.

### Best Practices for Research Code

#### Code Quality Standards

* **Documentation:** Every function should have a clear docstring explaining what it does, its parameters, and return values.
* **Type Hints:** Use Python type hints to make your code more readable and catch errors early.
* **Testing:** Write unit tests for your functions. Aim for at least 80% test coverage.
* **Style:** Follow PEP 8 style guidelines. Use tools like `black` and `flake8` to maintain consistency.

#### Reproducibility Standards

* **Environment Management:** Always include `environment.yml` or `requirements.txt` files.
* **Random Seeds:** Set random seeds for all stochastic processes to ensure reproducibility.
* **Version Control:** Commit frequently with descriptive messages.
* **Dependencies:** Pin specific versions of packages in your environment files.

#### Analysis Workflow

1. **Data Loading:** Use the provided utility functions in `src/utils.py` for loading and saving data.
2. **Exploratory Analysis:** Start with the functions in `src/analysis.py` for standard analyses.
3. **Results Management:** Save all results to the `results/` directory with timestamps.
4. **Documentation:** Update the project README and create analysis reports.

### Common Commands and Workflows

#### Setting Up a New Project

```bash
# Clone the repository
git clone <repository-url>
cd <project-name>

# Set up the environment
conda env create -f environment.yml
conda activate <project-name>

# Install the project package
pip install -e .
```

#### Daily Workflow

```bash
# Start working on a new feature
git checkout -b feature/issue-number-description

# Make changes and commit
git add .
git commit -m "feat: Add new analysis function"

# Push and create PR
git push origin feature/issue-number-description
```

#### Updating Your Work

```bash
# Get latest changes from main
git checkout main
git pull origin main

# Update your feature branch
git checkout feature/your-branch
git rebase main
```

---

## Part 3: The Team Leader Guide

As a Team Leader, you are a project manager. Your primary responsibilities are to guide your project's scientific direction and ensure a high standard of code and analysis quality.

### Managing Your Team

* **Adding/Removing Members:** You have "Maintainer" permissions on your team. This allows you to add existing organization members to your team or remove them. Go to the organization's **Teams** page, find your team, and manage its membership.
* **Assigning Tasks:** Use the "Issues" tab as your project management board. Triage new issues, add descriptive labels, and assign them to team members.

### Reviewing Pull Requests

This is your most important task. Your role is not just to find errors but to mentor and improve the lab's overall code quality.

* **Review Promptly:** Try to provide feedback on PRs within 1-2 business days.
* **Be Constructive:** Explain *why* a change is needed. Offer suggestions and praise good work.
* **Check for Reproducibility:** Does the code run? Is the documentation clear? Does it follow the lab's data management policy?
* **Merge with Confidence:** Once you are satisfied with the changes and any automated checks have passed, you can merge the Pull Request.

### Project Management Responsibilities

#### Issue Management

* **Triage Issues:** Regularly review and categorize new issues.
* **Set Priorities:** Use labels to indicate priority levels and issue types.
* **Assign Work:** Distribute tasks among team members based on their expertise and availability.
* **Track Progress:** Use project boards or milestones to track project progress.

#### Code Quality Assurance

* **Review Standards:** Ensure all code follows the lab's coding standards.
* **Testing:** Verify that new code includes appropriate tests.
* **Documentation:** Check that documentation is updated with code changes.
* **Performance:** Review code for efficiency and scalability.

#### Team Communication

* **Regular Check-ins:** Schedule regular team meetings to discuss progress and challenges.
* **Knowledge Sharing:** Encourage team members to share their expertise and learn from each other.
* **Mentorship:** Provide guidance and support to junior team members.

### Technical Leadership

#### Architecture Decisions

* **Design Reviews:** Review and approve major architectural changes.
* **Technology Choices:** Make decisions about new tools, libraries, or frameworks.
* **Integration:** Ensure new components integrate well with existing systems.

#### Quality Control

* **Automated Checks:** Set up and maintain CI/CD pipelines for automated testing.
* **Code Reviews:** Establish and enforce code review processes.
* **Performance Monitoring:** Monitor and optimize code performance.

---

## Part 4: The Owner's Manual

This section is for the PI and designated lab administrators. Your role is to manage the organization's structure, security, and finances.

### Core Administrative Tasks

#### Onboarding a New Lab Member

1. Go to the organization's **People** tab and click "Invite member."
2. Once they accept, verify they have enabled 2FA. Their profile in the organization list will show a "2FA" shield icon.
3. Notify the relevant Team Leader(s) that the new member can now be added to their project team(s).

#### Creating a New Project

1. This process is initiated when a "🚀 New Research Project Proposal" issue is approved.
2. Click the `+` icon on the organization's main page and select "New repository."
3. In the "Repository template" dropdown, select `research-project-template`.
4. Name the new repository (e.g., `ixi-project-gamma`) and ensure it is set to **Private**.
5. Go to the **Teams** tab, create a corresponding team (e.g., `project-gamma-team`), and assign the designated Team Leader(s) the **Maintainer** role for that team.
6. Go to the new repository's **Settings > Collaborators and teams**, add the new team, and grant it **Write** access.

#### Archiving a Completed Project

1. When a project is finished and published, its repository should be made read-only to preserve its state.
2. Go to the repository's **Settings**, scroll to the bottom to the "Danger Zone," and click "Archive this repository."

#### Security Audits (Quarterly)

1. Go to **Organization settings > Security** and ensure that the "Require two-factor authentication" policy is active.
2. Briefly review the Audit Log for any unusual activity.

### Organization Management

#### Repository Templates

* **Maintain Templates:** Keep the `research-project-template` updated with the latest best practices.
* **Customize Templates:** Create specialized templates for different types of projects (e.g., data analysis, machine learning, computational modeling).
* **Documentation:** Ensure all templates include comprehensive documentation and examples.

#### Access Control

* **Role Management:** Regularly review and update team memberships and permissions.
* **Security Policies:** Enforce security policies and monitor compliance.
* **Backup Access:** Maintain backup access for critical repositories in case of emergencies.

#### Billing and Resources

* **GitHub Plans:** Monitor GitHub usage and manage billing for premium features.
* **Storage Management:** Monitor repository sizes and manage storage limits.
* **Resource Allocation:** Allocate resources (compute, storage, etc.) across projects.

### Strategic Planning

#### Research Direction

* **Project Portfolio:** Maintain an overview of all active projects and their status.
* **Resource Planning:** Plan resource allocation for upcoming projects.
* **Collaboration Opportunities:** Identify opportunities for collaboration between projects.

#### Technology Strategy

* **Tool Evaluation:** Evaluate and adopt new tools and technologies.
* **Standardization:** Establish and maintain coding standards and best practices.
* **Training:** Organize training sessions for new tools and methodologies.

#### Compliance and Ethics

* **Data Privacy:** Ensure compliance with data privacy regulations.
* **Ethical Review:** Oversee ethical considerations in research projects.
* **Open Science:** Promote open science practices and data sharing policies.

---

## Appendix: Quick Reference

### Issue Templates

* **🐞 Bug Report:** For reporting errors or unexpected behavior
* **✨ Feature Request:** For proposing new features or improvements
* **📚 Documentation:** For documentation updates and improvements
* **🧪 Analysis Request:** For requesting new analyses or investigations
* **🚀 New Research Project Proposal:** For proposing new research projects

### Branch Naming Conventions

* `feature/issue-number-description` - New features
* `bugfix/issue-number-description` - Bug fixes
* `docs/issue-number-description` - Documentation updates
* `refactor/issue-number-description` - Code refactoring
* `test/issue-number-description` - Test additions or updates

### Commit Message Format

```
type(scope): description

[optional body]

[optional footer]
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### Labels

* **Priority:** `high`, `medium`, `low`
* **Type:** `bug`, `enhancement`, `documentation`, `question`
* **Status:** `in-progress`, `review-needed`, `blocked`
* **Component:** `analysis`, `data`, `visualization`, `documentation`

---

## Getting Help

If you have questions or need assistance:

1. **Check the Documentation:** Review this guide and project-specific README files.
2. **Ask Your Team Leader:** For project-specific questions and guidance.
3. **Create an Issue:** Use the "❓ Question" template for general questions.
4. **Lab Meetings:** Bring up questions during regular lab meetings.

Remember: The goal is to make our research more collaborative, reproducible, and transparent. Every contribution, no matter how small, helps us achieve this goal.

---

*Last updated: [Current Date]*
*Version: 1.0*
