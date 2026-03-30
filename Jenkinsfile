pipeline {
    // Indique que le script peut tourner sur n'importe quel "agent" (ta VM)
    agent any

    stages {
        // Étape 1 : Récupération du code depuis Git
        stage('Préparation') {
            steps {
                echo 'Récupération du code source...'
                checkout scm
            }
        }

        // Étape 2 : Sécurité (C'est ici que ton exercice devient "DevSecOps")
        stage('Scan de Sécurité') {
            steps {
                echo 'Recherche de secrets avec Gitleaks...'
                // On utilise "sh" pour lancer une commande système sur la VM
                // Le "|| true" permet de voir les erreurs sans bloquer la suite si tu veux juste tester
                sh 'gitleaks detect --source . --verbose || echo "Secrets trouvés !"'
            }
        }

        // Étape 3 : Simulation de Build ou Test
        stage('Vérification du Code') {
            steps {
                echo 'Analyse syntaxique en cours...'
                sh 'ls -R' // Liste les fichiers pour prouver que Jenkins voit ton repo
            }
        }
    }

    // Bloc optionnel pour envoyer un message à la fin
    post {
        always {
            echo 'Fin du pipeline DevSecOps.'
        }
    }
}
