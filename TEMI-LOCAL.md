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
Enable maven local in settings.gradle.kts (add mavenLocal() before maven central)

~~~kotlin
pluginManagement {
    repositories {
        google()
        mavenLocal()
        mavenCentral()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenLocal()
        mavenCentral()
    }
}
~~~

In build.gradle.kts
~~~kotlin
// uses local .m2 respository and snapshot version of sdk - enabvles testing on emulator
implementation("com.robotemi:sdk:1.131.4-SNAPSHOT")
~~~

