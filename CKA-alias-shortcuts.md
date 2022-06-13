source <(kubectl completion bash)

alias k=kubectl

complete -F __start_kubectl k

To setup short env variable:
DR="--dry-run=client -o yaml" 
  then k run mypod image=nginx $DR > mypod.yaml 
  is the same as below
       kubectl run mypod image=nginx --dry-run=client -o yaml > mypod.yaml
       

[https://kubernetes.io/docs/reference/kubectl/cheatsheet/](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
