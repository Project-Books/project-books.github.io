# Code reviews

This document outlines the process of code reviews. This serves as a guideline for reviewers, as we want to create a standardized way of reviewing code.
However, this could also be useful for contributors that want to understand the process. We want to be as transparent as possible.

## Process

1. Look at the pull request (PR) description to ensure that the PR assignee correctly filled out the 
template. For an example of an acceptable PR description, you can refer to any of the latest merged 
in PRs. The PR checklist is also there to help you.
2. Run the code. Even if the change looks small and isolated, still run it! There may be unintended side effects. 
3. Open the code in an IDE. Look at the diff to see what was changed and look for those parts 
of code in an IDE.  Doing so can help find areas of improvement that were hard to notice within 
GitHub's diff window (e.g. unused variables)

## Things to look for as a reviewer

- Style guide violations
  - Please ensure you are familiar with the relevant style guide(s).
- Areas to improve readability (e.g. does the name of the method accurately describe what it does? 
Can a comment be replaced with extracting a block of code into a method? Etc.)
- Areas to improve efficiency
- Code duplication (e.g. has the contributor redefined a utility method?)
- Grammatical mistakes
- If you see a test fail that works when you re-run it, it would be best not to ignore it. 
Look into why that may have failed.

This list is non-exhaustive and is only indicative of common problems that arise.

## Etiquette

In line with our [code of conduct](https://project-books.github.io/conduct/code-of-conduct/), always be welcoming.

Tips:
- Acknowledge the PR and tell them when you're able to review it (or that you'll review it shortly if you don't yet know when you'll be able to review it)
- Always thank the contributor when they first create the PR
- Politely offer constructive criticism. 
- Point out at least some of the good things as well if you're offering lots of feedback on areas to improve
- Always thank the contributor again when merging the PR (if you have permission)

Things to avoid:
- Being condescending (e.g. don't use ellipsis). We try hard to be supportive of people with all abilities, from beginner to pro.
- Reacting if you think someone has violated the code of conduct. It is best to speak to the maintainer to discuss the matter rather than taking it into your
own hands while you're angry, upset or in another emotional state.

As a code reviewer, you'll be representing the Book Project, so you must conduct yourself 
to the highest standard of our expectations.

## Timelines

This section only applies if you are the primary reviewer (e.g. you were asked to review some code).

### When to review a PR by

If possible, try to review the PR within seven days of when the assignee created it. 
This guidance also applies to updates. If a contributor updates a pull request, try to get back to 
them within seven days.

We recommend reviewing the PR as soon as possible for high-priority bug fixes since we must
merge in patches promptly.

If you are do not have a sufficient amount of time to review a PR, please inform the project 
maintainer (e.g. over Slack) so that they or someone else can review it.

### Providing updates

As a lot of us are busy people (jobs, family, etc.), it's understandable if seven days isn't always 
possible. In this case, we ask that you still contact the contributor within seven days with an 
update on when you will able to review it (or that you'll look into it shortly if you don't yet know 
when). 

Regular updates to keep the contributor informed that you're looking into the PR is essential.
