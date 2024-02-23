pipeline {
    agent any
    stages {
        stage('Erstellung der ersten Datei') {
            steps{
                script {
                    echo 'Die erste datei wird erstellt'
                    writeFile file: 'dokument1.txt', text: 'Hier ist die erste Datei'
                    echo 'Der Inhalt der ersten Datei'
                    cat dokument1.txt
                }
            }
        }
        stage('Erstellung der zweiten Datei') {
            steps{
                script {
                    echo 'Die zweite datei wird erstellt'
                    writeFile file: 'dokument2.txt', text: 'Hier ist die zweite Datei'
                    echo 'Der Inhalt der zweiten Datei'
                    cat dokument2.txt
                }
            }
        }
    }
}