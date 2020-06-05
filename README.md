 Forked from https://github.com/godaddy/kubernetes-external-secrets. 

 1. AWS account setup using step 4 in section https://github.com/godaddy/kubernetes-external-secrets#aws-based-backends. 
 > Directly provide AWS access credentials to the
> kubernetes-external-secrets pod by environmental variables.
> 
> Using AWS access credentials Set AWS_ACCESS_KEY_ID and
> AWS_SECRET_ACCESS_KEY env vars in the kubernetes-external-secrets
> session/pod. You can use envVarsFromSecret in the helm chart to create
> these env vars from existing k8s secrets

Edit the file charts/aws-secret/secret.yaml and add the aws credentials to be used by this tool.
kubectl apply -f secret.yaml
 2. Run command 
 `helm template -f charts/kubernetes-external-secrets/values.yaml --output-dir ./output_dir ./charts/kubernetes-external-secrets/`
 3. `cd ./output_dir/kubernetes-external-secrets/templates && kubectl apply -f deployment.yaml -f rbac.yaml -f service.yaml -f serviceaccount.yaml`
 4. You will see release-name-kubernetes-external-secrets-xxx as a pod in the list now. 
 5. kubect logs release-name-kubernetes-external-secrets-xxx to verify if there are no logged errors.




