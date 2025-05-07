pipeline {
    agent any
    environment {
        WAR_FILE = "mywebapp.war"
        TOMCAT_HOME = "D:\DevopsTaining\All softwares\apache-tomcat-9.0.104\apache-tomcat-9.0.104\bin"
    }
    stages {
        stage('Checkout Code') {
            steps {
                url: 'https://github.com/Narasimha191031018/mywebapp.git'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                bat """
                echo Deploying WAR file...
                copy %WAR_FILE% "%TOMCAT_HOME%\\webapps\\" /Y
                """
            }
        }
        stage('Restart Tomcat') {
            steps {
                bat """
                echo Restarting Tomcat...
                "%TOMCAT_HOME%\\bin\\shutdown.bat"
                timeout /t 5
                "%TOMCAT_HOME%\\bin\\startup.bat"
                """
            }
        }
    }
}
