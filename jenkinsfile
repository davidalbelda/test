pipeline {
    agent any

    stages {
        stage('Copy Files') {
            steps {
                script {
                    // Define source and destination paths
                    def sourcePath = 'C:\\nikos\\Proxies\\'
                    def destPath = 'C:\\nikos\\'

                    // Get selected files from parameters
                    def selectedFiles = params.FILES

                    // Debug: Print out the selected files
                    echo "Selected files (raw): ${selectedFiles}"

                    // Ensure selectedFiles is a list, split by comma if necessary
                    if (selectedFiles instanceof String) {
                        selectedFiles = selectedFiles.split(',')
                    }

                    // Debug: Print out the selected files after splitting
                    echo "Selected files (interpreted as list): ${selectedFiles}"

                    // Check if selectedFiles is not null and not empty
                    if (selectedFiles && selectedFiles.size() > 0) {
                        // Iterate through each selected file and copy it
                        selectedFiles.each { file ->
                            // Debug: Print each file name
                            echo "Processing file: ${file}"

                            // Copy the file from source to destination
                            bat "copy ${sourcePath}${file} ${destPath}"
                        }
                    } else {
                        echo "No files selected."
                    }
                }
            }
        }
    }
}
