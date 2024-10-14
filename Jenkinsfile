pipeline {
    agent any
    parameters {
        text (name: 'DEPLOY_ENV', description: 'Введите переменные окружения в формате ключ=значение')
    }
    stages {
        stage('Set Environment Variables') {
            steps {
                script {
                    // Разбираем переменные из DEPLOY_ENV на пары ключ-значение
                    def envVars = DEPLOY_ENV.split('\n').collectEntries { line ->
                        def parts = line.split('=')
                        [(parts[0]): parts[1]]
                    }

                    // Устанавливаем их как переменные окружения
                    envVars.each { key, value ->
                        env[key] = value
                        echo "Set environment variable: ${key} = ${value}"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Пример использования переменных
                    echo "Using environment variable pass: ${env.pass}"
                    sh 'printenv | grep pass'
                }
            }
        }
    }
}
