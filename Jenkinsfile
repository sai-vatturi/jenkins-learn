pipeline {
    agent any  // Runs on any available agent

    stages {
        stage('Read and Iterate JSON') {
            steps {
                script {
                    // Import JsonSlurper
                    import groovy.json.JsonSlurper

                    // Ensure the file exists
                    def jsonFile = 'data.json'
                    if (!fileExists(jsonFile)) {
                        error "JSON file not found: ${jsonFile}"
                    }

                    // Read and parse the JSON content
                    def jsonText = readFile(jsonFile)
                    def jsonArray = new JsonSlurper().parseText(jsonText)

                    // Iterate through the array and print values
                    jsonArray.each { obj ->
                        echo "----------------------------"
                        echo "Name: ${obj.name}"
                        echo "Age: ${obj.age}"
                        echo "Skills: ${obj.skills?.join(', ')}"  // Ensure skills exist before joining
                        echo "City: ${obj.location?.city}"  // Safe navigation to prevent null issues
                        echo "State: ${obj.location?.state}"
                    }
                    echo "----------------------------"
                }
            }
        }
    }
}
