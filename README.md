# php7-support
CLI tool to check for PHP7 support in your installed libraries based on your composer.json.

## Motivation
This tool aims to make it easier to incrementally upgrade a project's dependencies, by reporting
php7 support based on the libs' CI settings, until the whole project can be switched over to php7.

## Notes / Assumptions
- The lib supports php7 if it's tested with it (Confirm by reading travis.yml for example)
- If php7 support can be decided based on the master branch, then it'll be reported as supported.
(Later it could find out the latest stable version instead of using master.)
First implementation could assume travis and github only. Later other CI providers and VCRs could be supported,
like circle ci and gitlabs.

## Todo
- Loop through the installed packages in composer.lock
- For each package, check for php 7 support for both the currently installed version and the one in master
(By checking travis.yml for example)
- Also report the required php version from the composer.lock file
- Compare all the ci-tested php version against the project's required version. 
- Show separate sections: 1) which packages support php 7 already 2) which can be upgraded (And if they're supporting the project's required php version too, at the same time) 3) which cannot be upgraded, because the project doesn't explicitly states php7 support
