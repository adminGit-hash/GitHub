// Import the necessary classes
import jenkins.model.*
import jenkins.branch.*

// Define a new multibranch pipeline job
def createMultibranchPipelineJob(String jobName, String repoURL, String credentialsId) {
    def jenkins = Jenkins.instance
    def project = jenkins.createProject(org.jenkinsci.plugins.workflow.multibranch.WorkflowMultiBranchProject, jobName)
    
    def source = new org.jenkinsci.plugins.github_branch_source.GitHubSCMSource(repoURL)
    source.setCredentialsId(credentialsId)
    
    def factory = new org.jenkinsci.plugins.workflow.multibranch.WorkflowBranchProjectFactory()
    factory.setScriptPath('Jenkinsfile')
    
    project.setSourcesList([source])
    project.setProjectFactory(factory)
    
    return project
}

// Example usage
def job = createMultibranchPipelineJob('example-job', 'https://github.com/user/repo.git', 'github-creds')
