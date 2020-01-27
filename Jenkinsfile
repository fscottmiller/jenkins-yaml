def getEnvironment(yaml) {
    if (yaml.keySet().contains("environment")) {
        println "environment found"
        yaml["environment"].each {
            key, value -> println "${it.key}: ${it.value}"
        }
    }
}

node {
    checkout scm
    echo "a"
    def main = readYaml file: "main.yaml"
    echo "b"
    getEnvironment main
    echo "c"
}