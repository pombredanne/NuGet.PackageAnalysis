NuGet Package Analysis Rules
============================

Just like with Code Analysis, NuGet package creation can be guarded by a set of Package Analysis Rules.
For a walkthrough on how to create these yourself, I'd recommend you to check out the NuGet Team blog: [http://blog.nuget.org/20121023/creating-custom-package-rules-for-your-build.html][1]

In this repository I'll track some of my own custom rules. They are provided AS IS, but feel free to file an issue or submit a pull request if you hit something unexpected or want to contribute.

SemanticVersionRule
-------------------

My first package analysis rule is a very simple yet important one: verify whether the package being created has been given a proper Semantic Version compliant without violating the official Specification available at [http://semver.org][2].

As NuGet (currently version 2.2) does not fully support this Spec (yet - until SemVer hits RTM), this Package Analysis Rule can only check for violations **AFTER** NuGet created an instance of the *SemanticVersion* class internally before reaching the validation logic. This means I can't (yet) built the checks for the SemVer build number annotation.

*Please note: NuGet currently still ignores the PackageIssueLevel.Error and traces a warning instead. As soon as NuGet supports this you'll notice package creation will fail (no need to update this assembly as it already uses the Error level).*

Deploying the Package Analysis Rules
------------------------------------
Simply download the binaries and drop them in the `%localappdata%\nuget\commands` directory

[1]:http://blog.nuget.org/20121023/creating-custom-package-rules-for-your-build.html
[2]:http://semver.org