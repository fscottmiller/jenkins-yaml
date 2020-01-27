def getEnvironment(yaml) {
    if (yaml.keySet().toLowerCase().contains("environment")) {
        println "environment found"
        yaml["environment"].each {
            key, value -> println "${it.key}: ${it.value}"
        }
    }
}

node {
    def main = readYaml file: "main.yaml"
}