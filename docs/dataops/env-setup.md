# Dev Env Setup

Follow these instructions to set up and test your development environment:

1. Make sure you have access to the [GitHub Organization](https://github.com/wustl-data/).
2. Create a private repo named as your WUSTL username in the `wustl-data` GitHub Organization using the GitHub UI.
    - Don't add a README or .gitignore through the UI, these are provided by the template repo.
3. Make sure you can view the _upstream_ version of the [course repository](https://github.com/wustl-data/fl23)
4. Populate your private repo with the code from the upstream repository as follows:
    1. Clone the template repo

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

    3.  Push a version of the repo to your private repo

        ```bash
        git push --mirror https://github.com/wustl-data/<your wustl username>
        ```

        ```mermaid
        flowchart LR
        template([fl23])--> local([Your Local Repo])
        local-->|push| origin([Your Private GH Repo])
        ```

    4.  Go back to your original working directory

        ```bash
        cd ..
        ```

    5.  Delete your local version of the template repo

        ```bash
        rm -rf fl23
        ```
        ```mermaid
        flowchart LR
        origin([Your Private GH Repo])
        ```

5. Choose whether to work on the cloud in a Codespaces environment or on your local machine and follow the appropriate instructions for the rest of this exercise. Here are some considerations:
    - Cloud (Codespaces): No manual setup needed -- just click "open a codespace" on whichever branch you have open in GitHub. Codespaces are free for the class. You can keep your work preserved and easily access your environment on different machines, and you can have multiple instances of your environment running at once. However, you will need to be connected to the internet to work on your code. Generally, GitHub's servers are fast enough to frequently outperform personal computers for computation.

    - Local Dev Container: Takes some manual configuration and interfacing with Docker to get set up. Provides the comfort of a stable and accessible home for your code on your machine.

    - Manual setup: Requires you to manually install all the dependencies on your local machine. This is the most flexible option, but it is also the most time consuming and error prone.

6. Then run `git switch -t origin/hw0-upstream` to create and switch to the contents of the upstream branch. Now, run `git switch -c hw3` to create a new branch named `hw3` off of your current branch and switch to it. The `-c` part of the command is the `create` flag for the `git switch` command. Finally, run `git push -u origin hw3` to push the branch to your origin (private) repo. The `-u` flag sets the upstream branch for your local branch, so that you can use `git pull` and `git push` without specifying the branch name.

7. Run the following commands in the terminal to test your setup:

```bash
pytest
```

This should show a failing test

```
pre-commit run --all-files

```

This should run our _pre-commit hooks_ which will help provide you with code feedback before you commit your code. If you need to, get your code to pass the checks before continuing.

8. Add pandas to your project's dependencies.

```bash
poetry add pandas
```

Run `pytest` again to see if your test output is any different from before.

Use git commands to stage (`git add`) and commit (`git commit`) your changes. Use `git status` to see what files have been changed and what files are staged for commit, use `git log` to see the commit history, and use `git diff` to see the changes you've made since your last commit.


9. Complete the example assigment by implementing a function that returns a blank dataframe. If you're not sure how to proceed, try deducing next steps from your test output. Add, commit, and push your changes to your private repo.

10. Check your repo on GitHub. Go to the "Actions" tag and make sure the checks are passing. If they are, you are done with the exercise!
