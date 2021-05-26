# Contribution Guidelines

This document describes how to send a contribution to the project.

* [Definitions](#definitions): **please this section first**.
* [InnerSource Contribution](#innersource-contribution): describes the process of proposing a new feature or fix to the project.
* [Sending a contribution](#sending-a-contribution): describes how to send a contribution to the project once it was accepted to be scheduled.
* [Branch Policy](#branch-policy): describes the project's branching strategy.
* [Additional Documentation](#additional-documentation): some extra stuff that may be worth reading before start working on your contribution.

## Definitions

#### Upstream
The main Git repository of the project (this is not the same as the `main` branch). It is common to fork a project to send contributions (see [Contribution Guidelines](#contribution-guidelines) section). Those forks need to be aligned with the upstream repository.

#### Clean merge
A merge that is performed on a branch, without any other merges in between. Next screenshot shows what IS NOT a clean merge and therefore we get a dirty Git graph. It's difficult to see the scope of each change and rolling back can be nightmare:

![Clean and clear merge seen from `git log --graph --oneline`](/assets/img/screenshots/unclean-merge-log.png)

## InnerSource Contribution

The process of sending a contribution to an InnerSource project must follow the [guidelines described by the InnerSource Commons community](https://github.com/InnerSourceCommons/InnerSourceLearningPath/blob/master/introduction/03-how-works.asciidoc) (please visit the original document to check the current list of people that wrote the document). This section is based on those guidelines, with some modifications.

The process starts when a new feature that is important for an external team or contributor (from now on we simplify it to guest team) is requested to the team in charge of the project (host team) where that feature has to be implemented. The host team is interested in having that feature included in the project. However, the host team is unable to implement that feature in time. At this point, the guest team could decide to implement the feature by themselves and send a pull request to the host team, so the work is ready on time and the host team receive a new feature they did not have time to implement.

There are some issues that should be taken into account and addressed in this document:

* **The guest team should follow the rules of the host team** to make the contribution. That means **those rules must be written and available to them**.

* **Sending the pull requests for review with any prior communication could end with the host team not accepting the pull request due to unforeseen design or implementation problems**. For small features that are not critical to the host team there should be no problem in receiving pull requests for review at any moment. Other more complex solutions would need a more in-depth analysis and discussion. **This process should be clearly written down and publicly available for the guest team so they can decide how to proceed**.

Having said that, the process would be as follows:

* **Guest team identifies a new feature** they need from the host team.

* **Guest team** request that feature to the **host team**.

* **Product owner** has an important role here determining what functionality the host team is interested in accepting as a contribution.

* **Host team** could decide to take the feature or not. If they accept it, they develop the feature as usual and nothing else is needed.

* In other cases, **guest team**, following the rules specified by the **host team**, decides whether to send the pull request directly or, most probably when dealing with medium-to-large sized features, they will inform the **host team** they want to implement the feature by themselves.

* **Host team** verifies the feasibility of the feature and may require some specific information to the **guest team** about how they plan to solve it. **Host team** must ensure the proposal is valid to be accepted in terms of architectural design, coding conventions, dependency usage, or any other requirement they may have. Ideally most of those requirements will be written down within the documentation provided by the **host team**. If new ones are identified, documentation should be updated accordingly as soon as possible.

* **Product owner** ensures the whole process is documented. User stories must be created either by the **host team** or the **guest team** to cover the new feature, including all the needed information for both teams to ensure that the output of the previous point is fully covered.

* **Trusted Committer** will help and guide the **guest team** during the process. **Having the pull request accepted and merged is a common benefit for both parts**, and so it should be understood.

![InnerSource contribution process](/assets/img/diagrams/InnerSourceContribution.png)

The benefits of this approach are:

* Shared resources.
* Shared knowledge.
* Scalability.
* As far as the process is common to different projects, eases mobility across teams.
* Reduces the time of feature negotiation and escalation processes.

## Sending a contribution

In this project there are two main types of contributions:
* **[Issues](https://github.com/SantanderInnerSource/innersource-project-template/issues)**: any idea, comment or proposal is more than welcome to be discussed. Please open an [issue](https://github.com/SantanderInnerSource/innersource-project-template/issues)!
* **[Pull Requests](https://github.com/SantanderInnerSource/innersource-project-template/pulls)**: any change can be proposed via Pull Request. Please continue reading this document to find more details on this. In case you are unsure about the change, want to propose an important modification either in terms of size or relevance, or if you simply need some help, please open an issue and we will be more than happy to discuss about it.

As this project contains documentation only, changes can be made through the GitHub web interface. For completeness we include here the manual process that is usually followed for code contributions. It applies also to documentation, however the GitHub interface is usually easier for newcomers and people not used to work with Git repositories.

General GitHub workflow rules for contributing via fork apply to our project.

* Fork the project. See [GitHub documentation on forking a repo](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo)). Make sure you configure the upstream repo as a remote so you will be able to fetch newer changes from upstream later on, if needed.
* Create a local branch (`git checkout -b <branch_name>`).
* Make your changes. Please, follow the [Additional Documentation](#additional-documentation). **If you plan to add new files to the documentation** folder, please follow the [template document](doc/_template.md) included in the `doc` folder.
* Push your local branch to your fork (not to upstream, in the worst case you won't have push permission upstream and will get an error, unless you are a trusted committer, in which case please double check your command line).
* Go to GitHub, create the Pull Request. See [GitHub documentation on how to create a Pull Request from a fork](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork).
  * The contributor is responsible of providing commits that allow [clean merges](#clean-merge). In case this not happens, they were requested by the reviewers to rebase their branch and push again the changes.
* Reviewer is responsible of merging changes, even if the contributor has permissions to do it. Merges should look like the following one (obtained via `git log --graph --oneline` command):
![Clean and clear merge seen from `git log --graph --oneline`](/assets/img/screenshots/merge-log.png)
* From the image, is clear:
  * Where the merge was performed.
  * Who merged the changes (not in the image because `--oneline` option was used to summarize the resulting graph).
  * The commits being merged.
  * Who sent those commits (not in the image because `--oneline` option was used to summarize the resulting graph).
  * Ideally only one feature is covered by all of them, no matter if it's split into several commits for clarity, because the tree is clear enough thanks to its shape.

  ## Branch Policy

  This project contains documentation, here we describe a common approach for branching that applies well not only to this case, but also to code oriented repositories.

  The main ideas behind the branching strategy explained here are:
  * Keep things as simple as possible.
  * The contributors are fully responsible of their changes.
  * Users are expected to use the latest version released.

  By following these ideas, the project `main` branch is the place to go to get the latest changes. Some of them could be still under testing processes. This means `main` is as stable as the testing performed on each Pull Request before merging it into master. It is granted that those changes are part of the roadmap (in other words, may not be fully tested but they are not experimental).

  ---
  **From now on, the rest of the section does not apply to this project, but could be useful for code repositories**. This is just an example to show different points that should be covered, of course the specific approach each project may want to take for each of them can be different depending on their needs.   

  ---

  For more stable versions, we use tags and releases. Each release is associated to a tag in the repository, so it's easy to get the snapshot of each release if needed.

  In case of a bug, it will be fixed on the current `main` branch and not backported. Users are expected to be always in the latest release, supporting several versions at a time is out of the current possibilities of the project in terms of effort.

  **Corner case**: if a bug broke an older version and there were not any possibility of updating from that version to a newer one for a representative number of users, a branch would be created from that point, the fix would be applied on that branch and then merged into the `main` branch. The branch created for the fix is expected to be deleted as soon as users of that branch are able to update to the latest release.

  **Experimental development**: sometimes it is needed to break everything to explore new options for future releases (always under the roadmap of the project) while some developments for the next one are still being tested and pending to be merged. In those cases, a new branch will be created until `main` branch gets to a specific release point. At that point the new branch will be reintegrated into `main`.

  This means that most of the time there will be just one or two branches upstream, the rest will be part of the contributors' forks.


## Additional Documentation
In addition to all of the above mentioned, we encourage you to read the following guides before start contributing:

* [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/). Commit messages matter. Here's how to write them well. Written by Chris Beams.
* [Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell). From [Pro Git book](https://git-scm.com/book/en/v2), written by Scott Chacon and Ben Straub and published by Apress. All content is licensed under the Creative Commons Attribution Non Commercial Share Alike 3.0 license.
* [Git happens! 6 Common Git mistakes and how to fix them](https://about.gitlab.com/blog/2018/08/08/git-happens/). Written by Sam Beckham.
* [GitHub guide on mastering markdown](https://guides.github.com/features/mastering-markdown/).
* [GitHub docs contribution guide](https://github.com/github/docs/blob/main/CONTRIBUTING.md).
