pipeline {
    agent any

    stages {
        stage('Read and Iterate JSON') {
            steps {
                script {
                    // Define the path to your JSON file (should be in your repository)
                    def jsonFile = 'data.json'
                    
                    // Check if the file exists
                    if (!fileExists(jsonFile)) {
                        error "JSON file not found: ${jsonFile}"
                    }
                    
                    // Read and parse the JSON content from the file
                    def jsonArray = readJSON file: jsonFile
                    
                    // Iterate through the JSON array and print each object's values
                    jsonArray.each { obj ->
                        echo "----------------------------"
                        echo "Name: ${obj.name}"
                        echo "Age: ${obj.age}"
                        echo "Skills: ${obj.skills.join(', ')}"
                        echo "City: ${obj.location.city}"
                        echo "State: ${obj.location.state}"
                    }
                    echo "----------------------------"
                }
            }
        }
    }
}
