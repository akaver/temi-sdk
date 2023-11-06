Change gradle.properties - add '-SNAPSHOT' to the end of version name

~~~txt
VERSION_NAME=1.131.4-SNAPSHOT
~~~~

Release local artifact to ~/.m2 folder.

~~~bash
./gradlew clean sdk:publishToMavenLocal
~~~

End result should be published packages in
~~~txt
~/.m2/respository/com/robotemi/sdk/1.131.4-SNAPSHOT/
~~~


Add maven local support to your temi code, and switch package to snapshot version.
