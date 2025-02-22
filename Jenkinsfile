pipeline {
    agent any

    stages {
        stage('Read and Iterate JSON') {
            steps {
                script {
                    // Define the JSON file path (must be present in your repo)
                    def jsonFile = 'data.json'
                    
                    // Verify the file exists
                    if (!fileExists(jsonFile)) {
                        error "JSON file not found: ${jsonFile}"
                    }
                    
                    // Read and parse the JSON content using the built-in readJSON step
                    def jsonArray = readJSON file: jsonFile
                    
                    // Iterate over the JSON array
                    jsonArray.each { obj ->
                        echo "----------------------------"
                        echo "Name: ${obj.name}"
                        echo "Age: ${obj.age}"
                        
                        // Convert the 'skills' JSONArray to a Groovy list
                        def skillsList = []
                        obj.skills.each { skill ->
                            skillsList.add(skill)
                        }
                        echo "Skills: ${skillsList.join(', ')}"
                        
                        echo "City: ${obj.location.city}"
                        echo "State: ${obj.location.state}"
                    }
                    echo "----------------------------"
                }
            }
        }
    }
}
