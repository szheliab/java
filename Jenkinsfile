node ("master") {
    stage('Git-Checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '16e11b20-c722-4add-acc1-60fca7777f6e', url: 'https://github.com/tamamshud/java']]])
    }
}
