# Principal Considerations
## or
## How to try to develop web applications without getting in your own way or ruining it for yourself and others or being a dingus.



## Top-tier Considerations

1. **Code**
2. **Dependencies**
3. **Required Services**
4. **Configuration**
5. **Build**
6. **Document**
7. **Test**
8. **Run**
9. **Environments**
10. **Eventing and Logging**
11. **Profiling**
12. **Administrative and Tertiary Processes**
13. **Software Life into Maturity** 
14. **Security**

## Second-tier Considerations

1. **Code**
    1. Version control
    2. Continuous integration policy
    3. Sane defaults
    4. Hygeine

2. **Dependencies**
    1. Package managers
    2. Patching and upgrading
    3. Isolation and separation of concerns

3. **Required Services**
    1. Service drivers or providers isolated for configurability / injection
    2. Wrap and/or abstract environment/driver specific stuff so a configuration change can do it
    3. Tolerate unavailability with retries, queueing, volatile state usage.

4. **Configuration**
    1. Config should be provisioned by environment so that configuration leads to automatic flexibility and hot swapping of configurable elements.
    2. Config is never in code, because if it is it becomes code.

5. **Build**
    1. Transformation of code, dependencies, assets and configuration into a runnable package within an environment
    2. Easily testable (preferrably automatically tested)
    2. Indempotent, safe, logged, verbose processes.

6. **Document**
    1. Code should be written clearly so that it can self document
    2. Comments should be employed when code is necessarily unclear
    3. Project management methodology should create a documentation artifact that can provide context and connections between actions, events and assets.
    4. README.md should be all a developer needs to read to get from checking out from version control to running a development version locally (with passing tests)
    5. How-to's and onboarding information should be easily accessible and outlined.
    6. A decision register should be kept to outline decisions made throughout the software's life, why they were made, by whom (possibly) and against what alternatives
    7. A technical debt register should be kept to outline trade-offs made, mistakes identified, possible improvements identified, incoming refactors etc.
    8. Opportunistic use of context-providing links eg Jira codes in commit message; leave breadcrumbs wherever you can.
    9. Relevant information and non-functional artifacts should be managed and accessible eg. Confluence

7. **Test**
    1. Sanity checks for checking dependencies / assumed things like folder structure, specific files, dumb stuff not obviously required.
    2. Unit testing
    3. Integration testing for required Services with mockable or memoized inputs
    4. End-to-end testing - test the software with connected services as a whole.
    5. User testing - test as an agent utilizing the software.
    6. Verification testing - after events such as releases or environment changes re-run all tests and treat it like a first release.

8. **Run**
    1. Start, Stop, Restart, Status of application.
    2. Process managers for crash recovery
    3. Profiling and watchdog processes for real-time information on status and resource usage.

9. **Environments**
    1. Configuration is provisioned by environments as necessary
    2. No code changes should be required for moving from one evironment to another
    3. All environments should be as close to equivalent as possible
    4. Environments should be entirely isolated from eachother

10. **Eventing and Logging**
    1. At some time everything that the application does or has happen to it will be of interest to someone.
    2. Future business logic will want to work on arbitrary past data.
    3. Immutable data + Events + Event Handlers as Mutators = Time Travelling Logic
    4. Keep a master event log if possible. Forever.

11. **Profiling**
    1. At all times the resource usage of the application should be known as well as the history of that usage.

12. **Administrative and Tertiary Processes**
    1. Interval based reports or sporadically required tasks should be in code somehow, documented and configurable to the standard of the application.
    2. If not in code these processes should be defined and documented in a way such that any layperson can do it with the right access.
    3. Data imports and exports
    4. Arbitrary reports on anything at all.
    5. Auditing
    6. Erasing and locking down things if required

13. **Software Life into Maturity** 
    1. Maintenance such as patches, upgrades, breaking changes to dependencies
    2. The application should communicate somehow any foreseen problems occurring
    3. There should be some strategy or policy on how to manage required resources over time - up and down.

14. **Security**
    1. Every line of code, every dependency, every service, every environment, every configuration, every Event, every generated log, all data, all processes, all communications, all side-channels must be maintainable, patchable, auditable and assumed to be under constant opportunistic attack
    2. Obscurity is not security
    3. The application will be exploited and broken so there must be a strategy for identifying, managing, understanding and cleaning-up after a breach.

## Examples
Here I will put what specific approaches I currently enjoy for all of the above.

### TODO lol