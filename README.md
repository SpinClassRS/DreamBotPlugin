# DreamBotPlugin
## Initial IDE Setup
Download and install the Intellij IDEA and the Java 1.8 SDK, like you would when setting up a normal development environment

## Gradle Project Setup
* In IDEA, go to File -> New -> Project... and select Gradle from the side menu. Make sure the Project SDK is set to your Java 1.8 SDK and click Next
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/gradle_setup_1.png)
* Fill in the GroupId, ArtifactId and Version fields, click Next
    * More info about these can be found @ https://maven.apache.org/guides/mini/guide-naming-conventions.html
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/gradle_setup_2.png)
* Fill in a Project name and location, click Finish
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/gradle_setup_3.png)

* Open your project, click the 1:Project button the left hand side and open the build.gradle file
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/gradle_setup_4.png)
* Add the following to the very top of the build.gradle
    ```
    buildscript {
        repositories {
            maven {
                url "https://plugins.gradle.org/m2/"
            }
        }
        dependencies {
            classpath "gradle.plugin.com.spinclass:dreambot:1.1"
        }
    }
    ```
* Add `apply plugin: "com.spinclass.gradle.dreambot"` to the very bottom of build.gradle
* Click the Gradle button on the right hand side, click the refresh button and you should see dreambot listed under Tasks
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/developing_your_script_2.png)
* Run the updateDreambot task from the Gradle menu, on the right hand side
* Add `compileOnly files('./libs/dreambot-api.jar')` to the dependecies in build.gradle
* Your build.gradle should now look like this
![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/gradle_setup_final.png)

## Developing Your Script
* Add your GroupId + ArtifactId as a package to src/main/java and create your script class
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/developing_your_script_1.png)
* Add the ScriptManifest annotation to your class and extend AbstractScript
* Run the runDreambot task from the Gradle menu, on the right hand side
  ![alt text](https://github.com/SpinClassRS/DreamBotPlugin/blob/master/developing_your_script_3.png)
* DreamBot should open and you should now be able to select your script from Local Scripts
* Your script jar is also located in `builds/libs`, if you can't see it then run the buildScript task
