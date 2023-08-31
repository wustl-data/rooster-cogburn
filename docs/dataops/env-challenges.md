# Dev Environment Challenges

With all of that history and philosophy behind us, let's get into the practical. In this section, we'll go over the tools and techniques that are implemented in our assignment workflow in an attempt to bring DataOps to the classroom. A strong understanding of this workflow will help immensely during this course.

## Common Roadblocks

_Development environments_ are the set of tools and configurations that a developer uses to write and test code. Traditionally, these environments are often expected to be installed by the individual developer on their local machine. The manual installation of development dependencies gives rise to a variety of problems at various levels of software:

### OS-level concerns

- Package/Application installation and management
    - Windows: winget, OSX: brew, Ubuntu: apt
- Environment variables
    - PATH, Containers, text files
- File permissions
    - sudo, chmod, chown, "Run as Administrator"
- Shell configuration
    - bash/.bashrc, zsh/.zshrc

### Language-level concerns

- Language installation and version management
- Package management
    - Virtual environments
    - Dependency declaration & resolution
- Builds
- Testing
- Debugging

!!! note "Conda and Jupyter"

    Conda is a cross-language/cross-platform package manager, and will only be strictly necessary in this course if you would like to use it for a third-party package that requires it or only provides documentation for conda setups. If this is the case for you or if you just prefer conda, you will likely want to look into adjusting your dev container and using mamba for compatibility/performance reasons.

    Most of you are likely coming from Jupyter-centric development environments. While notebooks are great for experimentation and managing intermediate state, they are not great for reproducibility and collaboration. We will be using Jupyter in this course, but only as a tool for experimentation, exploration, and demonstration. All of your submitted code **must** be written in `.py` files, and all of your code should be runnable from the command line. This will make your code more stable, portable and easier to test and debug. If you really love developing in the Jupyter interface, you might want to look into tools like [nbdev](https://nbdev.fast.ai/) which provide better infrastructural support for Jupyter-centric development.

### Data concerns

- Storage and retrieval
- Installation, authentication, and configuration
- Seed data, test data, production data
- Database migrations

### Deployment concerns

- Containerization
- Config as Code
- Continuous delivery

### Application-level concerns

- Running services
- Interacting with the program
- Logging
- Feedback tools
- Documentation
- Authentication

### Collaboration concerns

- Version control
- Code review
- Issue tracking, feature requests, bug reports
- Continuous integration
- Barrier to entry
