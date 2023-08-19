# Setting up a GitHub Repo locally with CLI and Push the excisting content

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
   1. gh repo create <repository> --public --confirm
   2. gh repo create <repository> --private --confirm
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