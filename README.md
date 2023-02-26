# Cookiecutter for Java + Gradle

A cookiecutter template for modern Gradle (v8) builds of Java, with basic GitHub Actions for build-test.

## Install and use

Install `cookiecutter` and then run 
```bash
cookiecutter https://github.com/maciejskorski/cookiecutter-java-gradle`
```

Add the `build-test` task to GitHub Actions by adapting the following code
```yaml
# .github/workflows/build_test.yaml
name: Java Simple CI

on:
  push:

jobs:
  build-test-project:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout sources
      uses: actions/checkout@v3
    - name: Set up JDK 19
      uses: actions/setup-java@v3
      with:
        java-version: '19'
        distribution: temurin
    - name: Setup and execute Gradle
      uses: gradle/gradle-build-action@v2
      with:
        gradle-version: current
        arguments: |
          check
          build
          test
          --info
        build-root-directory: {{your_app_name}}
```



## References

1. [Gradle project](https://gradle.org/install/)
2. [Gradle GitHub Action](https://github.com/marketplace/actions/gradle-build-action)
3. [Older cookiecutter by @m-x-k](https://github.com/m-x-k/cookiecutter-java)
