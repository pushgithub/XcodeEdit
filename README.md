<img src="https://cloud.githubusercontent.com/assets/75655/24417155/91254d68-13e7-11e7-91eb-470380161633.png" width="154" alt="XcodeEdit">
<hr>

Reading _and writing_ the Xcode pbxproj file format, from Swift!

The main goal of this project is to generate `project.pbxproj` files in the legacy OpenStep format used by Xcode. Using this, a project file can be modified without changing it to XML format and causing a huge git diff.

Currently, this project is mostly used to support [R.swift](https://github.com/mac-cain13/R.swift).

⚠️  Limited support for modificiation
-----

At this time, there are only limited APIs for modifying a project file.
Only features that are actually needed by R.swift are implemented. There is no generic way to modify the project strucuture.


Usage
-----

This reads a xcodeproj file (possibly in XML format), and writes it back out in OpenStep format:

```swift
let xcodeproj = URL(fileURLWithPath: "Test.xcodeproj")

let proj = try! XCProjectFile(xcodeprojURL: xcodeproj)

try! proj.write(to: xcodeproj, format: PropertyListSerialization.PropertyListFormat.openStep)
```


Releases
--------

 - 2.13.0 - 2025-03-16 - Fix serialization for Xcode 16 projects
 - 2.12.0 - 2025-02-08 - Fix Linux support
 - 2.11.1 - 2024-11-03 - Make syncGroups property internal
 - 2.11.0 - 2024-11-03 - Add computed fullPath to PBXFileSystemSynchronizedRootGroup
 - 2.10.2 - 2024-09-24 - Add PBXFileSystemSynchronizedGroupBuildPhaseMembershipExceptionSet
 - 2.10.1 - 2024-09-19 - Serialization fix for file system synchronized directories
 - 2.10.0 - 2024-09-19 - Add support for file system synchronized directories in Xcode 16
 - 2.9.2 - 2023-09-20 - Fix warnings in Xcode 15
 - 2.9.1 - 2023-09-10 - Add support for local Swift packages
 - 2.9.0 - 2022-11-07 - Add removePackage function to XCSwiftPackageProductDependency
 - 2.8.0 - 2021-11-17 - Add fields to PBXShellScriptBuildPhase
 - 2.7.7 - 2020-05-08 - Add support for remote swift packages
 - 2.7.6 - 2020-04-25 - Add support for SPM product dependencies
 - 2.7.5 - 2020-02-13 - Add support for PBXBuildRule
 - 2.7.4 - 2019-10-04 - Improved parsing of optional fields
 - 2.7.3 - 2019-07-28 - Use Swift native random function
 - 2.7.2 - 2019-07-28 - Improved suport for SPM
 - 2.7.0 - 2019-06-10 - Add suport for Xcode 13 SPM objects
 - 2.6.0 - 2019-01-23 - Improved error messages for broken project files
 - 2.5.2 - 2018-12-30 - Fixes incorrect generation of relative URLs, again
 - 2.5.1 - 2018-12-28 - Fixes incorrect generation of relative URLs
 - 2.5.0 - 2018-12-11 - Improve serialization for escaped identifiers in pbxproj
 - 2.4.2 - 2018-10-03 - Fix escaped strings in serializer
 - 2.4.0 - 2018-07-03 - Add support for SourceTreeFolder type `PLATFORM_DIR`
 - 2.3.0 - 2018-06-17 - Add support for PBXLegacyTarget
 - 2.2.0 - 2018-04-04 - Swift 4.1 support
 - 2.1.0 - 2018-01-23 - Add some specific modification functions for R.swift
 - **2.0.0** - 2017-12-17 - Support parsing for "broken" project files
 - 1.1.0 - 2017-05-07 - Error types now public
 - **1.0.0** - 2017-03-28 - Rename from Xcode.swift to XcodeEdit
 - **0.3.0** - 2016-04-27 - Fixes to SourceTreeFolder
 - 0.2.1 - 2015-12-30 - Add missing PBXProxyReference class
 - **0.2.0** - 2015-10-29 - Adds serialization support
 - **0.1.0** - 2015-09-28 - Initial public release


Licence & Credits
-----------------

XcodeEdit is written by [Tom Lokhorst](https://twitter.com/tomlokhorst) and available under the [MIT license](https://github.com/tomlokhorst/XcodeEdit/blob/develop/LICENSE), so feel free to use it in commercial and non-commercial projects.

