# Dev Env Setup

Follow these instructions to set up and test your development environment:

## Prepare GitHub

1. Visit our course's [GitHub Organization](https://github.com/wustl-data) and make sure you are a member by confirming the presence of the **fl23** repository in the "pinned" section. If you have not been added, please send your GitHub username in an email to the instructor.

2. Create a repository for your homework submissions by clicking the green "New" button under *Repositories*. Name your repository with your WUSTL username. Select **private** visibility so other students may not see your submissions. Don't add a README, .gitignore, or license file through the UI: these are provided by the class template repo.

## Template (upstream) repo --> personal repo


!!! warning "Windows Users"

    If you are using Windows, commands like `cd` (change directory) and `rm -rf` (remove all folder contents) might not work in Powershell or the Windows Command Line. Windows users are advised to install the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) for their main terminal, following the documentation for integrating Visual Studio Code, git, and Docker. If this causes you trouble, git bash is an acceptable short-term solution for this exercise. Finally, if you are stuck using Powershell or cmd, you can tailor these instructions to perform the appropriate filesystem commands (cd, rm, etc.) as necessary.

1. Populate your private repo with the code from the upstream repository by executing the following commands in your terminal.

    1. Clone the template repo to a temporary folder named `fl23.git`:

        ```bash
        git clone --bare https://github.com/wustl-data/fl23
        ```

        ```mermaid
        flowchart LR
        template([fl23]) -->|clone| local([Your Local Repo])
        ```

    2.  Move your _current directory_ to the cloned repo's folder

        ```bash
        cd fl23.git
        ```

    3.  Push a version of the repo to your private repo, replacing `<your wustl username>` with your actual WUSTL username to match the repo you created earlier.

        ```bash
        git push --mirror https://github.com/wustl-data/<your wustl username>
        ```

        ```mermaid
        flowchart LR
        template([fl23])--> local([Your Local Repo])
        local-->|push| origin([Your Private GH Repo])
        ```

    4.  Go back to your original working directory (`..` goes up one level in the filesystem hierarchy).

        ```bash
        cd ..
        ```

    5.  Delete your local version of the template repo

        ```bash
        rm -rf fl23.git
        ```

        ```mermaid
        flowchart LR
        origin([Your Private GH Repo])
        ```

## Codespaces (cloud) or local dev container?

Choose whether to work on the cloud in a Codespaces environment or on your local machine and follow the appropriate instructions for the rest of this exercise. You might want to try both and see which one you like better, and you may switch between the two options at any time.

Here are some considerations:

- **Cloud (Codespaces)**: No manual setup needed -- You can launch a codespace from any code branch within the GitHub UI. By default, VS Code opens in the browser, but you can open the code in your desktop version at any time through menu options. Codespaces are free for the class. You can keep your work preserved and easily access your environment on different machines, even across different branches of code, and you can have multiple instances of your environment running at once. However, you will need to be connected to the internet to work on your code. Frequently, GitHub's servers are fast enough to outperform personal computers for computation.

- Local Dev Container: Takes some manual configuration and interfacing with Docker to get set up. Provides the comfort of a stable and accessible home for your code on your machine.

- Manual setup: Requires you to manually install all the dependencies on your local machine. This is the most flexible option, but it is also the most time consuming and error prone.

## Clone your private repo

=== "Codespaces"

    1. Go to your private repo on GitHub and click the green "Code" button. Select "Open with Codespaces" from the dropdown menu. This will open VS Code with all of the necessary dependencies installed in the environment.
    2. Run `git branch -a` to list all of your remote and local branches. `remotes/origin/hw0-upstream` should be listed.
    3. Create a local version of the `hw0-upstram` branch and switch to it.

        Run `git switch -t origin/hw0-upstream` to create and switch to the contents of the upstream branch. Now, run `git switch -c hw3` to create a new branch named `hw3` off of your current branch and switch to it. The `-c` part of the command is the `create` flag for the `git switch` command. Finally, run `git push -u origin hw3` to push the branch to your origin (private) repo. The `-u` flag sets the upstream branch for your local branch, so that you can use `git pull` and `git push` without specifying the branch name.

=== "Local Dev Container"

    1. Make sure you have Docker Desktop and VS Code installed. In VS Code, download the Dev Containers extension.

    2. Clone your private repo to your local machine by visiting the repo on GitHub, clicking the green "Code" button, and copying the https URL in the "Local" tab. Then, in your terminal, run `git clone <url>` to clone the repo to your local machine. This will create a folder named after your repo in your terminal's current directory.

    3. Open the repo in VS Code.

        === "OSX"
            Use the GUI to open the folder containing the repo you just cloned.

        === "WSL"
            `cd` to the repo directory and run `code .` to open the repo in VS Code.

## Test your assignment

1. Run the following commands in the terminal to test your setup:

    ```bash
    pytest
    ```

    This should show a failing test

    ```
    pre-commit run --all-files

    ```

    This should run our _pre-commit hooks_ which will help provide you with code feedback before you commit your code. If you need to, get your code to pass the checks before continuing.

2. Add pandas to your project's dependencies.

    ```bash
    poetry add pandas
    ```

Run `pytest` again to see if your test output is any different from before.

Use git commands to stage (`git add`) and commit (`git commit`) your changes. Use `git status` to see what files have been changed and what files are staged for commit, use `git log` to see the commit history, and use `git diff` to see the changes you've made since your last commit.


9. Complete the example assigment by implementing a function that returns a blank dataframe. If you're not sure how to proceed, try deducing next steps from your test output. Add, commit, and push your changes to your private repo.

10. Check your repo on GitHub. Go to the "Actions" tag and make sure the checks are passing. If they are, you are done with the exercise!
