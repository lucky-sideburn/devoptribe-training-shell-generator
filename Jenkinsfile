pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
    }
    stages {
        def remote = [:]
        remote.name = '10.10.10.7'
        remote.host = '10.10.10.7'
        remote.user = 'jenkins'
        remote.password = credentials('jenkins-ssh-pass')
        remote.allowAnyHosts = true
        stage('Shell Generator') {
            steps {
                sshCommand remote: remote, command: "ls -lrt"
                sshCommand remote: remote, command: "for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done"
            }
        }
    }
}
