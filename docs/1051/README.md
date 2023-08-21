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

   You can find more commands and their explanations in the GitHub CLI documentation: https://cli.github.com/manual/

Remember to replace placeholders like `<repository>` and `<pull-request-number>` with actual repository names and pull request numbers.

By following these steps, you should be able to set up and use GitHub CLI correctly on your system. Always refer to the official GitHub CLI documentation for the latest information and updates.


Create a new repository directly from the command line using the GitHub CLI tool and then push your existing content to it:

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


---

Documentation by: **Raymond C. TURNER**

Last Updated: 1 Day ago