# Setting up a GitHub Repo from CLI

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
   gh repo create <repository>
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