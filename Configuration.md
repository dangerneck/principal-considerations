# Configuration

## Config should be provisioned by some external method or service so that configuration leads to automatic flexibility and hot swapping of configurable elements

[dotenv](https://github.com/motdotla/dotenv) is always a great place to start. But any kind of config provisioning is good as long as you treat it like a particularly important Required Service.

## Config is never in code, because if it is it becomes code

There are no exceptions.