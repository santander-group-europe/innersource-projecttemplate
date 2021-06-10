# Code Review Process

This is an essential part of the InnerSource journey, not only to ensure code quality, but also to create and enrich a large and detailed documentation base around each and every change we ever made. The first important concept is review comments are not only for the reviewer or reviewee, but for all future contributors interested in knowing more about that particular change and why it was integrated the way it was.

The code review process involves the following actors and pieces:

  * **Documentation**  
    * A document is needed to provide the necessary steps and guidelines to allow contributors to send a proper pull request. It is usually named CONTRIBUTING.
  * **Author**  
    * The contributor sending the pull request.
  * **Committer**:
    * The person or bot who makes the commit into the "main" branch.
  * **Reviewer**  
    * One Trusted Committer having the final decision and merge ability.  
    * Optionally, a second reviewer could be required to accept the changes.  This second reviewer could be another Trusted Committer or a regular author (ideally someone who is a candidate to be a Trusted Committer in the near future). The latter will not be allowed to commit (so they cannot do merge commits either), so in this case the merge has to be done by the Trusted Committer.
  * **Local fork of the target project**
    * Contributors have only read access to upstream repositories unless they are Trusted Committers and act as reviewers in the process. If they act as commit authors, they will just use their read permission over the upstream repository. In other words, all contributions must be treated equally and go over a proper code review process.
    * The local fork allows to create local branches and modify things without affecting the upstream repository contents nor structure.
  * **Upstream repository**
    * The project repository, against which all the contributors' forks must be aligned before starting a contribution.
    * **All builds must be done from this copy** (any of their branches or tags).
    * Only **Trusted Committers** have write access, and they use it only for merging Pull Requests.
    * Nobody commits code directly here.

The workflow is as follows:

  * Starts when a contributor sends a pull request (previous steps like discussing a change proposal or deciding the design of the solution are not part of the review process itself, they are covered in the [Inner Source Contribution section](/CONTRIBUTING.md#innersource-contribution) within the [Contribution Guidelines document](/CONTRIBUTING.md)).
  * Before the Trusted Committer starts reviewing the changes, some steps should happen:
    * Running tests automatically. These include commit message checks, syntax checks, and unit tests.
      * The goal here is to ensure the change follows the contribution guidelines and guarantee certain code coverage.
    * If any of the above fails, the contributor should fix the errors and update the pull request.
  * The Trusted Committer reviews the changes.
    * In case the Trusted Committer requests changes, the contributor should update the pull request accordingly and the previous step would trigger again.  
      * The Trusted Committer acts as mentor here, helping and guiding the contributor to modify the contribution in order to get it accepted. This should be seen as a learning/teaching process and, at the same time, as a documentation process that could help to future contributors to learn about how the things are done.  
      * It is very important to keep clean, concise, and meaningful discussions in the pull requests threads. This falls under the responsibility of the Trusted Committer.
    * In case of acceptance, the Trusted Committer will merge the changes into the corresponding upstream branch (contributor may be required to rebase the code to get a clean merge).  
      * In some cases, **when upstream branches receive a large number of contributions in short periods of time, rebasing could be an endless process**. In those cases, other changes could have been merged into upstream branch in the middle of the review process. To solve this, automated testing is also done right before the merge takes place to ensure no other breaking changes have been introduced in the meantime (e.g., [see OpenStack Gerrit workflow](http://bvajjala.github.io/projects/ci/openstack-git-gerrit-and-jenkins-workflow.html)). Nevertheless, **if the characteristics of the project allow us to perform clean merges, this should not be a problem** because the changes will be always tested and reviewed on the latest version of the codebase.  
  * Once the code is merged, the code review process ends.

![Code Review Process Diagram](/assets/img/diagrams/CodeReview.png)

Merging the code is an easy task that should follow a simple rule: keep the tree as clean as possible. Anyone reading the git log should be able to understand who did what and where, and locate the exact point in the history to roll back if needed. Mixing several branches at the same time ends with a mess that is difficult to analyze and understand.

![Dirty git log tree](/assets/img/screenshots/dirty-tree.png)

This tree makes difficult to understand what changes came into the main branch with each merge. It is also difficult to know which commits belong to a given version/release (look for messages starting by `[release]`).

![Plain git log tree](/assets/img/screenshots/plain-tree.png)

This approach—using the GitHub rebase and merge button—is more readable, releases are easier to identify, but still misses which changes corresponds to a given merge, making difficult to identify possible rollback, tag, or branch points.

![Clean merge](/assets/img/screenshots/clean-merge.png)

This is the preferred case because each merge and release are clearly delimited, and it is easy to identify the commits they both consist of.
