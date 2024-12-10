pipeline {
    agent any
    environment {
        JMETER_HOME = "/caminhojmeter" // Ajuste para o caminho do JMeter no Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Setup Environment') {
            steps {
                script {
                    echo "Instalando dependências e configurando o ambiente..."
                }
            }
        }
        
        stage('Run Load Test') {
            steps {
                sh "${JMETER_HOME}/bin/jmeter -n -t test-plans/load-test.jmx -l reports/load-test-results.jtl -e -o reports/load-test-report"
            }
        }
        
        stage('Publish Reports') {
            steps {
                archiveArtifacts artifacts: 'reports/**/*', allowEmptyArchive: true
            }
        }
    }
    post {
        always {
            echo "Pipeline concluído."
        }
        success {
            echo "Testes executados com sucesso."
        }
        failure {
            echo "Falha durante a execução dos testes."
        }
    }
}