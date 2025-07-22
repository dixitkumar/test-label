pipeline {
    agent any
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!'
            }
        }
    }
    
    post { 
        always { 
            echo 'I will always say Hello again!'
            	 if (sh(script: 'find -path "./build_version.properties" | egrep . > /dev/null', returnStatus: true) == 0) {
                        	def props = new Properties()
							def file = new File('./target/runtime/conf/build_version.properties')
							file.withInputStream { stream ->
							    props.load(stream)
							}
							sicsBuildNo = props.getProperty('build')
							println "SicsBuildNo: $sicsBuildNo"
                    }
        }
    }
}
