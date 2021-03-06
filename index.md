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

Now, some strategies have been proposed for branching, and most rely on the _tag_ capabilities of the version control system to do the semantic part. My philosophical question is: **why do we need tags, which are inherently prone to human errors?**. I've come with this idea to try tackle semantic versioning by syncing branches, that is, to fusion the two parts above by using the following branching strategy:

![semantic_branching](https://docs.google.com/drawings/d/e/2PACX-1vSfQsK6vIYNlZCu3XWa2fipg9REb_Wtwlo6uNBvCyzH_1vho9ZgxpxL2KcQYKJ5OOCLCinvBrdPorBu/pub?w=1440&h=1080)

Basically, the widely known (and now controversial) `master` branch is split into three branches named `major`, `minor` and `patch`. That is, if a set of commits enters the `major` branch, that's to be the latest, and it folows the semantic versioning: it introduces API changes for instance. Same concept applies for the `minor` and `path` branches. Additionally, I add an optional `test` branch which is equivalent to what usually is named `devel` or `unstable`, and its purpose is to organize any integration test required, specially if the repo is a super repo of submodules. The sync arrows are to be chosen freely, using `merge` or `rebase`. I personally prefer `rebase` to sync branches, and `merge` for adding new work on top (features, fix, etc), in general. But, using `merge` to sync and configure to use a merge commit has the advantage that the merge commit represent the point in time where the version changed, so I might consider using `merge` to sync instead ;). And recall that commits can be _squeezed_ before going into a `patch` release, from where a set is to become a `minor` release, and from where a set is to become a `major` release.

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

And that's it, my idea of a semantic branching strategy.

{% include sharing.html %}

### The '92 Dream Team is not the best ever assembled

![dream_team](https://www.usab.com/~/media/7ca08f0318194f0ba592a906aa251295.ashx?bc=e3e3e3&h=300&w=400)

Not that I respect the team, to me, it could have been even better with these changes:

1. Dominique Wilkins, instead of Clyde Drexler. With all due respect, but Clyde is not match in this team, specially with someone like Dominique in the court. My guess is that Dominique is not "American", though he was included in the team later on. Other than that, there is no rational explanation for this choice. I don't even care about Isiah Thomas not being there, me being a Detroit Pistons fan at that time.

2. Shaquille O'Neal instead of Christian Laettner. Well, this why you shouldn't never base your decision purely on numbers. Believe or not, Shaq was in that season as a NCAA player, and later became the dominant player he was. Can you imagine him in the first dream team? No one would have notice that he was actually the NCAA guy, probably that's why they didn't choose him, besides the numbers.

3. Hakeem Olajuwon, instead of either Patrick Ewing or David Robinson. It really don't care who is to be substituted, but Hakeem, IMHO, is in the Top 5 all-time player (not center, player... yes, over Kobe, Lebron and whowever you want to put on Top 3, you still need to overcome Hakeem), and none of the other two are. Period. Probably the one center MJ ever respected, never saw a dunk on him by MJ, like on other centers of that era. [His story](https://www.youtube.com/watch?v=l7gbybeKafQ) is even more incredible, considering this was the 80s. Similar to Dominique, I think he was not in the first team due to "American" reasons.

So that's it, my best team never assembled is the one in the picture below:

![better](https://docs.google.com/drawings/d/e/2PACX-1vT6vNH03VBP_j5fr435fPvgPM8VtcMAo3tRe3fLARdgiVe06yyrMnQOcgixxwSg3PlUCqzn0k8KfC0F/pub?w=1440&h=1080)

{% include sharing.html %}
