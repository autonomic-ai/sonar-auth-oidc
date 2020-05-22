
## Perform release

```
cd sonar-auth-oidc
./mvnw clean install
./mvnw release:prepare
./mvnw release:perform
```

### AU Release

1. In the repo directory, run the following command:

    ```bash
    ./mvnw clean install
    ```

1. Navigate to [Releases page][releases] of the forked repo
1. Create a new release and upload the jar from the `targets` subdirectory
1. Update the [au-docker-sonarqube/Dockerfile][sonar_dockerfile] in accordance with the release to ensure the [version][sonar_version] and [path][sonar_path] are correct


## Update SonarCloud project

```
git checkout <release tag>
./mvnw clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=vaulttec -Dsonar.login=<security token>

```


## Deploy to Marketplace

1. create a PR on the [sonar-update-center-properties repo](https://github.com/SonarSource/sonar-update-center-properties)
1. start a new topic on the [Community Forum](https://community.sonarsource.com/c/plugins) as described in [Deploying to the Marketplace](https://docs.sonarqube.org/latest/extend/deploying-to-marketplace/)

[releases]: https://github.com/autonomic-ai/sonar-auth-oidc/releases
[sonar_dockerfile]: https://github.com/autonomic-ai/au-docker-sonarqube/blob/rc/Dockerfile
[sonar_version]: https://github.com/autonomic-ai/au-docker-sonarqube/blob/rc/Dockerfile#L14
[sonar_path]: https://github.com/autonomic-ai/au-docker-sonarqube/blob/rc/Dockerfile#L60