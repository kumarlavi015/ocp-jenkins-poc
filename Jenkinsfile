retriever: modernSCM(
  [
    $class: "GitSCMSource",
    remote: "https://github.com/lavi2088/openshift-jenkins.git"
  ]
)

// The name you want to give your Spring Boot application
// Each resource related to your app will be given this name
appName = "openshift-jenkins"

pipeline {
    // Use the 'maven' Jenkins agent image which is provided with OpenShift 
    //agent { label }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Docker Build") {
            steps {
                // This uploads your application's source code and performs a binary build in OpenShift
                // This is a step defined in the shared library (see the top for the URL)
                // (Or you could invoke this step using 'oc' commands!)
                binaryBuild(buildConfigName: appName, buildFromPath: ".")
            }
        }

        // You could extend the pipeline by tagging the image,
        // or deploying it to a production environment, etc......
    }
}
