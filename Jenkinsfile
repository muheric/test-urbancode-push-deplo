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
                baseDir: 'jobs/Jenkins-to_ucd/workspace/build/distributions',  
                fileIncludePatterns: '*.zip',
                fileExcludePatterns: '',
                pushProperties: 'jenkins.server=Local\jenkins.reviewed=false',
                pushDescription: 'Pushed from Jenkins',
                pushIncremental: false
            ]
        ]
    ])
}
