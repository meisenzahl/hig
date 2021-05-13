# Prepare Code for Review

## Program for the present, not the future

At elementary we believe in the YAGNI principle (You aren't gonna need it): Always implement when you _actually have_ a need - but never when you _think_ you are _gonna_ need it. Combined with continous refactoring, the YAGNI principle keeps the code base as simple as possible while helping us to avoid technical debt.

## Avoid big changes in one go

As someone proposing a code change, probably the most helpful thing is to keep it small. A small Pull Request feels less intimidating for a code reviewer, so there is a higher chance to get timely feedback for such a request. In addition, a small change is a lot less to test and there is a much smaller chance of a regression - both things lead to a higher overall quality and therefore to a better experience for the end user.

If you're proposing large functional changes, it's usually better to do so in several smaller Pull Request and linking them to a corresponding issue report which explains the overarching goal.

## Keep it self contained

It's really tempting to do a lot of refactoring as you see it, but this makes it really hard for a reviewer to understand the important parts for the functional changes.

## Keep it consistent

Naming is one of those things that feels trivial but really helps in a few years when it's all new eyes on some code. Especially if we can use names that sound like the ones already present in the libraries used it can make it much easier to figure out what's happening.

## Comment non-trivial code

If you are writing some non-trivial code, make sure to add a comment which explains exactly _what_ and more importantly _why_ your code does what it does.

## Don't mix refactor with functionality commits

If you need to move and refactor a certain piece of code, its much easier to review if both steps are broken down into individual commits:

**Commit #1: Moved logic into do_foo**

```diff
+ void do_foo () {
+ [Code from the other_function]
+}
void other_function () {
- [Code from the other_function]
+ do_foo ();
}
```

**Commit #2: Refactoring do_foo**

```diff
void do_foo () {
+ Changes
+ in foo logic
}
```

Don't worry, we understand this is sometimes a difficult advice to follow thoroughly. But we strongly encourage to keep an eye on your commit history: Whenever the nature of the changes in your commits seem to be rather unrelated, its probably worth the effort to [clean up the Git history with interactive rebasing](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History). This extra step makes it much easier for another person to review your changes and minimizes the risk of regressions for all of us.

## Describe your change

Make sure you describe the changes you are proposing in the Pull Request description. If appropriate, add a screenshot or a short video to show case your change. This cuts down a lot on the time a reviewer needs to invest to understand your code.

## Review your code yourself first

When you got your initial version for the poposed change working, look into the code you've added once again and ask yourself if anything could be done in a better fashion before sending it to official Code Review. Of course, if you want some early opinion, there is always the possibility to open a Draft Pull Request as well.