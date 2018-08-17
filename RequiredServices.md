# Required Services

## Service drivers or providers isolated for configurability / injection

This is very dependent on your specific implementations, but a required service is like a dependency that must have some operational logic and outside uncontrollable and unpredictable state. So a little more flexibility is required. 

## Wrap and/or abstract environment/driver specific stuff so a configuration change can do it

Dependency Injection! Inversion of control! Or just don't make assumptions your code doesn't explicitly check! DI is not such a thing in JS because import/require do a pretty good job and you can bend things enough anyway.

## Tolerate unavailability with retries, queueing, volatile state usage

Yeah, your API is so nice and solid and you have the sickest load balancing in place and the best caching policy anyone has ever imagined and your cloud provider guarantees 99.95% uptime which is like, pfff, pretty much all the time! And when it fails anyway it's sooooooo brief and quick and who cares! Like, even Facebook goes down sometimes!

Everything working as expected is an assumption that should be tested before it is required to be true.

Retries are good! There's no shame in a retry! It doesn't have to be just try / catch! You know what? Exceptions are stupid! I hate them! Handle as much failure as you can! Exceptions are basically giving your software the emotional maturity of a toddler. Hey, can you please get daddy his database query result? Oh, it timed out? Why are you throwing everything away? Don't cry, you can try again! No, it's not ruined forever! You need a nap, I knew I should have made you nap before we left the house today. Now you're screaming, that's really just not ideal. Etc.

Queues are cool too, they handle spikes much better than retries since they don't amplify load-related failures. 