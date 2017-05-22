echo "Empezando mi workflow"

stage 'build'
node {

    echo "Download do Projeto do GIT"
    git 'https://github.com/Supertchuco/otto-rest.git'

    echo "Buildando"
	sh 'chmod +x gradlew'
    sh './gradlew build -x test'

    archive 'build/libs/*.jar'

}



stage 'Build Image'
node {
    sh './dockerBuild -t'
}