# Document

## Code should be written clearly so that it can self document

Don't necessarily go as far as Literate Programming but the computer doesn't give a damn what variables are called as long as they follow the rules, and compilers/minifiers/transpilers/whatever will garbage them up anyway. So, name things and structure code as much as you can so that you can see what it's doing as a human! Clear > clever! Optimize later!

## Comments should be employed when code is necessarily unclear

After necessary optimizations or with things that are necessarily gross, just throw comments in.

Also it's a great opportunity to point out **implicit domain knowledge** in the code that may look like a code smell or some junior bullshit.


## Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.

For 1-3 people Trello is good.

For medium to larger teams Jira is great, but pretty much how you use the project management solution is far more important than what it is doing.

## README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)

This is not just to indicate that you have used 'create-react-app' to generate the site, it also can be used to introduce any developer to the project.

## How-to's and onboarding information should be easily accessible and outlined.

Your brain is not a manageable dependency. Put your project specific knowledge into some kind of managed storage! 

## A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives

It absolutely doesn't matter how you do it, just do it in one place and do it always.

Here's a simple one:
Decision | Decider | Notes 
---| --- | ---
i like this | me (smart&strong dev) | i like it and im better than darryl so darryl can go huff a butt
butts are gross dont huff them | me | yuck darryl get your face out of all those butts sheesh you huff maniac
Hillary Huff is a funny nickname for darryl | me | haha darryl you dingus

Or a little more detailed & professional

Decision | Decider | Sign off | Alternatives | Notes
--- | --- | --- | --- | ---
documentation is important | CEO | product owner | failing miserably | failure is considered bad i learned that in my MBA
documentation is hard | tech lead | N/A | not writing docs trust me i remember everything just email me lol | why bother code is perfect just read my perfect beautiful code and do you want to hear my opinions on political correctness 
install a door between devs & the rest | everyone | everyone | dealing with a bunch of manchildren | how the hell did this happen they're in their thirties

## A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.

Not only is it important to track what terrible things you're accepting temporarily, this is a great way to cover your ass and look smarter than the horrible code you write! And it can feed into sexy buzzwords like *RISK* and *BIT ROT* and *WE ARE MONSTERS* and help you justify to non-technical folks why the third refactor in 6 months is absolutely more important than changing the colour of the sweet car animation that comes up when you enter the site.

## Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.

```
git commit -m "PROJECT-045 bad button fix #time=1h30m #type=Spicy #etc #darrylsucks"
```

## Relevant information and non-functional artifacts should be managed and accessible eg Confluence

**Never fall into the trap of believing you can remember things accurately, or even at an opportune time.**


    1. **Code should be written clearly so that it can self document**
        - Don't necessarily go as far as Literate Programming but the computer doesn't give a damn what variables are called as long as they follow the rules, and compilers/minifiers/transpilers/whatever will garbage them up anyway. So, name things and structure code as much as you can so that you can see what it's doing as a human! Clear > clever! Optimize later!
    2. **Comments should be employed when code is necessarily unclear**
        - After necessary optimizations or with things that are necessarily gross, just throw comments in.
        - Also it's a great opportunity to point out **implicit domain knowledge** in the code that may look like a code smell or some junior bullshit.
    3. **Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.**
        - 1-3 people Trello is good
        - medium to larger teams Jira is great, but pretty much how you use the project management solution is far more important than what it is doing.
    4. **README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)**
        - this is not just to indicate that you have used 'create-react-app' to generate the site, it also can be used to introduce any developer to the project.
    5. **How-to's and onboarding information should be easily accessible and outlined.**
        - Something you've done that another person might say 'hey donghole over there did that before, ask them about it' -- write it down so you can put it on Confluence or whatever else. 
    6. **A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives**
        - it absolutely doesn't matter how you do it, just do it in one place and do it always.
    7. **A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.**
        - if you don't do this then the future developers will come in and whisper behind your back how you don't even understand variable scoping or that for loops are out of fashion and you can't point to a document that turns the dingus indicator back on to them! (Dingicator?)
    8. **Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.**
    9. **Relevant information and non-functional artifacts should be managed and accessible eg Confluence**
    - **Never fall into the trap of believing you can remember things accurately, or even at an opportune time.**
