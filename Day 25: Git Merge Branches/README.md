📝 DevOps Project Documentation: Day 25
Task: Git Workflow - Feature Branching & Integration
Objective: To integrate a new application frontend (index.html) into the production codebase using a standard feature-branch-to-mainline workflow.

Technical Specifications:
Host: ststor01 (Stratos DC Storage Server)
Repository Path: /usr/src/kodekloudrepos/games
Source Artifact: /tmp/index.html
Branches: nautilus (Feature), master (Production)

🛠️ The Implementation Workflow
Branch Isolation: Created and switched to a new branch named nautilus. This ensures that the staging of the new file does not disrupt the stable master branch during the process.

Artifact Integration: Migrated the index.html file from the temporary storage directory into the repository and recorded the change with a descriptive commit message: Add index.html to nautilus branch.

Merge Execution: Switched back to the master branch and merged the nautilus branch. Because no conflicting changes existed on master, Git performed a Fast-forward merge, which effectively moves the master pointer to the latest commit on the feature branch.

Upstream Synchronization: Executed a push to origin for both branches. This ensures that the remote backup and any automated CI/CD pipelines are aware of the new feature and the updated master state.

