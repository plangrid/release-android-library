release-android-library
=======================

Remote script to create a maven compatible release of an android library (aar). This release comes in a zip or exploded form and is only created locally inside your own build folder. You can these use these files to release to JCenter or Maven Central.

Matching blog post here: [http://blog.blundellapps.co.uk/locally-release-an-android-library-for-jcenter-or-maven-central-inclusion/](http://blog.blundellapps.co.uk/locally-release-an-android-library-for-jcenter-or-maven-central-inclusion/)

#### adding to your library
```
apply plugin: 'com.android.library'

ext {
    PUBLISH_GROUP_ID = 'com.blundell'
    PUBLISH_ARTIFACT_ID = 'example-library-name'
    PUBLISH_VERSION = '1.0.0'
}

android {
    // configs, flavors etc
}

dependencies {
    // dependencies
}

// Copy the file locally and use
apply from: 'android-release-aar.gradle'
// or use the remote copy to keep update with latest changes
apply from: 'https://raw.githubusercontent.com/plangrid/release-android-library/master/android-release-aar.gradle'
```


#### useage
The deploy script will read your Artifactory credentials from the env vars `ARTIFACTORY_USER` and `ARTIFACTORY_PASSWORD` and upload the library to the PG artifactory.

`./gradlew clean build uploadArchives`
