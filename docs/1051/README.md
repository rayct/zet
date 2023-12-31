# GITHUB STUFF - 2023

## Setting up a GitHub Repo locally with CLI and Push the excisting content


Setting up the GitHub CLI (Command Line Interface) involves a few steps to ensure that it's configured correctly on your system. The GitHub CLI allows you to interact with GitHub repositories and perform various actions directly from your terminal. Here's how you can set it up correctly:

1. **Install GitHub CLI:**

   If you haven't already, you need to install the GitHub CLI on your system. You can download and install it from the official GitHub CLI repository: https://github.com/cli/cli

   Follow the installation instructions for your operating system.

2. **Authenticate GitHub CLI:**

   After installing the GitHub CLI, you need to authenticate it with your GitHub account. Open your terminal and run the following command:

   ```
   gh auth login
   ```

   This will guide you through the authentication process. You can choose to authenticate using your GitHub username and password, a Personal Access Token, or by using the browser. Follow the prompts to complete the authentication.

3. **Configure Repository Context:**

   Once you're authenticated, you can configure the default repository context. This means that you can set a default repository to work with. This can be particularly useful if you work with a specific repository frequently.

   To set the default repository context, use the following command:

   ```
   gh repo set-default
   ```

   Follow the prompts to select the repository you want to set as the default.

4. **Start Using GitHub CLI:**

   With authentication and configuration completed, you can start using GitHub CLI commands to interact with repositories. Some common commands include:

   - Creating a new repository: `gh repo create`
   - Cloning a repository: `gh repo clone <repository>`
   - Creating a new issue: `gh issue create`
   - Creating a pull request: `gh pr create`
   - Listing issues: `gh issue list`
   - Checking out a pull request: `gh pr checkout <pull-request-number>`
   - Delete a Repo: `gh repo delete <repository`

5. **To delete a GitHub repository using the GitHub CLI (Command Line Interface), you can use the following command:**

```sh
gh repo delete <repository>
```

Replace `<repository>` with the name of the repository you want to delete. Keep in mind that this action is irreversible and will permanently delete the repository and all its associated data, including issues, pull requests, and code.


*More commands and their explanations in the GitHub CLI documentation: <https://cli.github.com/manual/>*

Remember to replace placeholders like `<repository>` and `<pull-request-number>` with actual repository names and pull request numbers.

By following these steps, you should be able to set up and use GitHub CLI correctly on your system. Always refer to the official GitHub CLI documentation for the latest information and updates.

---


## Create a new repository directly from the command line using the GitHub CLI tool and then push your existing content to it:

1. **Install GitHub CLI:**
   If you haven't already, install the GitHub CLI tool as mentioned earlier.

2. **Authenticate with GitHub:**
   If you haven't authenticated with GitHub using the CLI tool, run:
   ```bash
   gh auth login
   ```

3. **Create a New Repository:**
   To create a new repository and push existing content to it, follow these steps:

   a. Navigate to the directory of your existing project that you want to turn into a repository.
   ```bash
   cd /path/to/your/existing/project
   ```

   b. Initialize a Git repository if your project isn't already a Git repository.
   ```bash
   git init
   ```

   c. Add and commit your existing content.
   ```bash
   git add .
   git commit -m "Initial commit"
   ```

   d. Use the GitHub CLI to create a new repository. Replace `<repository>` with your desired repository name.
   ```bash
   1. gh repo create <repository>
   2. gh repo create <repository> --public --confirm
   3. gh repo create <repository> --private --confirm
   ```

   This command will create a new repository on GitHub with the provided name, set it as public or private, and confirm the action.

4. **Push Existing Content:**
   Once the repository is created, you can set the remote origin and push your existing content to it.

   a. Add the remote repository as the origin. Replace `<username>` with your GitHub username and `<repository>` with the repository name.
   ```bash
   git remote add origin git@github.com:<username>/<repository>.git
   ```

   b. Push your local content to the remote repository's master branch. If you're using a different branch, replace `master` with the appropriate branch name.
   ```bash
   git push -u origin master
   ```

Now you've created a new repository using the GitHub CLI and pushed your existing content to it. Make sure you have the necessary permissions and SSH keys set up correctly to interact with the remote repository.

---

## Setting up a GitHub Repo locally with CLI

Create a new repository directly from the command line using the GitHub CLI tool.
This tool allows you to interact with GitHub repositories, issues, pull requests, and more, all from your terminal. Here's how you can use it to create a new repository:

1. **Install GitHub CLI:**
   If you haven't already, you need to install the GitHub CLI tool. You can download it from the GitHub CLI repository: https://github.com/cli/cli

2. **Authenticate with GitHub:**
   After installing, you need to authenticate the CLI tool with your GitHub account. Run the following command and follow the prompts:
   ```bash
   gh auth login
   ```

3. **Create a New Repository:**
   Once authenticated, you can create a new repository with the `gh repo create` command. Replace `<repository>` with your desired repository name:
   ```bash
   1. gh repo create <repository>
   2. gh repo create <repository> --public --confirm
   3. gh repo create <repository> --private --confirm
   ```

   This command will prompt you to provide various details for your repository, such as its visibility (public or private), description, and whether you want to initialize it with a README, license, etc.

4. **Clone the Repository:**
   After the repository is created, you can clone it to your local machine using Git:
   ```bash
   git clone git@github.com:<username>/<repository>.git
   ```

