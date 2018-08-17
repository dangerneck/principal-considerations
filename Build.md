# Build

## Transformation of code, dependencies, assets and configuration into a runnable package within an environment

For Node/JS npm + some kind of shell script is a good start, and often as far as you need to go. webpack if you're doing front-end js. 

## Easily testable (preferrably automatically tested)

For Node/JS npm + mocha for the code portion of testing

## Indempotent, safe, logged, verbose processes

Design the build and test steps so they follow the Open/Closed principle, and also make sense and don't do not-immediately-obvious things that are important!