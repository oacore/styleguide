# CORE styleguide

## Overview of projects

- [`CHARS core harvesting system`](https://bitbucket.org/kmi-ou/chars-core-harvesting-system/) : SpringBoot The CORE Harvesting system
- [`core-frontend`](https://bitbucket.org/kmi-ou/core-front-end): Symfony app for the backend to the frontend (crazy right?)
- [`core-fileserver`](https://bitbucket.org/kmi-ou/core-similarities): Symfony app for serving the file and using the file server
- [`repository-dashboard`](https://bitbucket.org/kmi-ou/repository-dashboard) : Symfony app dedicated to the dashboard
- [`configurations`](https://bitbucket.org/kmi-ou/configurations): the properties of the web servers and the app servers
- [`resync-gen-api`](https://bitbucket.org/kmi-ou/resync-gen-api): the generator for the CORE Fastsync sitemaps
- [`spark-core`](https://bitbucket.org/kmi-ou/spark-core): code related to MUCC (Microsoft, Unpaywall, Crossref, CORE)
- [`next`](https://github.com/oacore/next) the frontend, it includes all the static pages and the styles of https://core.ac.uk

## How we manage the projects: Git Flow
![Git flow](https://wac-cdn.atlassian.com/dam/jcr:b5259cce-6245-49f2-b89b-9871f9ee3fa4/03%20(2).svg?cdnVersion=515)
[From the workflow explained by Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
> As CHARS is in constant evolvement we are using develop as the branch where we run the workers. For all the other projects please use GitFlow unless otherwise stated.
## Naming Style
### Workers
Use this structure:
```
object_action[ _item| ]
```
Examples: `document_download`, `text_extract_item`

### Components (libraries and modules that are not workers)
The name needs to be short and define what is the component about, if you are not able to define what the component does or represents in one single word probably you will need two components.

### Variable names
This apply for Java, variable names should always be understandable. Better have a long variable name than a short one. Single letter or short variables are wrong in general, as make the code difficult to read. If you name a variable with a short name you need to have a very good reason for it.

### Method names, class names
The name should say what it does or represents, again long is better than short. Names like `Executor` or `do()` should be avoided as are unclear on what is happening inside that.

## Code Style
We try to follow standards as much as we can, if you are deciding between a standard and a not standard way always go for the standard way.

### PHP
Symfony 4+ projects should follow the [Symfony Coding Standards](https://symfony.com/doc/current/contributing/code/standards.html). You may use [php-cs-fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) to automatically correct this along with [IDE plugins](https://github.com/FriendsOfPHP/PHP-CS-Fixer#helpers).

You must run php-cs-fixer before committing. Avoid mixing a code change and a whole-file code format in the same commit. These should be made separately for easier code review.

### Python
For our code in Python you should follow the [PEP8 specifications](https://www.python.org/dev/peps/pep-0008/), if possible integrating a linter that check for this or using an IDE that enforce it is strongly recommended.

### Format your code
Always, no exceptions, ever.
### POJOs
All the parameters need getters and setters and a `toString()`

### Wrap your `if`s `while`s etc.
All the iterator items should be wrapped with `{}`. One-line iterations are difficult to read and makes the code more error prone.

### Dates in Java
As we now moved to Java8 please use all the different date entity accordingly. `Instant` for timestamp, `Duration` for duration, `LocalDate` for date, `LocalDateTime` for date-time. 


### Exceptions
Always log your exceptions, unless your exception is handled properly in the code. Avoid to mute exceptions even if they will "never happen" as they add blind spot for maintaing the code.
In Java, please avoid to use `printStacktrace()` and use `logger.error`. In general we want to be careful with exception handling we don't want to hide them but we also want to manage them properly. [This is a good reference on what to do with exceptions.](http://wiki.c2.com/?DontCatchExceptions)

