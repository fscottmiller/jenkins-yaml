def getEnvironment(yaml) {
    if (yaml.keySet().contains("environment")) {
        println "environment found"
        yaml["environment"].each {
            key, value -> println "${key}: ${value}"
        }
    }
}

def getParameters(yaml) {
    if (yaml.keySet().contains("parameters")) {
        println "parameters found"
        yaml['parameters'].each {
            key, value -> println "${key}: ${value}"
        }
    }
}

node {
    checkout scm
    def main = readYaml file: "main.yaml"
    getEnvironment main
    getParameters main    
}