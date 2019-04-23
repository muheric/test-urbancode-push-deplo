node {
    // class: Defines the Pipeline plug-in to define. The UCD Jenkins Pipeline plug-in’s class name is UCDeployPublisher
    step ([$class: 'UCDeployPublisher',
    
    // siteName: The name of the IBM UrbanCode Deploy server configured in Jenkins Configure System page.
    siteName: 'https://appdeploy.bngf.local:8443',
    // Specify actions to perform against a single component.
    component: [
            $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
            componentName:'Jenkins',
            // createComponent: Define a new component to create.
            createComponent: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.ComponentHelper$CreateComponentBlock',
                // componentTemplate: The name of a template to base the component on.
                componentTemplate: '',
                // componentApplication: The name of an application to add the component to.
                componentApplication: 'Jenkins'
                
                ],
                
                // delivery: Perform a component version import.
            delivery: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
                
                // pushVersion: Name to assign the component version. BUILD_NAME is resolved by Jenkins.
                pushVersion: '${BUILD_NUMBER}',
                // baseDir: The base directory that contains the build artifacts.
                baseDir: 'jobs\\test-ucd\\workspace\\build\\distributions',
                // fileIncludePatterns: Regex defining what files to include.
                fileIncludePatterns: '*.zip',
                // fileExcludePatterns: Regex defining what files to exclude.
                fileExcludePatterns: '',
                // pushProperties: Assign properties to the new component version. Syntax: KEY=VALUE separated by new lines.
                pushProperties: 'jenkins.server=Local\njenkins.reviewed=false',
                // pushDescription: Description to assign to the component version.
                pushDescription: 'Pushed from Jenkins'
                ],
                // deploy: Automatically begins a deploy process on successful import.
            deploy: [
            $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$DeployBlock', 
            // deployApp, deployEnv, and deployProc: The Application, Environment, and Application Process to run.
            deployApp: 'Jenkins',
            deployEnv: 'Test',
            deployProc: 'Deploy Jenkins', 
            // skipWait: Optionally skip waiting for the UCD process to complete.
            skipWait: false,

            // deployReqProps: Specify application process properties.
            deployReqProps: 'AppProcessProp1=Value1\nAppProcessProp2=Value2',

        // createProcess: If the application process does not exist, this specification will create one. 
        createProcess: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.ProcessHelper$CreateProcessBlock',
                // processComponent: Specify a single component process to initialize the new application process. It will create a single Import Component step in an application process based on the component specified above.
                processComponent: 'Deploy'
            ],
            // deployVersions: Specify which versions to deploy. Syntax: COMPONENT:VERSION. Separate multiple with a new line character (\n).
            deployVersions: 'Jenkins:${BUILD_NUMBER}',

            // deployOnlyChanged: Specify to only deploy on changed versions.
            deployOnlyChanged: false,
            // createSnapshot: Creates a snapshot of the deployment environment.
            // If deployWithSnapshot is true, the snapshot will be created first and used for the deployment.
            // Also if deployWithSnapshot is true, the deployVersions in the deploy block will be added to the new snapshot, instead of being used for the deployment.
            createSnapshot: [
               $class:'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$CreateSnapshotBlock',
                snapshotName: 'NameExample',
                deployWithSnapshot: false
            ]
            
    ]
]
        ])
}
