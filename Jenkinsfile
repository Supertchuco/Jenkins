echo "Empezando mi workflow"

stage 'build'
node {

    echo "Download do Projeto do GIT"
    git 'https://github.com/Supertchuco/otto-rest.git'

    echo "Buildando"
    sh './gradlew build -x test'

    archive 'build/libs/*.jar'

}

stage 'test'
node {
    sh './gradlew clean test'

    step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/TEST-*.xml'])
}