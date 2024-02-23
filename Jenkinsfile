pipeline {
    agent any
    triggers {
        cron('H/6 * * * *')
    }
    stages {
        stage('Erstellung der ersten Datei') {
            steps{
                script {
                    echo 'Die erste datei wird erstellt'
                    writeFile file: 'dokument1.txt', text: 'Hier ist die erste Datei'
                    echo 'Der Inhalt der ersten Datei'
                    sh 'cat dokument1.txt'
                }
            }
        }
        stage('Erstellung der zweiten Datei') {
            steps{
                script {
                    echo 'Die zweite datei wird erstellt'
                    writeFile file: 'dokument2.txt', text: 'Hier ist die zweite Datei'
                    echo 'Der Inhalt der zweiten Datei'
                    sh 'cat dokument2.txt'
                }
            }
        }
        stage('Hinzufügen von zusätzlichen Texten'){
            steps {
                script {
                    sh 'echo -n "Zusätzlicher Inhalt zu der ersten Dokument ${BUILD_NUMBER}" >> dokument1.txt'
                    sh 'echo -n "Zusätzlicher Inhalt zu der zweiten Dokument ${BUILD_NUMBER}" >> dokument2.txt'
                    echo 'Die Texte weurden hinzugefügt'
                }
            }
        }
    }
    post {
        always {
            archiveArtifacts 'dokument1.txt, dokument2.txt'
        }
    }
}