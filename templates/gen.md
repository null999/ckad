# pod with port
k run web --image=nginx:1.19.0 --port=80 --dry-run=client -o yaml

# pod with limits
k run web --image=nginx:1.19.0 --port=80 --limits=cpu=1 --requests=cpu=0.5 --dry-run=client -o yaml

# pod with env
k run web --image=nginx --port=80 --env=version=2 --dry-run=client -o yaml | k apply -f -

# deploy
k create deploy webdeploy --image=nginx --dry-run=client -o yaml

# svc
k expose deploy webdeploy --name websvc --port=80 --target-port=80 --type=ClusterIP --dry-run=client -o yaml > svc.yaml