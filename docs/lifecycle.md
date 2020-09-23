# Development Lifecycle Requirements

The following requirements govern the development lifecycle:

-   Direct commits or self-commits to the master branch are not allowed. All
    contributions to master **MUST** come in the form of a Pull Request.
-   Pull Requests **MUST** include not only code changes but also test changes
    and documentation changes.
-   Pull Requests **MUST** be public and open during a reasonable period of time
    so that the community can check them and contribute if necessary.
-   Pull Requests need to be approved (using the standard GitHub function or a
    'LGTM' comment) by all the reviewers involved, i.e. all people that gave
    their feedback on it. Nonetheless, if a PR has been approved by at least one
    reviewer, and after a reasonable time for feedback no further comments have
    been received, the approved Pull Request should be landed as-is.
-   Pull Request approval **MUST** be issued by a third party. Nobody can
    auto-merge their contributions.
-   Before merging an open Pull Request Travis status **MUST** be green.

## Development Lifecycle

Apart from the minimal, mandatory lifecycle described above the following
guidelines also apply.

The development lifecycle of a GE **SHOULD** be as follows:

1. When developing a new feature / bug try to **divide the work** into smaller
   parts. For instance, dividing by frontend and backend implementation. There
   can be other criteria that might depend on each feature / bug. The aim of
   this division is to simplify the review process. Big commits are usually hard
   to review, hard to change later and prone to conflicts.

2. Once you have divided the work in parts, the implementation of each part
   **SHOULD** be done in a **different branch** that you will use later to _Pull
   Request_ to the GE Repository. One recommended practice is that you _fork_
   the original repository to your GH account and develop the feature in your
   own branch (which will belong to your own repository). Later, you will make a
   Pull Request from that branch to the GE repository. See
   [branching model](http://nvie.com/posts/a-successful-git-branching-model).

3. The Pull Request **SHOULD** include not only the feature's source code but
   **unit or integration tests** together with relevant documentation.

4. At the time of landing (merging), a Pull Request **SHOULD** include **only
   one commit**. While developing you **MAY** have more than one commit but
   ultimately _only one commit **SHOULD** remain_. For doing so, use the
   [git squash](https://blog.github.com/2016-04-01-squash-your-commits/)
   functionality.

Nonetheless, there can be situations for which a Pull Request might be better
explained with more than one commit. In that particular case you **SHOULD** also
try to squash your commits into functionally coherent blocks. Nonetheless, every
commit message **MUST** be descriptive of what feature or bug the code is
implementing, for instance:

```
ISSUE 345. POST Operation /entities. Part I Parsing Requests.
ISSUE 345. POST Operation /entities. Part II DB Persistence.
ISSUE 345. POST Operation /entities. Part III Rendering Responses.
```

5. Once a Pull Request is done, a **code review** will be performed. Find a
   competent reviewer that can perform a code review. There can be more than one
   reviewer but one of them **SHOULD** be a main developer or technical
   owner/architect of the project. Typically the reviewer will test the feature,
   review the code (style, robustness, structure, performance) and suggest some
   changes. The code review **MUST** be made using the code review facilities
   provided by GitHub.

6. Try to address all the comments suggested by reviewers. If a comment is not
   going to be addressed a rationale **SHOULD** be provided.

7. Wait for a final **positive review**. This **MAY** imply _one or more
   iterations_ over steps 5 and 6.

8. Land (merge) the new code. But before landing **ensure that all tests are
   passing**. Under certain conditions your Pull Request could not be directly
   landed (merged). In that case you would need to rebase your branch with the
   master branch, resolve all conflicts, push them and finally merge the new
   code in the master branch. Nobody can auto-merge their contributions.

9. If later you discover that new code is breaking something _do not hesitate to
   back out the culprit code_. That's the advantage of landing only one commit.
   Backing out code is as easy as `git revert <commit_hash>` .
