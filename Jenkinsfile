pipeline {
    agent any
    tools {
        maven 'Maven_3.8.6'   // Replace with your Maven tool name
        jdk 'JDK_17'          // Replace with your JDK tool name
    }
    environment {
        WAR_FILE = "target/mywebapp.war"
        TOMCAT_HOME = "D:/DevopsTaining/All softwares/apache-tomcat-9.0.104/apache-tomcat-9.0.104"
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Narasimha191031018/mywebapp.git'
            }
        }
        stage('Build WAR') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                bat """
                    echo Deploying WAR file...
                    copy "%WAR_FILE%" "%TOMCAT_HOME%\\webapps\\" /Y
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
