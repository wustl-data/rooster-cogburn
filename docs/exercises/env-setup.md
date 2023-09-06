# Dev Env Setup

Follow these instructions to set up and test your development environment:

## Prepare GitHub

1. Visit our course's [GitHub Organization](https://github.com/wustl-data) and make sure you are a member by confirming the presence of the **fl23** repository in the "pinned" section. If you have not been added, please send your GitHub username in an email to the instructor.

2. Create a repository for your homework submissions by clicking the green "New" button under *Repositories*. Name your repository with your WUSTL username. Select **private** visibility so other students may not see your submissions. Don't add a README, .gitignore, or license file through the UI: these are provided by the class template repo.

3. Make sure you have [Git Credential Manager](https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/install.md) installed. Follow the instructions for your operating system. OSX users should make sure they have [Homebrew](https://brew.sh/) installed, and Windows users should make sure to follow the WSL addendum in the instructions if you are using WSL/Ubuntu.

## Template (upstream) repo --> personal repo


!!! warning "Windows Users"

    A large number third party software libraries, including libraries that are commonly used in this course, assume UNIX-style terminal commands. MacOS and Linux terminals are considered UNIX terminals, but Powershell on Windows is not. As a minor example, if you are using Windows, commands in this documentation like `cd` (change directory) and `rm -rf` (remove all folder contents) might not work.

    Historically, this has often been worked around by either *emulating* a UNIX terminal with a program such as _Git Bash_, or by installing/dual-booting a full Linux/Ubuntu OS alongside your Windows OS.

    However, Windows has recently made it extremely easy to run a fully-featured Linux OS from the Windows Terminal via **Windows Subsystem for Linux (WSL)**.

    Windows users, especially if you think you will be working with local dev containers instead of Codespaces (see considerations [below](#codespaces-cloud-or-local-dev-container)), are **strongly advised** to install the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) for their main terminal, following the documentation for integrating Visual Studio Code, git, and Docker. If this is undesirable for you, you may need to troubleshoot your own installation methods.

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

- **Local Dev Container**: Takes some manual configuration and interfacing with Docker to get set up. Provides the comfort of a stable and accessible home for your code on your machine.

- **Manual setup**: Requires you to manually install all the dependencies on your local machine. This is the most flexible option, but it is also the most time consuming and error prone.

## Clone and open your private repo

=== "Codespaces"

    1. Go to your private repo on GitHub and click the green "Code" button. Select "Open with Codespaces" from the dropdown menu. This will open VS Code with all of the necessary dependencies installed in the environment.

=== "Local Dev Container"

    1. Make sure you have Docker Desktop and VS Code installed. In VS Code, download the Dev Containers extension.

    2. Clone your private repo to your local machine by visiting the repo on GitHub, clicking the green "Code" button, and copying the https URL in the "Local" tab. Then, in your terminal, run `git clone <url>` to clone the repo to your local machine. This will create a folder named after your repo in your terminal's current directory.

    3. Open the repo in VS Code.

        === "OSX"
            Use the GUI to open the folder containing the repo you just cloned.

        === "WSL"
            `cd` to the repo directory and run `code .` to open the repo in VS Code.

    4. When VS Code opens, it should prompt you to open the folder in a Dev Container. Accept the prompt and wait for the container to build. This may take a few minutes the first time. If you miss the prompt, you can open the command palette (Ctrl+Shift+P) and search for "Reopen in Container".

## Switch to the `hw0-upstream` branch and create a `hw0` branch

1. Run `git branch -a` to list all of your remote and local branches. `remotes/origin/hw0-upstream` should be listed.
2. Create a local version of the `hw0-upstram` branch and switch to it.

    Run `git switch -t origin/hw0-upstream` to create and switch to the contents of the upstream branch. Now, run `git switch -c hw0` to create a new branch named `hw0` off of your current branch and switch to it. The `-c` part of the command is the `create` flag for the `git switch` command. Finally, run `git push -u origin hw0` to push the branch to your origin (private) repo. The `-u` flag sets the upstream branch for your local branch, so that you can use `git pull` and `git push` without specifying the branch name.

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

3. Run `pytest` again to see if your test output is any different from before.

## Commit and push your changes

Use git commands to stage (`git add`) and commit (`git commit`) your changes. Use `git status` to see what files have been changed and what files are staged for commit, use `git log` to see the commit history, and use `git diff` to see the changes you've made since your last commit.


9. Complete the example assigment by implementing a function that returns a blank dataframe. If you're not sure how to proceed, try deducing next steps from your test output. Add, commit, and push (`git push`) your changes  to your private repo.

    !!! tip "Git GUI"

        Although it's good to know how to use git from the command line, you may find it easier to use a GUI. VS Code has a built-in git GUI, and GitHub Desktop can be a helpful interface for non-WSL users.

10. Check your repo on GitHub. Go to the "Actions" tag and make sure the checks are passing!

## Improve your test

1. Modify the test provided to check for a filter condition.
2. Commit and push your changes to your private repo.

The workflow run in your Actions tab on GitHub should be **red**. We will turn this test green with the exercise on Thursday.
