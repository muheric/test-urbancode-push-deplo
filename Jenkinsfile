node {
   step([$class: 'UCDeployPublisher',
        siteName: 'local',
        component: [
            $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
            componentName: 'Jenkins',
            createComponent: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.ComponentHelper$CreateComponentBlock',
                componentTemplate: '',
                componentApplication: 'Jenkins'
            ],
            delivery: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
                pushVersion: '${BUILD_NUMBER}',
               baseDir: '/var/lib/jenkins/workspace/Jenkins-to_UCD/',  
                fileIncludePatterns: '*.zip',
                fileExcludePatterns: '',
                pushProperties: 'jenkins.server=Local\njenkins.reviewed=false',
                pushDescription: 'Pushed from Jenkins',
                pushIncremental: false
            ],
           
           
           deploy: [
            $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$DeployBlock',
            deployApp: 'Jenkins',
            deployEnv: 'Test',
            deployProc: 'Deploy Jenkins',
            createProcess: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.ProcessHelper$CreateProcessBlock',
                processComponent: 'Deploy'
            ],
            deployVersions: 'Jenkins:${BUILD_NUMBER}',
            deployOnlyChanged: false
        ]
        ]
    ])
}
