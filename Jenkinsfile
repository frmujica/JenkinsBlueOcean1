pipeline {
  agent any
  stages {
    stage('Hello') {
      environment {
        DEPLOY_TO = 'production'
        MY_CRED = credentials('MY_SECRET')
      }
      steps {
        echo 'Hello World: ${params.NAME}'
        echo 'Variable de entorno local [DEPLOY_TO]: ${DEPLOY_TO}'
        script {
          def nombre = '${params.NAME}'
          def color = '${param.colores}'

          echo "Valor variable de entorno [MIVAR_ENTORNO]: ${MIVAR_ENTORNO}"

          if ( nombre == 'Fran'){
            echo 'en nombre es ${params.NAME}'
          } else {
            echo 'El nombre NO es el que esperaba'
          }

          if ( color == 'negro'){
            echo 'Muy oscuro'
          } else {
            echo 'Muy claro'
          }

          for (int i = 0; i < 10; ++i) {
            echo "linea numero: ${i}"
          }
        }

      }
    }

    stage('Hello2') {
      when {
        expression {
          '${params.colores}' == 'blanco'
        }

      }
      steps {
        echo 'BLANCO!!!!!!!!!!!'
      }
    }

  }
  environment {
    Name = 'Nombre'
  }
  parameters {
    string(name: 'Name', description: 'Nombre')
    choice(name: 'colores', choices: ['blanco', 'negro'], description: 'Elige un color')
  }
}