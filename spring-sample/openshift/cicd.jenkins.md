node() {
stage 'build-dev'
    openshiftBuild(namespace: 'dev', buildConfig: 'spring-sample', showBuildLogs: 'true')
stage 'deploy-dev'
    openshiftDeploy(namespace: 'dev',deploymentConfig: 'spring-sample')
    openshiftScale(namespace: 'dev',deploymentConfig: 'spring-sample',replicaCount: '1')

stage 'deploy-stage'
    openshiftTag(namespace: 'dev', sourceStream: 'spring-sample',  sourceTag: 'latest', destinationStream: 'spring-sample', destinationTag: 'promoteToQA')

    openshiftDeploy(namespace: 'stage',deploymentConfig: 'spring-sample')
    openshiftScale(namespace: 'stage',deploymentConfig: 'spring-sample',replicaCount: '1')
    
}
