node {
    // it will give the maven location
    def mvnHome = tool name: 'maven3', type: 'maven'
    stage ('SCM checkout'){
        git credentialsId: 'git-1',
        url: 'https://github.com/pranatgit/jenkins-pranat-javahomes',
        branch: 'master'
    }
    stage ('Maven Build'){
        sh label: '', script: "${mvnHome}/bin/mvn clean package"
    }
}
