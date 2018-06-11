node {
  def PWD = pwd()
  stage("Cleanup Workspace") {
    sh 'echo Cleaning up workspace .....'
    cleanWs()
    sh 'echo y | docker system  prune'
  }
  stage("Checkout") {
    checkout scm
  }
  stage("Build") {
    sh "docker run --rm --interactive --volume $PWD:/app composer install"
  }
  stage("Unit Test") {
    sh "${PWD}/vendor/bin/phpunit -c tests/unit/phpunit.xml tests/unit"
  }
  stage("Deploy") {
    timeout(time:5, unit:'HOURS') {
      input message: 'Approve deployment?', ok: 'Deploy!'
    }
    sh 'if docker node ls > /dev/null 2>&1; then docker swarm leave --force; fi'
    sh 'if ! docker images | grep megazebra-php >  /dev/null 2>&1; then docker build -t megazebra-php -f ./docker/php/Dockerfile .; fi'
    sh 'docker swarm init'
    sh 'docker stack deploy -c docker-compose.yml source-stock'
  }

}
