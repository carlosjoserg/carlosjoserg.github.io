---
layout: default
---

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

## An unordered set of ideas

### Semantic branching

There are several ways to manage versions in software. Or for that purpose, anything versionable.

In one hand, there is the semantic part (AKA release system), which refers to compatibility, dependencies, API changes, and so. Probably the best example for that is the [Semantic Versioning](https://semver.org/) system. However other, even rather crazy, exist, such as the [TeX release system](http://www.texfaq.org/FAQ-TeXfuture) using the decimals of the number $$\pi$$.

On the other hand, there is the diff part (AKA version control system), which refers to the changes while developing the software. Probably the best example is simply [`git`](https://git-scm.com/). However, and naturally (`git` was not always there), other exist, such as the popular [`svn`](https://subversion.apache.org/). Though in both cases, the concept of _branching_ exist.

Now, some strategies have been proposed for branching, and most rely on the _tag_ capabilities of the version control system to do the semantic part. So my wonder is, why do we need tags, which are inherently prone to human errors? So I've come with this idea to merge the two parts above using the following branching strategy:

![semantic_branching](https://docs.google.com/drawings/d/e/2PACX-1vSfQsK6vIYNlZCu3XWa2fipg9REb_Wtwlo6uNBvCyzH_1vho9ZgxpxL2KcQYKJ5OOCLCinvBrdPorBu/pub?w=960&h=720)

Basically, the widely known and now controversial `master` branch is split into three branches named `major`, `minor` and `patch`. That is, if a set of commits enters the `major` branch, that's to be the latest, and introduces API changes for instance. Same concept applies for the `minor` and `path` branch. Additionally, I'd add the `test` branch which is equivalent to what usually is named `devel` or `unstable`, and it's purpose is to fulfil any integration test required, specially if the repo is super repo of submodules. The sync arrows are free to choose on your preffered sync way using `merge` or `rebase`. I personally prefer `rebase` to sync branches, and `merge` for adding new work on top (features, fix, etc).

Regarding the branches that add work, I'm starting to like the namespacing of what's is about, and usually are triggered by an issue for tracking purposes, and an inmediate merge request. My most commong branch names are:

* `/feature`: add new functionality
* `/fix`: solves a non-critical bug
* `/hotfix`: solves a critical bug
* `/enhancement`: improves an existing functionality
* `/doc`: when it only changes documentation, comments, typos
* `/test`: Something unstable or to be tested validated
* `/temp`: the backup branch :)

Additionally, in a multiuser repository, I'm also starting to prepend the person name specifically working on that branch, or at least, leading that work. So, a branch adding a super speed travel to a repo would like `carlos/feature/89-add_super_speed_travel`, where `89` is the issue number if required for tracking purposes.

For completeness of this writing, I had to search for `semantic branching`, and for instance, I found [this](https://dev-cafe.github.io/branching-model/), which is not at all what I wanted to state here. Another searcy entry is [this one](https://medium.com/dipien/git-branching-for-google-play-apps-230b46edccc6) which start to be more similar, but not exactly what I meant above.

So this is it, my semantic branching model.


{% include sharing.html %}
