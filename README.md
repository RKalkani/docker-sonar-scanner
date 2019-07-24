docker-sonar-scanner
====================

[![pulls][docker hub svg]][docker hub]

The docker image with sonar scanner 4.0.0 binary to analyze your project.

Using it in your gitlab projects
----------------------------------

Create a `sonar-project.properties` file on root of your project:

Checkout documentation for available analysing parameter options: <https://docs.sonarqube.org/7.9/analysis/analysis-parameters/>

~~~conf
sonar.projectKey=your-project-key
sonar.exclusions=node_modules/**,coverage/**

sonar.sources=.

sonar.gitlab.project_id=git@your-git-repo.git
~~~

Add the next stage to your `.gitlab-ci.yml`.

~~~yaml
stages:
- analysis

sonarqube:
  stage: analysis
  image: rkalkani/sonar-scanner
  script:
  - sonar-scanner
~~~

Defining custom sonar-scanner options
----------------------------------

You can pass any additional option to the `sonar-scanner` binnary, if needed:

~~~yaml
sonarqube:
  stage: analysis
  image: rkalkani/sonar-scanner
  script:
  - sonar-scanner -Dsonar.custom.param=whatever -Dsonar.custom.param2=whichever
~~~

[docker hub]: https://hub.docker.com/r/rkalkani/sonar-scanner
[LICENSE]: ./LICENSE
[docker hub svg]: https://img.shields.io/docker/pulls/rkalkani/sonar-scanner.svg
