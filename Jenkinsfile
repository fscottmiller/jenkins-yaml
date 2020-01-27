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
            container("${it['name']}") {
                stage("${it['name']}") {
                    sh "${it['command']}"
                }
            }
        }
    }
}
 
def getKube(yaml) {
    def images = []
    // [ 'name' : "${tool}", "image" : "${image}:${version}", 'ttyEnabled' : true, 'command' : 'cat' ]
    yaml['stages'].each {
        if (it.keySet().contains('image')) {
            def img = ['ttyEnabled': true, 'command': 'cat']
            img['name'] = it['image']
            img['img'] = it['image']
            images += img
        }
    }
    return images
}

node {
    checkout scm
    def main = readYaml file: "main.yaml"
    getEnvironment main
    def options = [:]
    options['containers'] = getKube main
    echo "${options}" //debug
    podTemplate(options) {
        node(POD_LABEL) {
            runStages main
        }
    }
}