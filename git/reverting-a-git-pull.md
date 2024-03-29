---
title: Reverting a Git Pull
date: "Mon Sep 20 16:00:00 -0400 2021"
tags: [git, howto]
---

If you ran a `git pull` and need to revert, you can use `git reflog` to find
the last revision you were on before you pulled:

```
~/work/some-project (master) % git reflog
f7da659 HEAD@{0}: pull: Fast-forward
...
~/work/some-project (master) % git reflog
87582cf HEAD@{0}: pull: Fast-forward
f7da659 HEAD@{1}: pull: Fast-forward
...
```

`HEAD@{0}` is the commit you just pulled, and `HEAD@{1}` is the commit that
was checked out before the pull. To revert to it:

```
git checkout HEAD@{1}
```

See `man git-reflog` for more info.
