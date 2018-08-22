# Example Decisions
## Stack 1:
  - Node with NPM
  - Postgres DB
  - Kubernetes with docker images for orchestration
  - Atlassian services
    - Bitbucket
    - Jira
    - Confluence
    - Bamboo



1. <a  href="/Code.md" name="Code">**Code**</a>
    1. Version control
        - **Git on Bitbucket**
    2. Clear branching and commit strategy
        - **Cactus model. Feature branches -> master. master is dev. tag *for test and/or prod*
    2. Sane defaults
        - **master is dev, no production creds in code**
    3. Hygeine for code and version control
        - **keep commit messages informative, keep removing old branches**


2. <a  href="/Dependencies.md" name="Dependencies">**Dependencies**</a>
    1. Package managers
        - **npm for JS**
        - **docker for containers**
        - **kubernetes for infra**

3. <a  href="/RequiredServices.md" name="RequiredServices">**Required Services**</a>
    1. Service drivers or providers isolated for configurability / injection
        - **kubernetes helps**
    2. Wrap and/or abstract environment/driver specific stuff so a configuration change can do it
        - **kubernetes with configmaps and secrets**

4. <a  href="/Configuration.md" name="Configuration">**Configuration**</a>
    1. Config should be provisioned by environment so that configuration leads to automatic flexibility and hot swapping of configurable elements.
        - **kubernetes**
    

5. <a  href="/Build.md" name="Build">**Build**</a>
    1. Transformation of code, dependencies, assets and configuration into a runnable package within an environment
        - **npm + bamboo**
    2. Easily testable (preferrably automatically tested)
        - **mocha tests + gwen-web later**
    2. Indempotent, safe, logged, verbose processes.
        - **bamboo plans**

6. <a  href="/Document.md" name="Document">**Document**</a>
    1. Code should be written clearly so that it can self document
    2. Comments should be employed when code is necessarily unclear
    3. Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.
        - **jira + bitbucket + confluence**
    4. README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)
        - **a-yup**
    5. How-to's and onboarding information should be easily accessible and outlined.
        - **confluence**
    6. A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives
        - **confluence**
    7. A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.
        - **confluence**
    8. Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.
        - **thank u atlassian**
    9. Relevant information and non-functional artifacts should be managed and accessible eg. Confluence
        - **^^^**

7. <a  href="/Test.md" name="Test">**Test**</a>
    1. Sanity checks for checking dependencies / assumed things like folder structure, specific files, dumb stuff not obviously required.
        - **mocha and kubernetes**
    2. Unit testing
        - **mocha**
    3. Integration testing for required Services with mockable or memoized inputs
        - **mocha and koob**
    4. End-to-end testing - test the software with connected services as a whole.
        - **DUNNO**
    5. User testing - test as an agent utilizing the software.
        - **gwen-web**
    6. Verification testing - after events such as releases or environment changes re-run all tests and treat it like a first release.
        - **necessarily manual**

8. <a  href="/Run.md" name="Run">**Run**</a>
    1. Start, Stop, Restart, Status of application.
        - **npm, bamboo, kubernetes**
    2. Process managers for crash recovery
        - **kubernetes**
    3. Profiling and watchdog processes for real-time information on status and resource usage.
        - **kubernetes**

9. <a  href="/Environments.md" name="Environments">**Environments**</a>
    1. Required Services such as configuration can be provisioned by environments
        - **kubernetes configmaps and secrets**
    2. No code changes should be required for moving from one evironment to another
        - **this is why kubernetes is the industry standard god damn**
    3. Staged environments should be as close to equivalent as possible
        - **just another koob cluster baby**
    4. Environments should be entirely isolated from eachother, if they are not then they should be considered a single logical environment
        - **just anoter kloobster**
    5. Environments are a major source of erosion, so resource usage and environmental side effects should be monitored and constrained.
        - **kloobs provide many opportunities for this also**

10. <a href="/EventingandLogging.md" name="EventingandLogging">**Eventing and Logging**</a>
    1. At some time everything that the application does or has happen to it will be of interest to someone.
        - **DUNNO YET**
        - **but kubernetes cluster-level logging with persistent storage is a start**
    2. Future business logic will want to work on arbitrary past data.
    3. Immutable data + Events + Event Handlers as Mutators = Time Travelling Logic
    4. Keep a master event log if possible. Forever.

11. <a href="/Profiling.md" name="Profiling">**Profiling**</a>
    1. At all times the resource usage of the application should be known as well as the history of that usage.
        - **k o o b**

12. <a href="/Admin.md" name="AdministrativeandTertiaryProcesses">**Administrative and Tertiary Processes**</a>
    1. Interval based reports or sporadically required tasks should be in code somehow, documented and configurable to the standard of the application.
        - **stateful workloads in kubernetes and/or bamboo plans**
    2. If not in code these processes should be defined and documented in a way such that any layperson can do it with the right access.
        - **bamboo plans are real easy to click on**
    3. Data imports and exports
    4. Arbitrary reports on anything at all.
    5. Auditing
        - **koob gives many datapoints**
    6. Erasing and locking down things if required
        - **koob encapsulates everything so this is possible**

13. <a href="/CICD.md" name="ContinuousIntegration/ContinuousDeployment">**Continuous Integration / Continuous Deployment**</a>

    8. In conclusion: **Commit** -> **Build** -> **Test** -> **Deploy** -> **Run** -> **Log** / **Profile** / **Administer** -> **Nice**. Or any subset or superset of that flow.
        - **COMMIT** - bitbucket*
        - **BUILD** - bamboo*
        - **TEST** - bamboo with mocha + gwen-web + manual*
        - **DEPLOY** - bamboo + kubernetes*
        - **RUN** - kubernetes*
        - **LOG** - kubernetes + internal logging*
        - **PROFILE** - kubernetes*
        - **ADMINISTER** - bamboo + kubernetes*
        - **NICE** - yeah it is*

14. <a href="/SoftwareLifeIntoMaturity.md" name="SoftwareLifeintoMaturity">**Software Life into Maturity** </a>
    1. Maintenance such as patches, upgrades, breaking changes to dependencies
      - **DUNNO BUT ALMOST**
    2. The application should communicate somehow any foreseen problems occurring
      - **koob helps but DUNNO**
    3. There should be some strategy or policy on how to manage required resources over time - up and down.
      - **koob does this so much and so hard**

15. <a href="/Security.md" name="Security">**Security**</a>
    1. Every line of code, every dependency, every service, every environment, every configuration, every Event, every generated log, all data, all processes, all communications, all side-channels must be maintainable, patchable, auditable and assumed to be under constant opportunistic attack
    2. Obscurity is not security
    3. The application will be exploited and broken so there must be a strategy for identifying, managing, understanding and cleaning-up after a breach.
      - **i dunno security is hard**
      - **hopefully the security team can bang on our shit forever**