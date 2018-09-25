def rootDir = "bobcat"

properties(
        [
                buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '10')),
                disableConcurrentBuilds()
        ]
)

node {
    stage('Checkout Asset Share Commons'){
        git branch: "master", url: 'ssh://git@bitbucket.cognifide.com/~daniel.madejek/bobcattest.git'

    }

    stage('Run Tests'){
        sh "./gradlew clean test -Dbobcat.config.contexts=chrome"
        archiveArtifacts "/build/reports/allure-report/**/*.*"
    }

}