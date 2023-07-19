# IronHack Git-Workflow

1. What is the purpose of the Feature Branch Workflow in Git?
    - To provide a structured way to do software development. It allows multiple developers to work on different features or tasks concurrently without interfering with each other's work. Each feature or task is developed in its own branch, called a feature branch
2. How do you set up a new Git repository for your project?
    - Initialize a new Git repository in the project directory using the command: `git init`.
    - Add project files to the Git repository using the command: `git add .`
    - Commit the initial state of the project using the command: `git commit -m "Initial commit"`.
    - Optionally, you can set up a remote repository and connect it to your local repository using the command: `git remote add origin <repository URL>`.
3. What is the main branch in the Feature Branch Workflow?
    - In the Feature Branch Workflow, the main branch is often referred to as the "master" branch or, more recently, the "main" branch. It represents the stable and production mirror version of the code.
4. How do you create a new branch for a specific feature or task?
    - Using the following command:  `git branch <branch-name>` and `git checkout <branch-name>` or as a shortcut `git checkout -b <branch-name>`. 
5. How do you switch to a different branch in Git?
    - With the command: `git checkout <branch-name>`. you can to navigate between branches and work on different features.
6. How do you make changes and track your progress in the feature branch?
    - with these steps:
        - Switch to the feature branch using the command: `git checkout <feature-branch>`.
        - Make the necessary changes to the code
        - Add the modified files to the staging area using the command: `git add .`
        - Commit the changes to the feature branch using the command: `git commit -m "feat: new changes"`.
7. How do you merge a feature branch into the main branch?
    - with these steps:
        - in local
            - Switch to the main branch using the command: `git checkout main`.
            - Ensure that the main branch is up to date by pulling the latest changes from the remote repository: `git pull origin main`.
            - Merge the feature branch into the main branch using the command: `git merge <feature-branch>`.
            - Resolve any merge conflicts that may arise during the merge process.
            - Commit the merge changes to finalize the integration of the feature branch into the main branch.
        - in github
            - Create a pull request from the feature branch to the main branch
            - Add relevant description of the changes
            - Add reviewers
            - Wait the review from reviewers and maybe CI integration pass
            - In case of comments from the reviewers, resolve them
            - If the comments are resolved and re-approved, merge the PR
            - Optionally, you can delete the feature branch, and personally I prefer to do it to maintain healthy the github tree
8. What should you do if there are merge conflicts during the merge process?
    - it means that there are conflicting changes in the files being merged. To resolve merge conflicts, I manually edit the conflicting files to choose the desired changes. so I stage the changes using git add and then complete the merge by committing the changes.
9. Why is it important to test the merged codebase after completing the merge?
    - To ensure that the integrated changes from the feature branch work correctly with the existing codebase. Testing helps identify any issues or regressions introduced by the merge
10. What are some additional challenges you can undertake to enhance your understanding of the Feature Branch Workflow?
    - Practicing working on multiple feature branches simultaneously and merging them independently.
    - Experimenting with branching strategies, such as branching off feature branches for further isolation or using long-running release branches.
    - Collaborating with other developers on a shared repository and simulate a real features development.
    - Working differents features with other developers but both of us using shared utilities to practice merge conflicts
11. How do you delete a feature branch after merging it into the main branch?
    - I commonly delete the feature branch from github button, and also I always like to work with Gitkraken IDE, it easily can sync the local branch to the remotes, but in a local environment it could be:
    - using the command: `git branch -d <feature-branch>` to delete local branch and `git push <remote> --delete <feature-branch>` to delete the branch remotely.
12. What is the purpose of code reviews in the Feature Branch Workflow?
    - To ensure the quality, correctness, and maintainability of the codebase, and also to Improve the analysis, good practices, knowledge of the reviewers since, in order to give feedback you need to know a lot or at least had a nice knowledge from the topic or good practices.
13. How do you push your feature branch to a remote repository?
    - With the command: `git push -u origin <feature-branch>`. This command pushes the feature branch to the remote repository and sets it as the upstream branch, allowing you to easily push future changes to the same branch using `git push` without specifying the branch name.
14. What is the recommended approach for naming feature branches in the Feature Branch Workflow?
    - Using descriptive and meaningful names that reflect the purpose of the feature or task. It is common to prefix the branch name with a specific identifier, such as "feature/" or "task/", followed by a concise and informative name. For example, a feature branch for implementing user authentication could be named "feature/user-authentication" or simply "feature/auth". but, I had work in companies with standards like adding the jira ticket to the github branch name, like "feature/DTSC-160-user-authentication"
15. How can you keep your feature branch up to date with the latest changes from the main branch?
    - I think there diferents strategies, using merge commits or rebase
    - with merge:
        - Switch to the main branch using the command: `git checkout main`.
        - Sync the origin changes: `git fetch origin`.
        - Pull the latest changes from the remote main branch using the command: `git pull origin main`.
        - Switch back to your feature branch using the command: `git checkout <feature-branch>`.
        - Merge the changes from the main branch into your feature branch using the command: `git merge main`.
        - Resolve any merge conflicts, if any, that arise from the merge process.
        - Commit the merge changes to update your feature branch with the latest changes from the main branch.
    - with rebase:
        - Switch to the main branch using the command: `git checkout main`.
        - Sync the origin changes: `git fetch origin`.
        - Pull the latest changes from the remote main branch using the command: `git pull origin main`.
        - Switch back to your feature branch using the command: `git checkout <feature-branch>`.
        - Rebase the feature branch to the main branch using the command: `git rebase main`.
        - Resolve any rebase conflicts, and continue with the rebase using the command `git rebase --continue`.
        - Push the rebased feature branch using the command `git push -f` (since the history of the branch is overwritten you need to force the push).
    - I personally prefer the rebase approach to maintain an easy view of github branches tree



