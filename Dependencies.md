# Dependencies

## Package managers

Use whatever the standard for your language is. 
  - Node/JS: [yarn](https://yarnpkg.com/) or [npm](https://www.npmjs.com/)

## Patching and upgrading

The package manager handles the operations of downloading, caching and tracking dependency artifacts. Combined with [Semantic Versioning](https://semver.org/) you can (to some degree) specify your update policy, and then you actually do the updating as part of your development process!

## Isolation and separation of concerns

Using a package manager and approaching these dependencies like black boxes with known inputs and outputs -- you can go ahead and not give a damn about their specifics. Just worry about how you use them and how you choose to extend them. Separated! [Open/Closed Principle!](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)