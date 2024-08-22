pipeline{
    agent any
    stages{
        stage('GIT clone repo'){
            steps {
               //clone repo
				git branch: 'main', url: 'https://github.com/faldesaivishvaja/maven_project.git'
                }
		}
		stage('Build maven project'){
		    steps{
			    	bat 'cd musicstore'
				bat 'mvn -Dmaven.test.failure.ignore=true clean package'
		    }
		}
		stage('Building tomcat image with generated war file using Dockerfile'){
		    steps{
				bat 'docker build -t vishvajafaldesai/musicstore .'
		    }
		}
		stage('Running tomcat container'){
		    steps{
				bat 'docker run --name musicstore -p 3050:8080 vishvajafaldesai/musicstore'
		    }
		}
    }
}
