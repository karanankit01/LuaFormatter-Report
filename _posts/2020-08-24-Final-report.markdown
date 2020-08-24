---
layout: post
title:  " Final Work Submission Report  Project Summary [In Progress]"
date:   2020-08-24 16:57:51
---

## Overview

### What is LuaFormatter ?
LuaFormatter is a code formatter for Lua scripts inspired by clang-format. It also integrates easily in various code editors.  

### Project Idea
Formatter style the lua scripts according to the configuration value set to it. But before this project LuaFormatter doesn't check if the configuration values make sense before using it i.e, validation of configuration values. Some configuration with validation error:  
 * Domain validation  
   * **`column_limit : -5 `** , **`indent_width : -2`**
 * Conflict Validation  
   * **`single_quote_to_double_quote : true`** and **` double_quote_to_single_quote : true`**

So the project was aimed at the following:
 * Building the Validators for each of the configuration fields.
 * Implement feature to add configuration field value through command line flags.
 * Enhancement of configuration field with more features and solve existing bugs.

Initially, the Formatter workflow was simple as:
<img src="{{ site.baseurl }}/assets/img/Before_project.png">

## Project Implementation
The project started with fixing the existing issues and implemented some enhancement features in it.The project was completed in three phases:  
### Phase1
This phase starts with adding test case for **space_before_call** feature. It was later followed by adding the **column_table_limit** feature in the configuration. This feature helps the user to set the column limit of the table independently of **column_limit** config value. If user will not provide the value of column_table_limit then the formatter automatically sets the column_table_limit value as same as column_limit. The test case and documentation is added along with this feature. Also, **align_parameter** feature was fixed in this phase.  

### Phase2
The codebase workflow (HACKING.md) of the project was initiated in this phase. This is the working documentation of the program. In continuation with HACKING.md the feature implementation of configuration setting through command line flags is started. In this feature the user can set the configuration value of each field through command line flags. Also the Unit-test and documentation for the feature is added.  

    ./lua-format file.lua --column-limit 20 --use-tab --no-align-parameter --tab-width 4 --extra-sep-at-table-end --table-sep ; --keep-simple-function-one-line

*Configuration through command line flags*

### Phase3
Now the validators for the configuration fields are implemented. Values of each configuration fields are passed through their corresponding validators. In case of error in the configuration values the validators throw the error and the program gets terminated. Validators are implemented for domain error, logic error and conflicting error with the value of other configuration field. At last workflow of all the implemented features was updated in HACKING.md  


Finally, after completion of the project the workflow of the Formatter is:
<img src="{{ site.baseurl }}/assets/img/After_project.png">

## Technologies involved
The technologies which I learned and used in the project are given below:
 * Used Args parser and group validator to set configuration flags.
 * **Std::map** are used to store the configuration value from command line flags and validators of configuration field.
 * Used **`std::any`** for storing values of every configuration field in a single map which later processed by **`std::any_cast`**.
 * Used lambda function to implement the validator.
 * Used generic programming to keep the project in standard layout.
 * Implemented unit-test for various features.
 * Get knowledge about various **`git commands`** and used it for maintaining the PRs and git log.

## My Code Contributions
The following PRs include the work for the above-mentioned highlights and also other miscellaneous works and bug fixes during the GSoC period.
### Merged PRs
 * [#93 : Fixed Compilation and Typo error ](https://github.com/Koihik/LuaFormatter/pull/93)
 * [#105 : Test case for space_before_call feature ](https://github.com/Koihik/LuaFormatter/pull/105)
 * [#106 : Fixed issue#98 Added Column_table_limit feature ](https://github.com/Koihik/LuaFormatter/pull/106)
 * [#108 : Fixed Bug of align_parameter for false ](https://github.com/Koihik/LuaFormatter/pull/108)
 * [#113 : Implemented configuration flags via commandline](https://github.com/Koihik/LuaFormatter/pull/113)
 * [#117 : Documentation for configuration setting through commandline](https://github.com/Koihik/LuaFormatter/pull/117)
 * [#118 : Added unit-test for command line feature](https://github.com/Koihik/LuaFormatter/pull/118)
 * [#124 : Implemented Integral lazy configuration validator](https://github.com/Koihik/LuaFormatter/pull/124)
 * [#130 : Implemented Conflicting validators with test cases](https://github.com/Koihik/LuaFormatter/pull/130)

### Open PRs
 * [#111 : Added HACKING.md - codebase workflow](https://github.com/Koihik/LuaFormatter/pull/111)

### Closed PRs
 * [#107 : Test case for fix continuation](https://github.com/Koihik/LuaFormatter/pull/107)
### All PRs : [LuaFormatter](https://github.com/Koihik/LuaFormatter/pulls?q=is%3Apr+author%3Akaranankit01)

## Further Work (After GSoC)
The GSoC Project is completed successfully and all the features are ready to use by the users. After this I have some plan which can be implemented after Google Summer of Code.
 * Some more fields will be added in the configuration for formatting.
 * Existing bugs will be resolved.
 * Enhancement of some existing features like chop_down_parameter will be done.
 * Continue to work on the project along with fixing issues and helping other developers and users.


## Acknowledgments
I would like to thank my mentor for his continuous guidance throughout the summer and giving me the best experience of my life. The motivation and guidance I got from him will definitely help me in the days to come.  

Time flew and brought us close to the end. However, the best things deserve to be a special part of our life and LabLua had already made its place in my heart long back. Loads of 💖 to my LabLua family.  

We will keep improving the user as well as developer experience in the coming days. Cheers to a new beginning.✌
