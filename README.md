# Principal Considerations
or
## How to try to develop web applications without getting in your own way or ruining it for yourself and others or being a dingus.

The following is a set of *important things* to consider in the development of a web application. Some are written as rules to follow and some are written as general and open suggestions on how to avoid these *important things* from becoming a problem or -- especially -- surprising you then derailing you, your team or project entirely. 

It is not essential to have strategy for every single thing below, but it is always a good idea to at least consider how it may effect your application in its lifetime and communicate somehow an awareness of them in documentation for the future developers that inherit your application. And as with any rule or principle put forth once they are learned or known they can be broken or ignored. Put another way: learn the rules so you know how to break them most effectively.

The [12 Factor App](https://12factor.net/) was a starting point for this, so we owe a great deal to that, but I found that to be far too specific in some points   and entirely missing other points.

This is also an attempt at me articulating succinctly the combined experience of my career - without going into specific implementations too much. 

*I invite all suggestions and comments. Submit a pull request or contact me.* 

This is only useful as far as it guides folks in a positive direction and offers signposts for danger down the road. Personally I'm fed up with seeing the same short-sighted and (bluntly) boring problems coming up in projects I work on. So let's end the perpetual MVP -> Beta -> Crash And Burn -> Start Again cycle of many web applications and stop the slow degradation of program quality in general.

Also don't just say containerizing solves everything you dingus you're just hiding the complexity and delaying disaster till something changes and it doesn't work anymore and absolutely nobody knows how to deal with it!

### Roadmap

**This is very much a first draft.** The wording is inconsistent, the depth of thinking in each consideration varies, etc etc. 

Over time there will be a *simmering* of concepts and wording to reduce this into its most potent essence. You gotta reduce your sauce, otherwise its just weird flavoured water that you're pouring on your meal. Just eat soup if you want to do that.

## Top-tier Considerations

1. [**Code**](#Code)
2. [**Dependencies**](#Dependencies)
3. [**Required Services**](#RequiredServices)
4. [**Configuration**](#Configuration)
5. [**Build**](#Build)
6. [**Document**](#Document)
7. [**Test**](#Test)
8. [**Run**](#Run)
9. [**Environments**](#Environments)
10. [**Eventing and Logging**](#EventingandLogging)
11. [**Profiling**](#Profiling)
12. [**Administrative and Tertiary Processes**](#AdministrativeandTertiaryProcesses)
13. [**Continuous Integration / Continuous Deployment**](#ContinuousIntegration/ContinuousDeployment)
14. [**Software Life into Maturity**](#SoftwareLifeintoMaturity)
15. [**Security**](#Security)

## Second-tier Considerations

1. <a name="Code">**Code**</a>
    1. Version control
    2. Clear branching and commit strategy
    2. Sane defaults
    3. Hygeine for code and version control
    4. Semantic versioning to allow your project to become an easily manageable dependecy for something else

2. <a name="Dependencies">**Dependencies**</a>
    1. Package managers
    2. Semantic versioning allowing dependency updates and changes to be managed in a standard and predictable way
    3. Isolation and separation of concerns

3. <a name="RequiredServices">**Required Services**</a>
    1. Service drivers or providers isolated for configurability / injection
    2. Wrap and/or abstract environment/driver specific stuff so a configuration change can do it
    3. Tolerate unavailability with retries, queueing, volatile state usage.

4. <a name="Configuration">**Configuration**</a>
    1. Config should be provisioned by environment so that configuration leads to automatic flexibility and hot swapping of configurable elements.
    2. Config is never in code, because if it is it becomes code.

5. <a name="Build">**Build**</a>
    1. Transformation of code, dependencies, assets and configuration into a runnable package within an environment
    2. Easily testable (preferrably automatically tested)
    2. Indempotent, safe, logged, verbose processes.

6. <a name="Document">**Document**</a>
    1. Code should be written clearly so that it can self document
    2. Comments should be employed when code is necessarily unclear
    3. Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.
    4. README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)
    5. How-to's and onboarding information should be easily accessible and outlined.
    6. A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives
    7. A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.
    8. Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.
    9. Relevant information and non-functional artifacts should be managed and accessible eg. Confluence

7. <a name="Test">**Test**</a>
    1. Sanity checks for checking dependencies / assumed things like folder structure, specific files, dumb stuff not obviously required.
    2. Unit testing
    3. Integration testing for required Services with mockable or memoized inputs
    4. End-to-end testing - test the software with connected services as a whole.
    5. User testing - test as an agent utilizing the software.
    6. Verification testing - after events such as releases or environment changes re-run all tests and treat it like a first release.

8. <a name="Run">**Run**</a>
    1. Start, Stop, Restart, Status of application.
    2. Process managers for crash recovery
    3. Profiling and watchdog processes for real-time information on status and resource usage.

9. <a name="Environments">**Environments**</a>
    1. Configuration is provisioned by environments as necessary
    2. No code changes should be required for moving from one evironment to another
    3. All environments should be as close to equivalent as possible
    4. Environments should be entirely isolated from eachother

10. <a name="EventingandLogging">**Eventing and Logging**</a>
    1. At some time everything that the application does or has happen to it will be of interest to someone.
    2. Future business logic will want to work on arbitrary past data.
    3. Immutable data + Events + Event Handlers as Mutators = Time Travelling Logic
    4. Keep a master event log if possible. Forever.

11. <a name="Profiling">**Profiling**</a>
    1. At all times the resource usage of the application should be known as well as the history of that usage.

12. <a name="AdministrativeandTertiaryProcesses">**Administrative and Tertiary Processes**</a>
    1. Interval based reports or sporadically required tasks should be in code somehow, documented and configurable to the standard of the application.
    2. If not in code these processes should be defined and documented in a way such that any layperson can do it with the right access.
    3. Data imports and exports
    4. Arbitrary reports on anything at all.
    5. Auditing
    6. Erasing and locking down things if required

13. <a name="ContinuousIntegration/ContinuousDeployment">**Continuous Integration / Continuous Deployment**</a>
    1. Committing work to version control can be seen as a logical step forward i.e. feature completed, bug fixed, refactor completed. This can and should be used to pass the software through all other safely automatable steps.
    2. Clear branching and commit strategy allows predictable results from watching for changes in a code repository.
    3. Well defined, safe and verbose Builds allow automatic builds from changes in watched code repositories.
    4. Separated and complete Testing suites allow for maximum reasonable testing to be done after a Build.
    5. Isolated predictable environments that provision configuration inputs means that built artifacts can be moved to arbitrary environments without needing forward knowledge about their differences or effects of being present in those environments.
    6. Run strategies allow for any programmable agent to check the status, stop the application, update artifacts, and then start it again. Process managers and profiling also allow for at least a basic level of self-healing applications.
    7. Eventing and Logging allows the process of preparing and deploying the application can be part of the application's auditable and watchable master event log. This provides a logical entry point for Software Life into Maturity considerations.
    8. In conclusion: **Commit** -> **Build** -> **Test** -> **Deploy** -> **Run** -> **Log** / **Profile** / **Administer** -> **Nice**. Or any subset or superset of that flow.

14. <a name="SoftwareLifeintoMaturity*">**Software Life into Maturity** </a>
    1. Maintenance such as patches, upgrades, breaking changes to dependencies
    2. The application should communicate somehow any foreseen problems occurring
    3. There should be some strategy or policy on how to manage required resources over time - up and down.

15. <a name="Security">**Security**</a>
    1. Every line of code, every dependency, every service, every environment, every configuration, every Event, every generated log, all data, all processes, all communications, all side-channels must be maintainable, patchable, auditable and assumed to be under constant opportunistic attack
    2. Obscurity is not security
    3. The application will be exploited and broken so there must be a strategy for identifying, managing, understanding and cleaning-up after a breach.

## Examples
Here I will put what specific approaches I currently enjoy for all of the above. Or explanations if appropriate.

1. **Code**
    1. **Version control**
        - [Git](https://git-scm.com/) Pretty much the right choice.
    2. **Clear branching and commit strategy**
        - [Cactus](https://barro.github.io/2016/02/a-succesful-git-branching-model-considered-harmful/) for small teams and those confident with git
        - [Git Flow-like](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) for pushing complexity and responsibility more onto the maintainers and seniors than each developer with more pull-request opportunities and a more process-heavy approach
    3. **Sane defaults**
        - What I mean by this is onboarding easy and frictionless and safe. **Ensure someone on their first day can use all the technology in your stack on default settings and nothing bad will happen**. `master` branch doesn't have production credentials, for example. Running tests won't touch real data. Make it very easy to explore and learn, make it _literally impossible_ to break anything without the help of existing developjers.
        - This logically leads to the very important idea that **if something has complex and impactful effects or side-effects make those clear** and **add friction to processes directly proportional to the scale of their negative effects**. A button to copy your public key to the clipboard should be normal, fine. A button to copy your private key to your clipboard probably shouldn't exist, or be very difficult!
    4. **Hygeine for code and version control**
        - This means going back constantly over code and over branches to keep them simple and within the process you've decided on. Or, if the process changes this means taking the time to adjust things as you go. The longer you put this off the bigger the refactor later, or the more exceptions you have to explain and document, or the more tempted you are to not do things consistently. You are the most brilliant human who was ever born and the world sparkles under your incandescent glory. Your brain however is a wet mass of idiot that wants you do nothing but flop around in constant uninterrupted hedonistic frictionlessness. Don't let your inner idiot win.
    5. **[Semantic Versioning](https://semver.org/) to allow your project to become an easily manageable dependecy for something else**

2. **Dependencies**
    1. **Package managers**
        - whatever the standard for your language is. [yarn](https://yarnpkg.com/) or [npm](https://www.npmjs.com/) are good for js.
    2. **Patching and upgrading**
        - the package manager handles the operations of downloading, caching and tracking dependency artifacts. Combined with [Semantic Versioning](https://semver.org/) you can (to some degree) specify your update policy, and then you actually do the updating as part of your development process!
    3. **Isolation and separation of concerns**
        - using a package manager and approaching these dependencies in such a way that they are black boxes with known inputs and outputs you can go ahead and not give a damn about them except how you use them / how you deal with them. Separated!

3. **Required Services**
    1. **Service drivers or providers isolated for configurability / injection**
        - Very dependent on your specific implementations, but a required service is like a dependency that must have some operational logic and outside uncontrollable and unpredictable state. So a little more flexibility is required.
    2. **Wrap and/or abstract environment/driver specific stuff so a configuration change can do it**
        - Dependency Injection! Inversion of control! Or just don't make assumptions your code doesn't explicitly check! DI is not such a thing in JS because import/require do a pretty good job and you can bend things enough anyway.
    3. **Tolerate unavailability with retries, queueing, volatile state usage.**
        - Yeah, your API is so nice and solid and you have the sickest load balancing in place and the best caching policy anyone has ever imagined and your cloud provider guarantees 99.95% uptime which is like, pfff, pretty much all the time! And when it fails anyway it's sooooooo brief and quick and who cares! Like, even Facebook goes down sometimes!
        - Everything working as expected is an assumption that should be tested before it is required to be true
        - Retries are good
        - Queues handle spikes pretty well!

4. **Configuration**
    1. **Config should be provisioned by some external method or service so that configuration leads to automatic flexibility and hot swapping of configurable elements.**
        - [dotenv](https://github.com/motdotla/dotenv) is always a great place to start. But any kind of config provisioning is good as long as you treat it like a particularly important Required Service
    2. **Config is never in code, because if it is it becomes code.**
        - There are no exceptions

5. **Build**
    1. **Transformation of code, dependencies, assets and configuration into a runnable package within an environment**
        - npm + some kind of shell script is a good start, and often as far as you need to go
        - webpack if you're doing front-end js
    2. **Easily testable (preferrably automatically tested)**
        - npm + mocha for the code portion of testing
    2. **Indempotent, safe, logged, verbose processes.**
        - design the build and test steps so they follow the Open/Closed principle, and also make sense and don't do not-immediately-obvious things that are important!

6. **Document**
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

7. **Test**
    1. **Sanity checks for checking dependencies / assumed things like folder structure, specific files, dumb stuff not obviously required.**
    2. **Unit testing**
    3. **Integration testing for required Services with mockable or memoized inputs**
    4. **End-to-end testing - test the software with connected services as a whole.**
    5. **User testing - test as an agent utilizing the software.**
    6. **Verification testing - after events such as releases or environment changes re-run all tests and treat it like a first release.**

8. **Run**
    1. **Start, Stop, Restart, Status of application.**
    2. **Process managers for crash recovery**
    3. **Profiling and watchdog processes for real-time information on status and resource usage.**

9. **Environments**
    1. **Configuration is provisioned by environments as necessary**
    2. **No code changes should be required for moving from one evironment to another**
    3. **All environments should be as close to equivalent as possible**
    4. **Environments should be entirely isolated from eachother**

10. **Eventing and Logging**
    1. **At some time everything that the application does or has happen to it will be of interest to someone.**
    2. **Future business logic will want to work on arbitrary past data.**
    3. **Immutable data + Events + Event Handlers as Mutators = Time Travelling Logic**
    4. **Keep a master event log if possible. Forever.**

11. **Profiling**
    1. **At all times the resource usage of the application should be known as well as the history of that usage.**

12. **Administrative and Tertiary Processes**
    1. **Interval based reports or sporadically required tasks should be in code somehow, documented and configurable to the standard of the application.**
    2. **If not in code these processes should be defined and documented in a way such that any layperson can do it with the right access.**
    3. **Data imports and exports**
    4. **Arbitrary reports on anything at all.**
    5. **Auditing**
    6. **Erasing and locking down things if required**

13. **Continuous Integration / Continuous Deployment**
      - At the point you're doing this you probably have a clear choice. If not here's a roadmap:
      
      1. shell / batch scripts for build, test, run
      2. a single script that handles the build, test, run scripts making it a 1 click / 1 call process
      3. a service that watches a repository for changes then runs the above process
      4. you're done, or you get Team City or Bamboo or something running.

14. **Software Life into Maturity** 
    1. **Maintenance such as patches, upgrades, breaking changes to dependencies**
    2. **The application should communicate somehow any foreseen problems occurring**
    3. **There should be some strategy or policy on how to manage required resources over time - up and down.**

15. **Security**
    1. **Every line of code, every dependency, every service, every environment, every configuration, every Event, every generated log, all data, all processes, all communications, all side-channels must be maintainable, patchable, auditable and assumed to be under constant opportunistic attack**
        - Logging and profiling is a minimum to have any idea that you may have folks or software poking for holes.
    2. **Obscurity is not security**
        - The only reason it might appear that way is nobody has bothered to try yet. Just wait until you have something valuable going on with your software.
    3. **The application will be exploited and broken so there must be a strategy for identifying, managing, understanding and cleaning-up after a breach.**
        - For real: have a disaster plan and a going public plan when you inevitably lose track of important data or find you've been serving ads for reasonably prices Ray-Bans.
