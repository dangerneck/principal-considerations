# Code

## Version control

[Git](https://git-scm.com/) Pretty much the right choice.

## Clear branching and commit strategy

[Cactus](https://barro.github.io/2016/02/a-succesful-git-branching-model-considered-harmful/) for small teams and those confident with git.

[Git Flow-like](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) for pushing complexity and responsibility more onto the maintainers and seniors than each developer with more pull-request opportunities and a more process-heavy approach

## Sane defaults

What I mean by this is onboarding easy and frictionless and safe. **Ensure someone on their first day can use all the technology in your stack on default settings and nothing bad will happen**. `master` branch doesn't have production credentials, for example. Running tests won't touch real data. Make it very easy to explore and learn, make it _literally impossible_ to break anything without the help of existing developers.

This logically leads to the very important idea that **if something has complex and impactful effects or side-effects make those clear** and **add friction to processes directly proportional to the scale of their negative effects**. A button to copy your public key to the clipboard should be normal, fine. A button to copy your private key to your clipboard probably shouldn't exist, or be very difficult!

## Hygeine for code and version control

This means going back constantly over code and over branches to keep them simple and within the process you've decided on. Or, if the process changes this means taking the time to adjust things as you go. The longer you put this off the bigger the refactor later, or the more exceptions you have to explain and document, or the more tempted you are to not do things consistently. 

You are the most brilliant human who was ever born and the world sparkles under your incandescent glory. Your brain however is a wet mass of idiot that wants you do nothing but flop around in constant uninterrupted hedonistic frictionlessness. So: try to find a balance! 

## Semantic Versioning

[Semantic Versioning](https://semver.org/) to allow your project to become an easily manageable dependecy for something else. Treat your private in-house dependencies with the same care. Don't be afraid of private repositories.