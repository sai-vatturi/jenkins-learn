pipeline {
    agent any

    stages {
        stage('Read and Iterate JSON') {
            steps {
                script {
                    // Define a helper function for parsing JSON that is not subject to CPS serialization.
                    @NonCPS
                    def parseJson(String jsonText) {
                        return new groovy.json.JsonSlurper().parseText(jsonText)
                    }

                    // Ensure the JSON file exists
                    def jsonFile = 'data.json'
                    if (!fileExists(jsonFile)) {
                        error "JSON file not found: ${jsonFile}"
                    }

                    // Read and parse the JSON content using the helper method
                    def jsonText = readFile(jsonFile)
                    def jsonArray = parseJson(jsonText)

                    // Iterate through the array and print each object's values
                    jsonArray.each { obj ->
                        echo "----------------------------"
                        echo "Name: ${obj.name}"
                        echo "Age: ${obj.age}"
                        echo "Skills: ${obj.skills?.join(', ')}"
                        echo "City: ${obj.location?.city}"
                        echo "State: ${obj.location?.state}"
                    }
                    echo "----------------------------"
                }
            }
        }
    }
}
