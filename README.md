###[Bower][1]

#### What it is:

 - “Package manager for the web”.
 - Unopinionated - no system-wide dependencies and exposes an API that more opinionated frameworks can
   use (such as Yeoman) 
 - Runs over Git 
 - Package virtually any kind of asset or type of component

#### Use it when:
You want to consume and/or share resources across various projects.  Typically these are front-end resources, such as CSS, javascript libraries, etc, but Bower does not limit you to a particular resource or file type.

#### Why use it:
 - Simple to use and share 
     - simply specify what files you want to share/release (or rather which files you don’t **) and they are made available to others when they execute `bower install <your package>` 
     - Add a git tag (`git tag -a v1.4 -m 'my version 1.4'`) to your repository and bower is automatically updated 
 - Make your package's dependencies visible to others
 - Allows a lot of control in how you define your dependencies.  Allowing you to specify exact version or ranges of versions.
 - Separate runtime dependencies from development dependencies 
    - This separation allows you keep testing dependencies isolated and keeps them from leaking into your release

** You essentially have to negate all the files except the ones you want to share via the “ignore”: [files]

#### How to use it:
##### Installation:
Via NPM `npm install -g bower`

##### Typical workflow

 1. Create a bower.json file via `bower init`
 - This holds all of the package information, such as dependencies, dev-dependencies, package name and description, authors, etc
 - Yeoman will generate this file for you if you create an Angular app with Yeoman’s Angular Generator
 2. Define the package
 - `name (required)`: The name of your package. version: A semantic
   version number (see semver). 
 - `main [string|array]`: The primary endpoints of your package. 
 - `ignore [array]`: An array of paths not needed in production that you want Bower to ignore when installing
   your package. 
 - `dependencies [hash]`: Packages your package depends upon in production. Note that you can specify ranges of versions for your dependencies. 
 - `devDependencies [hash]`: Development dependencies.
 - `private [boolean]`: Set to true if you want to keep the package private and do not want to register the package in future.
 3. Install necessary packages
 - This can be done by adding the packages names in the bower.json file or `bower install -s <package-name>` which is typically more convenient
 4. Share by `bower register <my-package-name> <git-endpoint>`

##### Basic Commands

 - `bower init` - initializes/creates an empty bower.json file
 - `bower install -S <package>` (or `bower install -S <package>#<version>`) - downloads a dependency for your package.  The `-S` will persist it in your bower.json file.
 - `bower update` - updates all your dependencies.  Running `bower update <package>` will update a specific dependency
 - `bower search <search string>` (or from the [bower.io site][2])

#### Problems:
 - Because it is unopinionated, everyone has an opinion on what they release and how to structure their release folder
 - The bower repository does not currently allow renaming or deleting packages, which becomes problematic if you name something incorrectly

  [1]: http://bower.io/
  [2]: http://bower.io/search
