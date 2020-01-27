// set env variables based on the environment root key
def getEnvironment(yaml) {
    if (yaml.keySet().contains("environment")) {
        yaml["environment"].each { key, value -> 
            env."${key}" = value
        }
    }
}

def runStages(yaml) {
    if (yaml.keySet().contains('stages')) {
        yaml['stages'].each {
            stage("${it['name']}") {
                echo "${it['command']}"
            }
        }
    }
}
 
// TODO: no parameters for now
// set parameters based on the parameters root key
// def getParameters(yaml) {
//     if (yaml.keySet().contains("parameters")) {
//         def parameterList = []
//         yaml['parameters'].each {
//             parameterList += "${yaml['type']}"(name: "${yaml['name']}")
//         }
//         return parameterList
//     }
// }

node {
    checkout scm
    def main = readYaml file: "main.yaml"
    getEnvironment main
    runStages main
}