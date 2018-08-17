# Continuous Integration / Continuous Deployment

At the point you're doing this you probably have a clear choice. If not here's a roadmap:

  1. shell / batch scripts for build, test, run
  2. a single script that handles the build, test, run scripts making it a 1 click / 1 call process
  3. a service that watches a repository for changes then runs the above process
  4. you're done, or you get Team City or Bamboo or something running.