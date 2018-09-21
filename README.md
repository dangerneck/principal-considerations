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

Over time there will be a *simmering* of concepts and wording to reduce this into its most potent essence. You gotta reduce your sauce, otherwise its just weird flavoured water that you're pouring on your meal. Just drink soup if you want to do that.

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

### <a href="/ExampleDecisions.md">Example Decision Stacks</a>

1. <a  href="/Code.md" name="Code">**Code**</a>
    1. Version control
    2. Clear branching and commit strategy
    2. Sane defaults
    3. Hygeine for code and version control
    4. Semantic versioning to allow your project to become an easily manageable dependecy for something else

2. <a  href="/Dependencies.md" name="Dependencies">**Dependencies**</a>
    1. Package managers
    2. Semantic versioning allowing dependency updates and changes to be managed in a standard and predictable way
    3. Isolation and separation of concerns

3. <a  href="/RequiredServices.md" name="RequiredServices">**Required Services**</a>
    1. Service drivers or providers isolated for configurability / injection
    2. Wrap and/or abstract environment/driver specific stuff so a configuration change can do it
    3. Tolerate unavailability with retries, queueing, volatile state usage.

4. <a  href="/Configuration.md" name="Configuration">**Configuration**</a>
    1. Config should be provisioned by environment so that configuration leads to automatic flexibility and hot swapping of configurable elements.
    2. Config is never in code, because if it is it becomes code.

5. <a  href="/Build.md" name="Build">**Build**</a>
    1. Transformation of code, dependencies, assets and configuration into a runnable package within an environment
    2. Easily testable (preferrably automatically tested)
    2. Indempotent, safe, logged, verbose processes.

6. <a  href="/Document.md" name="Document">**Document**</a>
    1. Code should be written clearly so that it can self document
    2. Comments should be employed when code is necessarily unclear
    3. Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.
    4. README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)
    5. How-to's and onboarding information should be easily accessible and outlined.
    6. A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives
    7. A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.
    8. Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.
    9. Relevant information and non-functional artifacts should be managed and accessible eg. Confluence

7. <a  href="/Test.md" name="Test">**Test**</a>
    1. Sanity checks for checking dependencies / assumed things like folder structure, specific files, dumb stuff not obviously required.
    2. Unit testing
    3. Integration testing for required Services with mockable or memoized inputs
    4. End-to-end testing - test the software with connected services as a whole.
    5. User testing - test as an agent utilizing the software.
    6. Verification testing - after events such as releases or environment changes re-run all tests and treat it like a first release.

8. <a  href="/Run.md" name="Run">**Run**</a>
    1. Start, Stop, Restart, Status of application.
    2. Process managers for crash recovery
    3. Profiling and watchdog processes for real-time information on status and resource usage.

9. <a  href="/Environments.md" name="Environments">**Environments**</a>
    1. Required Services such as configuration can be provisioned by environments
    2. No code changes should be required for moving from one evironment to another
    3. Staged environments should be as close to equivalent as possible 
    4. Environments should be entirely isolated from eachother, if they are not then they should be considered a single logical environment
    5. Environments are a major source of erosion, so resource usage and environmental side effects should be monitored and constrained.

10. <a href="/EventingandLogging.md" name="EventingandLogging">**Eventing and Logging**</a>
    1. At some time everything that the application does or has happen to it will be of interest to someone.
    2. Future business logic will want to work on arbitrary past data.
    3. Immutable data + Events + Event Handlers as Mutators = Time Travelling Logic
    4. Keep a master event log if possible. Forever.

11. <a href="/Profiling.md" name="Profiling">**Profiling**</a>
    1. At all times the resource usage of the application should be known as well as the history of that usage.

12. <a href="/Admin.md" name="AdministrativeandTertiaryProcesses">**Administrative and Tertiary Processes**</a>
    1. Interval based reports or sporadically required tasks should be in code somehow, documented and configurable to the standard of the application.
    2. If not in code these processes should be defined and documented in a way such that any layperson can do it with the right access.
    3. Data imports and exports
    4. Arbitrary reports on anything at all.
    5. Auditing
    6. Erasing and locking down things if required

13. <a href="/CICD.md" name="ContinuousIntegration/ContinuousDeployment">**Continuous Integration / Continuous Deployment**</a>
    1. Committing work to version control can be seen as a logical step forward i.e. feature completed, bug fixed, refactor completed. This can and should be used to pass the software through all other safely automatable steps.
    2. Clear branching and commit strategy allows predictable results from watching for changes in a code repository.
    3. Well defined, safe and verbose Builds allow automatic builds from changes in watched code repositories.
    4. Separated and complete Testing suites allow for maximum reasonable testing to be done after a Build.
    5. Isolated predictable environments that provision configuration inputs means that built artifacts can be moved to arbitrary environments without needing forward knowledge about their differences or effects of being present in those environments.
    6. Run strategies allow for any programmable agent to check the status, stop the application, update artifacts, and then start it again. Process managers and profiling also allow for at least a basic level of self-healing applications.
    7. Eventing and Logging allows the process of preparing and deploying the application can be part of the application's auditable and watchable master event log. This provides a logical entry point for Software Life into Maturity considerations.
    8. In conclusion: **Commit** -> **Build** -> **Test** -> **Deploy** -> **Run** -> **Log** / **Profile** / **Administer** -> **Nice**. Or any subset or superset of that flow.

14. <a href="/SoftwareLifeIntoMaturity.md" name="SoftwareLifeintoMaturity">**Software Life into Maturity** </a>
    1. Maintenance such as patches, upgrades, breaking changes to dependencies
    2. The application should communicate somehow any foreseen problems occurring
    3. There should be some strategy or policy on how to manage required resources over time - up and down.

15. <a href="/Security.md" name="Security">**Security**</a>
    1. Every line of code, every dependency, every service, every environment, every configuration, every Event, every generated log, all data, all processes, all communications, all side-channels must be maintainable, patchable, auditable and assumed to be under constant opportunistic attack
    2. Obscurity is not security
    3. The application will be exploited and broken so there must be a strategy for identifying, managing, understanding and cleaning-up after a breach.