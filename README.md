# hermit
 A fast-and-dirty hermetic build system

# Overview
 A hermetic build system, at it's core, has completely isolated and reproducible builds. This is a key component to correctness. Given the software world that we live in (multiple package managers, flaky remote artifact sources, etc), this can be a daunting goal to achieve. As opposed to starting from the bottom and building up, hermit will attempt to provide hermetic tools while allowing non-hermetic behavior. This enables ease of adoption, while providing better and better experiences the more users move away from non-hermetic behavior.

 The biggest problem with adopting a hermetic build system is that, in order to be truly hermetic, all your dependencies (both explicit and transitive) also need to be moved into the hermetic build system (or at least it's artifact repository) in order for your project to be truly hermetic. This is a massive investment up front, especially for cases where you need to push all the way down to low-level native libraries like libc. Instead, hermit will provide the high level tools necessary to create hermetic builds (a dependency graph, and the ability to depend on other hermit packages), but will not force exclusive hermit dependencies (or even using hermit builders). Genrules will be the law of the land, with an "it's better the more you move into hermit" attitude. 

# Goals and Caveats
#### These goals are lifted with love from Fahrzin Hemmati's [blog post on hermetic builds](http://blog.fahhem.com/2013/12/hermetic-build-systems/)

1) Core language support
 - Java
 - Python (pure)

2) Genrule support
 - hermit will, at v0, be exclusively genrules. This allows for inherently non-hermetic behavior, like simply subshelling out to another build/dependency management tool like maven or npm.

3) Easy Extension
 - Since this is still in ideation, this is a high-level goal, as opposed to a proposal of a plugin or sidecar system. Extensibility is good.


