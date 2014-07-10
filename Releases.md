## Introduction

Here's a list of recent releases of Closure Compiler.  We update the source distribution and the compile service (at http://closure-compiler.appspot.com) every couple weeks, depending on the changes that have been made.

For complete list of changes refer to the [change log](https://github.com/google/closure-compiler/commits/master)

## Details

### June 25, 2014 (v20140625)
Major changes in this release:
 - Variables in externs are copied to the "window" object. This means that properties can be accessed as "window.foo" even if they're only declared in the externs as "var foo;"
 - Added support for goog.module() which helps the transition to ES6 modules.
 - Added support for (non labs-prefixed) goog.defineClass which helps the transition to ES6 classes.
 - Added @package access control mode which means the given variable can be accessed from within the same package (like package-private in Java). Thanks to 20% contributor Brendan Linn.
 - Several fixes to make the compiler work with node.js code, mostly from @nicks.
 - Turn on the InferConst pass, which allows the compiler to do more typechecking and inlining.
 - Flatten module type expressions during module-preprocess.
 - Added --source_map_location_mapping flag. Thanks @terencehonles!
 - Added --output_wrapper_file flag. Thanks @retromodular!
 - Enable GatherExternsFromTypes pass for better handling of typedefs in externs.
 - Removed the old Rhino JS parser, since we are now fully switched over to the new ES6 parser.
 - Lots of work on transpiling ES6 to ES3, as well as running some checks directly on ES6 code. Big thanks to our interns, Matt Loring and Michael Zhou for pushing this work forward.
 - Lots of work on the new type inference system (not enabled by default yet)
 - Fixed Github issues: #110, #431, #432, #435, #439, #477

### May 8, 2014 (v20140508)
 - Improvements to make goog.defineClass easier to use
 - Improvements to the command line option syntax, including file globs and -W/-O flags for warning levels and optimizations, respectively. See [PR #403](https://github.com/google/closure-compiler/pull/403)
 - Added sourceMapInputFiles option, to map from generated JS (for example, from Angular templates) to the original source.
 - New parser is enabled by default.
 - Several improvements to performance and memory usage.
 - Lots of work on the new type inference system (not on by default yet).
 - Initial support for some ES6 features in whitespace-only mode.
 - Fixed issues: [issue 102](https://github.com/google/closure-compiler/issues#issue/102), [issue 119](https://github.com/google/closure-compiler/issues#issue/119), [issue 123](https://github.com/google/closure-compiler/issues#issue/123), [issue 186](https://github.com/google/closure-compiler/issues#issue/186), [issue 310](https://github.com/google/closure-compiler/issues#issue/310), [issue 387](https://github.com/google/closure-compiler/issues#issue/387), [issue 388](https://github.com/google/closure-compiler/issues#issue/388), [issue 389](https://github.com/google/closure-compiler/issues#issue/389), [issue 390](https://github.com/google/closure-compiler/issues#issue/390), [issue 400](https://github.com/google/closure-compiler/issues#issue/400) 

### April 7, 2014 (v20140407)
- Add a warning for the use of goog.base for projects that want to support strict mode in uncompiled code.
- Add "arguments.callee", "arguments.caller", "Function.prototype.arguments" and "Function.prototype.caller" to the "strict" mode checks.
- Have the runtime type checker type-check Object as any object type, possibly with an exotic prototype - not necessarily inheriting from a standard Object.
- Move the checking for 'with' statements into the StrictModeCheck.
- Add an InferConsts pass, and use it demonstrate that it fixes problems with CommonJS aliases (off by default).
- Lots of changes in the new type inference system (not enabled yet in this release)
- A few changes in the new parser (not enabled yet in this release)
- Add a warning for functions with a nullable return type that never return null (off by default)
- Issues fixed: [issue 354](https://github.com/google/closure-compiler/issues#issue/354), [issue 853](https://github.com/google/closure-compiler/issues#issue/853), [issue 1217](https://github.com/google/closure-compiler/issues#issue/1217), [issue 1243](https://github.com/google/closure-compiler/issues#issue/1243), [issue 1244](https://github.com/google/closure-compiler/issues#issue/1244), [issue 1264](https://github.com/google/closure-compiler/issues#issue/1264), [issue 1265](https://github.com/google/closure-compiler/issues#issue/1265), [issue 1260](https://github.com/google/closure-compiler/issues#issue/1260), [issue 1267](https://github.com/google/closure-compiler/issues#issue/1267), [issue 1270](https://github.com/google/closure-compiler/issues#issue/1270)

### March 3, 2014 (v20140303)
- Better inference for polymorphic functions as arguments.
- Improved goog.asserts typing.
- Gather property names from record types in externs (off by default, accessible through Java API as gatherExternsFromTypes option).
- Make cross-module method motion deterministic.
- Remove old code
- In progress: new type inference: generics for functions and classes, type casts.
- In progress: new parser to replace Rhino (currently off by default).
- Fixed [issue 719](https://github.com/google/closure-compiler/issues#issue/719), [issue 926](https://github.com/google/closure-compiler/issues#issue/926), [issue 1032](https://github.com/google/closure-compiler/issues#issue/1032), [issue 1109](https://github.com/google/closure-compiler/issues#issue/1109), [issue 1183](https://github.com/google/closure-compiler/issues#issue/1183), [issue 1198](https://github.com/google/closure-compiler/issues#issue/1198), [issue 1201](https://github.com/google/closure-compiler/issues#issue/1201), [issue 1204](https://github.com/google/closure-compiler/issues#issue/1204), [issue 1205](https://github.com/google/closure-compiler/issues#issue/1205), [issue 1219](https://github.com/google/closure-compiler/issues#issue/1219), [issue 1221](https://github.com/google/closure-compiler/issues#issue/1221), [issue 1222](https://github.com/google/closure-compiler/issues#issue/1222), [issue 1228](https://github.com/google/closure-compiler/issues#issue/1228), [issue 1243](https://github.com/google/closure-compiler/issues#issue/1243).

### January 10, 2014 (v20140110)
- New pass: GatherExternProperties.
- Deleted the RemoveTryCatch pass.
- Includes a work-in-progress new type inference pass.
- Warn about invalid use of id generators.
- Add support for a strict-mode compatible version of goog.base.
- Don't warn about ES3-incompatible property names in externs files.
- Warn about the right class in private-property-access warnings.
- Improvements to the fuzzer.
- Fix [issue 1056](https://github.com/google/closure-compiler/issues#issue/1056), [issue 1131](https://github.com/google/closure-compiler/issues#issue/1131), [issue 1135](https://github.com/google/closure-compiler/issues#issue/1135), [issue 1144](https://github.com/google/closure-compiler/issues#issue/1144), [issue 1147](https://github.com/google/closure-compiler/issues#issue/1147), [issue 1157](https://github.com/google/closure-compiler/issues#issue/1157), [issue 1160](https://github.com/google/closure-compiler/issues#issue/1160), [issue 1166](https://github.com/google/closure-compiler/issues#issue/1166), [issue 1168](https://github.com/google/closure-compiler/issues#issue/1168), [issue 1189](https://github.com/google/closure-compiler/issues#issue/1189).

### November 18, 2013 (v20131118)
- Allow multiple JSDoc tags on the same line.
- Warn for unnecessary casts (disabled by default).
- Add the experimental ES6 parser to our tree; we may make it the default in the future.
- Move compiler to Java 7.
- Initial work on a fuzzer for the compiler.
- Add another smart-name pass before property disambiguation (disabled by default).
- Warn when goog.string.Const.from is not called with a string literal.
- Bug fixes for cross-module method motion.
- Bug fixes for template types.
- Fix [issue 1114](https://github.com/google/closure-compiler/issues#issue/1114), [issue 1116](https://github.com/google/closure-compiler/issues#issue/1116), [issue 1120](https://github.com/google/closure-compiler/issues#issue/1120), [issue 1129](https://github.com/google/closure-compiler/issues#issue/1129).

### October 14, 2013 (v20131014)
- Disable the "rewrite function expressions" pass.
- Improvements in type inference for generics, related to record types and to inheritance.
- Allow unknown and record types in inline type annotations.
- Recognize a function return type as an inline annotation.
- Rotate commutative operators to eliminate parens.
- Fix [issue 1007](https://github.com/google/closure-compiler/issues#issue/1007), [issue 1024](https://github.com/google/closure-compiler/issues#issue/1024), [issue 1047](https://github.com/google/closure-compiler/issues#issue/1047), [issue 1070](https://github.com/google/closure-compiler/issues#issue/1070), [issue 1072](https://github.com/google/closure-compiler/issues#issue/1072), [issue 1073](https://github.com/google/closure-compiler/issues#issue/1073), [issue 1085](https://github.com/google/closure-compiler/issues#issue/1085), [issue 1103](https://github.com/google/closure-compiler/issues#issue/1103).
- Extern updates

### August 23, 2013 (v20130823)
- Experimental export option: exportLocalPropertyDefinitions
- Support of inline type declarations in "var" statements.
- RemoveUnusedClassProperties will now remove properties if a set  exists on a prototype.
- RemoveUnusedClassProperties is now on by default in ADVANCED mode.
- Fix: an 8 year old operator precedence bug (Issue 1062).
- Fix: incorrect variable inlining (Issue 1053)
- CollapseProperties correctness improvements
- Fix: spurious warnings for obviously good logical shifts
- VariableReferenceCheck is now suppressible using existing diagnostic groups.
- Extern updates

### July 22, 2013 (v20130722)
- Stricter missing-property checks for structs.
- Improved type inference for assignments to the prototype property.
- Fix incompatibility between removeUnusedClassProperties and Object.seal, and add the pass to advanced optimizations.
- Open source the code-coverage instrumentation pass.
- Allow constructors with a declared return type to be called without new.
- Bugfixes for goog.inherits used with generic types.
- Better detection of block comments that contain jsdoc tags.
- In ES5 mode, don't quote object literal keys when they're ES3 keywords.
- In ES3 mode, allow ES3 keywords as property names but quote them.
- New jsdoc tag @disposes for use with CheckEventfulDisposal pass to specify particular arguments of a function to be disposed.
- Updated externs for angular, jquery and maps api.
- Fix [issue 1017](https://github.com/google/closure-compiler/issues#issue/1017), [issue 1020](https://github.com/google/closure-compiler/issues#issue/1020), [issue 1021](https://github.com/google/closure-compiler/issues#issue/1021), [issue 1023](https://github.com/google/closure-compiler/issues#issue/1023), [issue 1030](https://github.com/google/closure-compiler/issues#issue/1030), [issue 1033](https://github.com/google/closure-compiler/issues#issue/1033), [issue 1035](https://github.com/google/closure-compiler/issues#issue/1035), [issue 1042](https://github.com/google/closure-compiler/issues#issue/1042), [issue 1043](https://github.com/google/closure-compiler/issues#issue/1043).


### June 3, 2013 (v20130603)
- Produce smaller code for boolean conditional expressions.
- Better type checking for classes that implement or extend generic types.
- More accurate attaching of JSDoc to AST nodes.
- Allow collapse properties to collapse simple global aliases.
- New CheckEventfulObjectDisposal pass for finding memory leaks in JS programs.
- Change RescopeGlobalSymbols to not rewrite variables that do not cross JSModules.
- Fix [issue 965](https://github.com/google/closure-compiler/issues#issue/965), [issue 987](https://github.com/google/closure-compiler/issues#issue/987), [issue 994](https://github.com/google/closure-compiler/issues#issue/994), [issue 1002](https://github.com/google/closure-compiler/issues#issue/1002), [issue 1006](https://github.com/google/closure-compiler/issues#issue/1006), [issue 1008](https://github.com/google/closure-compiler/issues#issue/1008).

### April 11, 2013 (v20130411)
- Improve bad cast detection.
- Add new diagnostic group for @struct/@dict inheritance warnings (checkStructDictInheritance)
- compiler support for goog.define
- experimental optimization: --disambiguate_private_properties
- "strip suffix" improvements
- improved experimental generics: support for user defined classes and interfaces using @template
- removed support for @classTemplate (use @template)
- improved "angular_pass" and bug fixes.
- build type speed improvements for several compiler passes
- new externs: svg, page visibility api, device orientation, device motion events, Intl, Jasmine
- misc extern corrections
- Fixes [issue 921](https://github.com/google/closure-compiler/issues#issue/921), [issue 925](https://github.com/google/closure-compiler/issues#issue/925), [issue 927](https://github.com/google/closure-compiler/issues#issue/927), [issue 931](https://github.com/google/closure-compiler/issues#issue/931), [issue 936](https://github.com/google/closure-compiler/issues#issue/936), [issue 937](https://github.com/google/closure-compiler/issues#issue/937), [issue 942](https://github.com/google/closure-compiler/issues#issue/942), [issue 957](https://github.com/google/closure-compiler/issues#issue/957)

### February 27, 2013 (v20130227)
- Moved to git!
- Added support for inline jsdocs for type annotations
- Don't reorder the condition of an IF if it contains side effects
- Speed up the closurePrimitives pass
- Add new diagnostic group for @struct/@dict inheritence warnings
- Add externs for W3C gamepad
- Support for type declarations with @const
- Function declarations are no longer allowed in 'if' blocks, to be consistent with ecmascript5 strict mode
- Better generics type-checking
- Faster phase-ordering algorithm
- @const on a constructor prevents it from being subclassed when visibility checks are on
- Faster dead-code elimination
- Fixed a bug where type inference wouldn't converge
- Fixes [issue 873](https://github.com/google/closure-compiler/issues#issue/873), [issue 871](https://github.com/google/closure-compiler/issues#issue/871), [issue 864](https://github.com/google/closure-compiler/issues#issue/864), [issue 862](https://github.com/google/closure-compiler/issues#issue/862), [issue 884](https://github.com/google/closure-compiler/issues#issue/884), [issue 874](https://github.com/google/closure-compiler/issues#issue/874), [issue 838](https://github.com/google/closure-compiler/issues#issue/838), [issue 253](https://github.com/google/closure-compiler/issues#issue/253), [issue 889](https://github.com/google/closure-compiler/issues#issue/889), [issue 901](https://github.com/google/closure-compiler/issues#issue/901), [issue 890](https://github.com/google/closure-compiler/issues#issue/890), [issue 915](https://github.com/google/closure-compiler/issues#issue/915), [issue 916](https://github.com/google/closure-compiler/issues#issue/916), [issue 918](https://github.com/google/closure-compiler/issues#issue/918), [issue 919](https://github.com/google/closure-compiler/issues#issue/919), [issue 922](https://github.com/google/closure-compiler/issues#issue/922), [issue 925](https://github.com/google/closure-compiler/issues#issue/925), [issue 927](https://github.com/google/closure-compiler/issues#issue/927), [issue 921](https://github.com/google/closure-compiler/issues#issue/921)

### December 12, 2012 (r2388)
- support for type declarations with @protected and @private
- dead code pruning of cases from switches with constant conditions.
- type checking fixes
- @struct/@dict annotations
- Stable naming improvements
- new warning: misplaced type annotation
- new diagnostic groups: suspiciousCode, cast, misplacedTypeAnnotation
- Added goog.defineClass support
- Added goog.getMsgWithFallback support
- better method templating support
- better IIFE inference
- better unused class removal
- AMD/CommonJS improvements
- Fixes [issue 867](https://github.com/google/closure-compiler/issues#issue/867), [issue 857](https://github.com/google/closure-compiler/issues#issue/857), [issue 851](https://github.com/google/closure-compiler/issues#issue/851), [issue 271](https://github.com/google/closure-compiler/issues#issue/271), [issue 791](https://github.com/google/closure-compiler/issues#issue/791), [issue 841](https://github.com/google/closure-compiler/issues#issue/841), [issue 764](https://github.com/google/closure-compiler/issues#issue/764), [issue 61](https://github.com/google/closure-compiler/issues#issue/61), [issue 808](https://github.com/google/closure-compiler/issues#issue/808), [issue 820](https://github.com/google/closure-compiler/issues#issue/820), [issue 824](https://github.com/google/closure-compiler/issues#issue/824), [issue 804](https://github.com/google/closure-compiler/issues#issue/804), [issue 821](https://github.com/google/closure-compiler/issues#issue/821)

### September 17, 2012 (r2180)
- Turn on es5 strict checks in VERBOSE mode
- Updated library dependencies (like Guava)
- Added a pass for chrome extension i18n
- Bug fixes for String.prototype.split
- warnings whitelist improvements
- heap pressure improvements
- type-checking improvements in inner scopes
- fixes [issue 726](https://github.com/google/closure-compiler/issues#issue/726), [issue 794](https://github.com/google/closure-compiler/issues#issue/794), [issue 783](https://github.com/google/closure-compiler/issues#issue/783), [issue 787](https://github.com/google/closure-compiler/issues#issue/787), [issue 785](https://github.com/google/closure-compiler/issues#issue/785), [issue 730](https://github.com/google/closure-compiler/issues#issue/730), [issue 779](https://github.com/google/closure-compiler/issues#issue/779), [issue 756](https://github.com/google/closure-compiler/issues#issue/756), [issue 777](https://github.com/google/closure-compiler/issues#issue/777), among others

### July 10, 2012 (r2079)
- Better checks for global names (controlled by @suppress {undefinedNames})
- Better checks for dead code
- Many bug fixes around function inlining, variable inlining
- Adds compiler support for inferred type using type templates in function declarations
- Enforce method inheritance even when @override is not specified
- Some native type inference for goog.bind, goog.partial
- Better type inference for inner functions
- Better type inference for goog.asserts functions
- Emit an error for named functions in a goog.scope (the old compiler just emitted corrupt code). Fixes [issue 737](https://github.com/google/closure-compiler/issues#issue/737)
- Fixes to CommonJS modules ([issue 732](https://github.com/google/closure-compiler/issues#issue/732))
- added a command-line flag to the open-source compiler for type-based optimizations
- added type-based property inlining
- Among many bug fixes, fixes [issue 747](https://github.com/google/closure-compiler/issues#issue/747), [issue 748](https://github.com/google/closure-compiler/issues#issue/748), [issue 735](https://github.com/google/closure-compiler/issues#issue/735), [issue 481](https://github.com/google/closure-compiler/issues#issue/481), [issue 728](https://github.com/google/closure-compiler/issues#issue/728), [issue 718](https://github.com/google/closure-compiler/issues#issue/718), [issue 685](https://github.com/google/closure-compiler/issues#issue/685), [issue 714](https://github.com/google/closure-compiler/issues#issue/714), [issue 711](https://github.com/google/closure-compiler/issues#issue/711), [issue 662](https://github.com/google/closure-compiler/issues#issue/662), [issue 773](https://github.com/google/closure-compiler/issues#issue/773), [issue 772](https://github.com/google/closure-compiler/issues#issue/772), [issue 688](https://github.com/google/closure-compiler/issues#issue/688), [issue 768](https://github.com/google/closure-compiler/issues#issue/768), [issue 769](https://github.com/google/closure-compiler/issues#issue/769), [issue 759](https://github.com/google/closure-compiler/issues#issue/759), [issue 753](https://github.com/google/closure-compiler/issues#issue/753), [issue 729](https://github.com/google/closure-compiler/issues#issue/729), [issue 746](https://github.com/google/closure-compiler/issues#issue/746), [issue 724](https://github.com/google/closure-compiler/issues#issue/724)

### April 30, 2012 (r1918)
- experimental support for jquery primitives
- adds the @expose annotation
- Adds --only_closure_dependencies
- sort closure dependencies by default
- improvements to RescopeGlobalSymbols
- improved type inference
- fixed an infinite loop in --ide_mode, and other parser improvements
- fixes for miscellany issues: [issue 684](https://github.com/google/closure-compiler/issues#issue/684), [issue 696](https://github.com/google/closure-compiler/issues#issue/696), [issue 701](https://github.com/google/closure-compiler/issues#issue/701), [issue 700](https://github.com/google/closure-compiler/issues#issue/700), [issue 689](https://github.com/google/closure-compiler/issues#issue/689), [issue 691](https://github.com/google/closure-compiler/issues#issue/691), [issue 672](https://github.com/google/closure-compiler/issues#issue/672), [issue 709](https://github.com/google/closure-compiler/issues#issue/709), [issue 698](https://github.com/google/closure-compiler/issues#issue/698)

### March 5, 2012 (r1810)
- Build-time improvements
- minor peephole rewriting improvements
- Added better warning controls to the Ant task ([issue 640](https://github.com/google/closure-compiler/issues#issue/640))
- Better type inference ([issue 669](https://github.com/google/closure-compiler/issues#issue/669))
- Removal for goog.addSingletonGetter ([issue 668](https://github.com/google/closure-compiler/issues#issue/668))
- fixed a bug in ide_mode ([issue 663](https://github.com/google/closure-compiler/issues#issue/663))
- better method arity checks
- adds support for @suppress {undefinedNames}
- fixes for miscellany issues: [issue 634](https://github.com/google/closure-compiler/issues#issue/634), [issue 651](https://github.com/google/closure-compiler/issues#issue/651), [issue 652](https://github.com/google/closure-compiler/issues#issue/652), [issue 650](https://github.com/google/closure-compiler/issues#issue/650), [issue 656](https://github.com/google/closure-compiler/issues#issue/656), [issue 643](https://github.com/google/closure-compiler/issues#issue/643), [issue 284](https://github.com/google/closure-compiler/issues#issue/284), [issue 582](https://github.com/google/closure-compiler/issues#issue/582), [issue 647](https://github.com/google/closure-compiler/issues#issue/647), [issue 310](https://github.com/google/closure-compiler/issues#issue/310), [issue 368](https://github.com/google/closure-compiler/issues#issue/368)

### January 23, 2012 (r1741)
- Compiler now preserves code with hidden side-effects in some cases. Addresses [issue 64](https://github.com/google/closure-compiler/issues#issue/64), [issue 398](https://github.com/google/closure-compiler/issues#issue/398)
- In Advanced mode, the compiler is now more aggressive about removing unused properties (RemoveUsedClassProperties).
- Improved jQuery 1.7, Google Maps 3.7, Typed Array and other externs definitions
- Experimental AMD and Common JS module support.
- Parser improvements.
- Better unused variable removal. [issue 641](https://github.com/google/closure-compiler/issues#issue/641)
- Better support for @lends. [issue 314](https://github.com/google/closure-compiler/issues#issue/314)
- Better type checking around conditionals, "Function.bind"/ "goog.bind", etc
- Source maps now use the v3 format by default.
- Removed some obsolete options from CompilerOptions
- Fixes [issue 644](https://github.com/google/closure-compiler/issues#issue/644), [issue 641](https://github.com/google/closure-compiler/issues#issue/641), [issue 638](https://github.com/google/closure-compiler/issues#issue/638), [issue 621](https://github.com/google/closure-compiler/issues#issue/621) [issue 619](https://github.com/google/closure-compiler/issues#issue/619), [issue 618](https://github.com/google/closure-compiler/issues#issue/618), [issue 603](https://github.com/google/closure-compiler/issues#issue/603), [issue 601](https://github.com/google/closure-compiler/issues#issue/601), [issue 600](https://github.com/google/closure-compiler/issues#issue/600), [issue 583](https://github.com/google/closure-compiler/issues#issue/583), [issue 575](https://github.com/google/closure-compiler/issues#issue/575), [issue 314](https://github.com/google/closure-compiler/issues#issue/314) among others

### November 14, 2011 (r1592)
- Fixed support -0.0, [issue 582](https://github.com/google/closure-compiler/issues#issue/582).
- Added support for compile time defines in ant builds, [issue 567](https://github.com/google/closure-compiler/issues#issue/567)
- Fixes for [issue 588](https://github.com/google/closure-compiler/issues#issue/588), [issue 586](https://github.com/google/closure-compiler/issues#issue/586), [issue 581](https://github.com/google/closure-compiler/issues#issue/581), [issue 569](https://github.com/google/closure-compiler/issues#issue/569), [issue 567](https://github.com/google/closure-compiler/issues#issue/567), [issue 566](https://github.com/google/closure-compiler/issues#issue/566), [issue 558](https://github.com/google/closure-compiler/issues#issue/558), [issue 550](https://github.com/google/closure-compiler/issues#issue/550), [issue 544](https://github.com/google/closure-compiler/issues#issue/544), [issue 539](https://github.com/google/closure-compiler/issues#issue/539), [issue 531](https://github.com/google/closure-compiler/issues#issue/531),
- New jQuery 1.7 and Gadget API externs
- Internal AST cleanup, removed unused Token and annotation IDs, unused legacy Rhino classes.
- Added experimental [RescopeGlobalSymbols](http://code.google.com/p/closure-compiler/source/detail?r=1541) pass.
- Add `checkDebuggerStatement` diagnostic group to enable checks for `debugger` statements
- Minor type checking improvements
- Minor optimization improvements
- Updated Guava and Ant dependencies to the latest available
- Webservice support for EcmaScript 5 and 5 Strict


### October 3, 2011 (r1459)
- Bad function inlining bug fixes
- Type system handles more idioms for assigning to the prototype ([issue 537](https://github.com/google/closure-compiler/issues#issue/537))
- Fixes compiler crash in UnreachableCodeElimination and InlineObjectLiterals ([issue 545](https://github.com/google/closure-compiler/issues#issue/545))
- Easier to suppress visiblity warnings
- Extend ExportTestFunctions so that it properly exports test methods defined on objects.
- Various type-checking bug fixes
- The module flags now lets you specify a %basename% placeholder with the name of the module output file.
- Adds an experimental option for more aggressive function inlining
- Other assorted issue fixes: 548, 533. 457, 538, 535, 534, 446, 511, 530, 529, 528

### August 11, 2011 (r1346)
- Bug fixes for using stdin as input that was introduced last release
- Bug fix for live variable analysis to handle expression in for-in loops
- Improve output delimiter to escaped when needed.
- Better warnings for property disambiguation

### August 4, 2011 (r1314)
- Checks for ecmascript5/strict mode
- Improvements to type checking
- Fixed some over-aggressive optimizations in advanced mode
- Local collapsing of object literals
- Extern updates
- [Fix issues 521, 505, 504, 501, 490, 489, 488 and others](http://code.google.com/p/closure-compiler/issues/list?can=1&q=closed-after%3A2011%2F6%2F15+closed-before%3A2011%2F8%2F2+status%3AFixed&colspec=ID+Type+Status+Priority+Component+Owner+Summary&cells=tiles)

### June 15, 2011 (r1180)
- Improvements to line-number reporting
- Interfaces can extend multiple interfaces, with checks for conflicting signatures
- Support for goog.typedef has been removed. Use the @typedef annotation.
- Closure namespaces are @const by default
- Optimization of parseInt, parseFloat
- Emit a warning if a private property overrides another private property
- Make sure functions are called with an appropriate 'this' type
- Add warnings about parameters being reassigned in a way that violates their type definition
- Add warnings if a object has properties defined before the object is defined
- Add duplicate object literal key check to jscompiler es5 strict mode checks
- Update jQuery 1.6 externs
- Fixes issues 459, 477, 482, 486, and many others

### May 2, 2011 (r1043)
- Now emits a warning if a block comment looks like it should be a jsdoc comment.
- Type checking improvements around interfaces.
- Improved handling of constructors defined in object literals.
- 20% smaller source maps (version 2).
- Experimental source map improvements (version 3)
- Rewrite goog.object.create at compile time
- Fix [issue 380](https://github.com/google/closure-compiler/issues#issue/380),407,412,413,416,423, 428

### April 5, 2011 (r964)
- Workaround Firefox parser, [issue 397](http://code.google.com/p/closure-compiler/issues/detail?id=397)
- Workaround Opera parser issue with compiled jQuery, [issue 390](http://code.google.com/p/closure-compiler/issues/detail?id=397)
- Workaround IE handling of vertical tabs in string to number conversions.
- Correct build time performance, [issue 386](http://code.google.com/p/closure-compiler/issues/detail?id=386)
- Fix crash compiling Dojo, [issue 389](http://code.google.com/p/closure-compiler/issues/detail?id=389)
- Improved folding of array and object literals
- [Fixed issues 49, 171, 304, 329, 345, 378, 379, 389, 390, 392, 397, 399](http://code.google.com/p/closure-compiler/issues/list?can=1&q=closed-after%3A2011%2F3%2F22+closed-before%3A2011%2F4%2F5+status%3AFixed)

### March 22, 2011 (r916)
- Added support for @interface declarations with non-function members
- Added support for check @const property definitions
- Deprecation warnings are now on by default with VERBOSE warnings
- Missing return warnings are now on by default with VERBOSE warnings
- Improved variable renaming algorithm
- Preliminary ECMASCRIPT5/ECMASCRIPT5_STRICT support (--language_in command line flag)
- Compile-time performance issue (Issue 349)
- More constants folding improvements
- Optimizations on the call graph are now performed in the main optimization loop
- goog.asserts are stripped by default, they can be enabled with the --debug option
- Improved unused code removal
- Other flag changes: --output_wrapper_marker support was removed, --flagfile support added
- New extern: jQuery 1.5, Google Maps API 3.4, Facebook JavaScript SDK, WebGL, IndexDB
- [Fixed issues 387, 384, 383, 381, 378, 375, 372, 369, 367, 366, 364, 363, 353, 349, 348, 325, 322, 321, 319, 318, 315, 301, 269, 266, 251, 249, 247, 204, 195, 133](http://code.google.com/p/closure-compiler/issues/list?can=1&q=closed-after%3A2011%2F1%2F19+closed-before%3A2011%2F3%2F22+status%3AFixed+)

### January 19, 2011
- whitespace-only support for es5 getters and setters
- New type syntax for structural constructors "{function(new:Type)}"
- Support for the @lends annotation.
- Add a @suppress {uselessCode} warnings group
- Improvements to constant-folding
- Native handling for goog.tweaks
- Emits an error if the left-hand side of an assign isn't an assignable expression
- removal of redundant returns and throws
- Optimize the "arguments" variable when possible.
- "toString" and "valueOf" are now officially assumed to be side-effect free.
- Add a --closure_entry_point flag, for use in conjunction with --manage_closure_dependencies
- Assorted type-checking fixes
- Fixes issues 311, 268, 267, 248, 261, 258, 187, 255, 236, 244, among others

### September 17, 2010
- Full support for goog.scope
- Better optimization of external calls that have no side effects (like getElementById)
- Much better unused var removal
- A number of peephole and constant-folding optimizations
- Much faster source map generation
- Better property detection for missingProperties check
- Much better type inference in local scopes
- type inference of return types on functions
- type checker warns about comparision of functions  to booleans, numbers, or strings
- Better externs file validation
- @suppress annotations work for all canonical warning groups
- @notypecheck annotation blocks more warnings
- General performance improvements
- Fixes issues 188, 186, 96, 177, 143, 221, 205, 200, 197, 182, 194, 172, 191, 71, 66, 229, among others

### June 16, 2010
- Beta support for goog.scope
- Smarter unreachable code analysis.
- Folds "new Error" to "Error", "new RegExp" to "RegExp", etc.
- Extract Prototype Member / Devirtualization improvements
- deterministic source maps
- Peephole optimizations
- Added @nocompile annotation to work with --manage_closure_dependencies
- Inline more functions into the global scope in advanced mode
- Better detection for dangerous 'this' references in verbose mode
- Disabled flow sensitive variable inlining by default, because it still has problems
- Fixes issues 174, 166, 168, 125 among others


### May 14, 2010
- Shadowing of the `arguments` variable is now forbidden
- Added the `--manage_closure_dependencies` flag (pending documentation)
- Support for the @extern annotation
- Type-inference plugin that knows about goog.asserts
- Data-flow based variable inlining
- Better function inlining
- Warnings for unknown @suppress parameters
- Fixes for [issue 141](https://github.com/google/closure-compiler/issues#issue/141), [issue 139](https://github.com/google/closure-compiler/issues#issue/139), [issue 58](https://github.com/google/closure-compiler/issues#issue/58), [issue 112](https://github.com/google/closure-compiler/issues#issue/112), and many others

### Mar 30, 2010
- Renamed `CompilerRunner.java` to `CommandLineRunner.java`
- More user-friendly messaging for trailing commas
- Improvements to inlining and property ambiguation optimizations
- Run-time type-checking (not available from the command-line)
- Better type checking in inner functions
- Fixes for [issue 33](https://github.com/google/closure-compiler/issues#issue/33), [issue 103](https://github.com/google/closure-compiler/issues#issue/103), [issue 116](https://github.com/google/closure-compiler/issues#issue/116), [issue 124](https://github.com/google/closure-compiler/issues#issue/124), [issue 127](https://github.com/google/closure-compiler/issues#issue/127), and [issue 130](https://github.com/google/closure-compiler/issues#issue/130) (among others)

### Feb 1, 2010
- Support for Ant (BuildingWithAnt)
- The ability to turn type warnings on/off independent of other flags (--jscomp_warning=checkTypes)
- With --warning_level=QUIET, all warnings will be silenced.
- Fix for Issue 86 ("@inheritDoc doesn't play well with interfaces")
- Fix for Issue 81 ("eval function replaced with eval operator")
- Fix for Issue 80 ("Inappropriate side-effect warning")
- A few improvements to variable inlining.
 

### Dec 17, 2009:
- Fix for [issue 75](https://github.com/google/closure-compiler/issues#issue/75) ("indexing into an array with a string shouldn't be an error")
- Fix for [issue 63](https://github.com/google/closure-compiler/issues#issue/63) ("create source map in whitespace-only mode.")
- Fix for [issue 24](https://github.com/google/closure-compiler/issues#issue/24) ("Add --charset option to command line compiler that changes the input and output chararacter set.")
- Don't generate warnings for ES5 directives
- Generate a warning for unsafe uses of "with".  Suppress warning with  /** @suppress {with} */
- Various bugs fixed.
  
### Dec 3, 2009:

- Several bug fixes.
- Make --define part of the open source API.
- Allow RemoveUnusedVars to strip unused anonymous function names.
- Add a warning for function declarations that may behave differently in different browsers.
- Enable local variable inlining for simple mode.
- Digits aren't allowed as the first character of a key, so add a prefix.

### November 19, 2009:

- Better dead assignment elimination
- Support for goog.base
- Allow $ in method names.
- Inline local functions and anonymous functions
- Fix some compiler crashes when folding ifs and handling local vars
- Better type inference in externs
- Don't emit warnings for JSDoc annotations we don't support.