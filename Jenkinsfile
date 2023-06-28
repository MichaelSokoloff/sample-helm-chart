def repo="https://github.com/MichaelSokoloff/sample-helm-chart/"
pipeline{
		agent{
			label 'helm'
		}
		stages{

                stage("add Repo") {
                        steps {
                               sh "helm repo add ${repo}"
                            }
                    }
				stage("Deploy to Dev") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app mysample/sample-app --values dev/values.yaml -n dev --wait"
                                    }
                                }
                            }
                    }
                stage("Deploy to UAT") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app mysample/sample-app --values uat/values.yaml -n uat --wait"
                                    }
                                }
                            }
                    }
            }
        }
