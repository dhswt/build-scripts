# Build Scripts > Gradle

## Gitea Maven Repo

```gradle
// configure ids
buildscript {
    ext {
        giteaUrl = System.getenv("GITEA_URL") ?: "https://gitea.dhswt.de"
        giteaRepoNamespace = System.getenv("CI_REPOSITORY_NAMESPACE") ?: "TODO add project id for building outside CI here"
    }
}

// add script
apply from: 'https://gitea.dhswt.de/actions/build-scripts/raw/branch/master/gradle/GiteaMavenRepo.gradle'

// configure a gitea namespace as repository
project {
    repositories {
        mavenCentral()
        mavenLocal()
        // addGiteaRepository(it, giteaUrl, "<namespace>")
    }
}

// publish to gitea
publishing {
    repositories {
        addGiteaPublishingRepository(it, giteaUrl, giteaRepoNamespace)
    }
    publications {
        maven(MavenPublication) {
            from components.java
        }
    }
}
```
