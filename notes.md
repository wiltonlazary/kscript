


## References

http://stackoverflow.com/questions/21814652/how-to-download-dependencies-in-gradle


```
apply plugin: 'java'

dependencies {
  runtime group: 'com.netflix.exhibitor', name: 'exhibitor-standalone', version: '1.5.2'
  runtime group: 'org.apache.zookeeper',  name: 'zookeeper', version: '3.4.6'
}

repositories { mavenCentral() }

task getDeps(type: Copy) {
  from sourceSets.main.runtimeClasspath
  into 'runtime/'
}
```
Download the dependencies (and their dependencies) into the folder runtime when you execute `gradle getDeps`.


https://github.com/andrewoma/kotlin-scripting-kickstarter

Kotlin natively supports scripting to a limited extent, so it is valid to use #! (shebang) directives at the top of kotlin source files.


## mvncp
https://github.com/andrewoma/kotlin-script/blob/master/extras/mvncp


https://github.com/andrewoma/kotlin-script

Installation
```bash
curl -s https://raw.githubusercontent.com/andrewoma/kotlin-script/master/extras/mvncp > ~/bin/mvncp && chmod u+x ~/bin/mvncp

```
Example
```
mvncp com.offbytwo:docopt:0.6.0.20150202  2> /dev/null
mvncp org.docopt:docopt:0.6.0-SNAPSHOT  2> /dev/null
```

## Official Docs

https://kotlinlang.org/docs/tutorials/command-line.html#using-the-command-line-to-run-scripts

kotlinc -script list_folders.kts


## Misc

for dependency resolution also consider
http://stackoverflow.com/questions/9407554/sbt-alternative-to-mvn-install-dskiptests

Create a sinlge jar containing all dependencies (to ease deployment for non-published dependencies)

## kotlinc shebang config

http://unix.stackexchange.com/questions/20880/how-can-i-use-environment-variables-in-my-shebang

Shebang lines do not undergo variable expansion, so you cannot use $FOO/MyCustomPython as it would search for an executable named dollar-F-O-O-...


http://www.unix.com/shell-programming-and-scripting/44511-environment-variables-shebangs.html


## Caching

http://stackoverflow.com/questions/12487424/uppercase-first-character-in-a-variable-with-bash
https://youtrack.jetbrains.com/issue/KT-10533

## Why not use env?
http://www.in-ulm.de/~mascheck/various/shebang/#interpreter-script

Most probably there isn't any Bell-Labs- or Berkeley-derived Unix that accepts the interpreter to be a script, which starts with #! again.
However, Linux since 2.6.27.9 2 and Minix accept this.

Also see https://en.wikipedia.org/wiki/Shebang_(Unix)#Portability

 Some systems, including Linux, do not split up the arguments;[10] for example, when running the script with the first line like,

Also see http://stackoverflow.com/questions/4303128/how-to-use-multiple-arguments-with-a-shebang-i-e


## directly run scripts with kotlinc

```
## directly run the script...
echo kotlinc -script -classpath "$classpath" "$@"

```

## how does process substitution work?

http://unix.stackexchange.com/questions/156084/why-does-process-substitution-result-in-a-file-called-dev-fd-63-which-is-a-pipe