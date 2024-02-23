pipeline {
    agent any
    // periodischer Auslöser
    triggers {
        cron('H/6 * * * *')
    }
    // Dekleration von Stages
    stages {
        // Stage für die Erstellunder der ersten Datei
        stage('Erstellung der ersten Datei') {
            steps{
                script {
                    echo 'Die erste datei wird erstellt' // Ausgabe für die Aufgabe
                    writeFile file: 'dokument1.txt', text: 'Hier ist die erste Datei' //Erstellt eine Datei mit dem Namen "dokument1.txt und füght den Text hinzu"
                    echo 'Der Inhalt der ersten Datei'  // Ausgabe für die Afugabe
                    sh 'cat dokument1.txt' // Ausgabe des Inhaltes von der Datei
                }
            }
        }
        // Stage für die Erstellung der zweiten Datei
        stage('Erstellung der zweiten Datei') {
            steps{
                script {
                    echo 'Die zweite datei wird erstellt' // Ausgabe für die Aufgabe
                    writeFile file: 'dokument2.txt', text: 'Hier ist die zweite Datei' //Erstellt eine Datei mit dem Namen "dokument1.txt und füght den Text hinzu"
                    echo 'Der Inhalt der zweiten Datei' // Ausgabe für die Afugabe
                    sh 'cat dokument2.txt' // Ausgabe des Inhaltes von der Datei
                }
            }
        }
        // Stage, um Texze hinzuzufügem
        stage('Hinzufügen von zusätzlichen Texten'){
            steps {
                script {
                    // Hinzufügt des fongenden Text zur Datei. Damit eine neue Text erstellt wird, wird ein Environment Variable hinzugefügt. 
                    // Durch die Environment Variable aendert sich der zu hinzufügende Text jedes mal. so werden Fehler verhindert.
                    sh 'echo -n "Zusätzlicher Inhalt zu der ersten Dokument ${BUILD_NUMBER}" >> dokument1.txt'
                    sh 'echo -n "Zusätzlicher Inhalt zu der zweiten Dokument ${BUILD_NUMBER}" >> dokument2.txt'
                    echo 'Die Texte weurden hinzugefügt'
                }
            }
        }
    }
    // Post zum Speichern von Dateien
    post {
        always {
            archiveArtifacts 'dokument1.txt, dokument2.txt' // Speicher die Dateien mit definierten Namen. 
            // speichert nur die letzten Versionen. 
        }
    }
}