5. **Navigate to the Repository:**
   Use the `cd` command to navigate into your newly cloned repository directory:
   ```bash
   cd <repository>
   ```

Now you have a new repository created on GitHub directly from the command line.

This method can save you some time compared to manually creating a repository on GitHub's website and then setting up the remote locally. Just make sure you have the GitHub CLI installed and authenticated properly.

## To add a GitHub license to your repository from the command line interface (CLI), you can use the GitHub API to create a new license file. Here's a general outline of the steps you would need to follow using tools like `curl`:

1. **Choose a License**: Decide which license you want to add to your repository. Common licenses include MIT, Apache, GPL, etc.

2. **Generate License Text**: If the license you've chosen requires specific text to be included in the license file, generate or obtain that text.

3. **Create a New File**: You will use the GitHub API to create a new file with the license text. You will need to provide your GitHub repository name, owner, and authentication token.

Here's an example of how you could do this using `curl`:

```bash
# Set your GitHub repository information
REPO_OWNER="your_username"
REPO_NAME="your_repository"
LICENSE_NAME="LICENSE"  # The name of the license file, typically LICENSE

# Set your GitHub Personal Access Token
GITHUB_TOKEN="your_personal_access_token"

# Choose the license you want to add (replace with your desired license text)
LICENSE_TEXT=$(cat <<EOL
MIT License

...

EOL
)

# Create the license file using the GitHub API
curl -X PUT \
  -H "Authorization: token $GITHUB_TOKEN" \
  -d "{\"message\":\"Add license\",\"content\":\"$(echo -n "$LICENSE_TEXT" | base64 -w 0)\"}" \
  "https://api.github.com/repos/$REPO_OWNER/$REPO_NAME/contents/$LICENSE_NAME"
```

Remember to replace placeholders like `your_username`, `your_repository`, `your_personal_access_token`, and the `LICENSE_TEXT` with your actual information.

Also, be cautious with your personal access token as it grants access to your repository. Make sure to keep it secure and do not share it publicly.

Please note that this is a simplified example, and there are additional considerations such as error handling, license compatibility, and different license formats. Always review the GitHub API documentation for the most up-to-date information.


## gh config

* `gh config list`
* `gh config set`
* `gh config get`
* `gh config`

## Github Export Key
4. Export GPG_TTY environment variable: If the `--no-tty` flag doesn't work, try setting the `GPG_TTY` environment variable to point to your current TTY. This might help GPG locate the correct terminal and avoid the error.

   ```
   export GPG_TTY=$(tty)
   ```


## .gitignore

The `.gitignore` file is used to specify which files and directories should be ignored by Git when tracking changes in a repository. If you want to prevent changes to the `.gitignore` file itself from being committed and contributed to the repository, you can follow these steps:

1. **Stage your changes selectively:** Instead of using `git add .` or `git add -A` to stage all changes, manually stage only the files you want to commit. This way, you can exclude changes to the `.gitignore` file.

    ```bash
    git add file1.txt file2.txt # Add the files you want to commit
    ```

2. **Check your staging area:** You can use `git status` to see which files are staged for commit. Ensure that the changes to the `.gitignore` file are not included in this list.

    ```bash
    git status
    ```

3. **Commit your changes:** Once you've staged the necessary changes, commit them.

    ```bash
    git commit -m "Your commit message here"
    ```

Changes to the `.gitignore` file will not be included in this commit.

4. **Use `--skip-worktree` (Advanced):** If you want to ignore changes to the `.gitignore` file on an ongoing basis, you can use the `--skip-worktree` flag. This will mark the file as "assume unchanged," effectively ignoring any changes you make to it. However, be cautious with this approach as it's not a standard practice and might have some limitations.

    To set the `--skip-worktree` flag:

    ```bash
    git update-index --skip-worktree .gitignore
    ```

Remember that the `.gitignore` file is often part of a project's configuration and should be consistent across collaborators. If you find yourself frequently needing to modify the `.gitignore` file, it might be worth discussing the changes with your team to ensure everyone is on the same page.

Lastly, if you're concerned about accidentally committing changes to the `.gitignore` file, you can use pre-commit hooks or CI/CD pipelines to automate checks that prevent such commits. This would add an extra layer of protection and prevent the changes from being pushed to the repository.


## Undo Last commit

To undo the last commit you made, you have a couple of options. The right choice depends on whether you want to completely remove the commit or if you just want to make changes to it and create a new commit.

1. **Undo the commit but keep the changes as unstaged:**
   
   If you want to keep the changes you made in the last commit but undo the commit itself, you can use the following commands:

   ```bash
   git reset HEAD^
   ```

   This will remove the most recent commit while keeping the changes in your working directory. The changes will be unstaged, allowing you to make further adjustments before committing again.

2. **Completely remove the last commit:**

   If you want to completely remove the last commit along with the changes, you can use the following command:

   ```bash
   git reset --hard HEAD^
   ```

   This will remove the last commit and all changes associated with it.

Please be cautious when using the `--hard` option, as it will discard all changes without the possibility of recovery. Make sure you have a backup or are certain you want to permanently remove those changes.

Remember that if you've already pushed the commit to a remote repository, you might need to coordinate with your team to handle the removal properly and avoid causing issues for others.

As a general note, if you find yourself needing to frequently undo commits or modify history, consider using more localized branches or creating smaller commits that are easier to manage.

---

Documentation By: **Raymond C. TURNER**

Last Updated: Monday 28th August 2023 @ 19:43 BST