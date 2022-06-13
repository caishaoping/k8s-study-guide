# automation and shortcut k for kubectl

source <(kubectl completion bash)

alias k=kubectl

complete -F __start_kubectl k

# environment varible $DR to short expression in command

To setup short env variable:
DR="--dry-run=client -o yaml"

  then 
  
       k run mypod image=nginx $DR > mypod.yaml 
  
  is the same as below
  
       kubectl run mypod image=nginx --dry-run=client -o yaml > mypod.yaml

# kns alias for "switching" namespaces, to quickly set current namespace and avoid to include -n in every command:

alias kns='kubectl config set-context --current --namespace'

kns my-namespace1

#Ref:

[https://kubernetes.io/docs/reference/kubectl/cheatsheet/](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

[https://kube.academy/courses/how-to-prepare-for-the-cka-exam/lessons/aliases-shortcuts-and-command-completion](https://kube.academy/courses/how-to-prepare-for-the-cka-exam/lessons/aliases-shortcuts-and-command-completion)
