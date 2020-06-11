# k8s-operator-sdk-demo

The codebase is modified from [<<Kubernetes Operator>>](https://www.amazon.com/Kubernetes-Operators-Automating-Container-Orchestration/dp/1492048046/ref=sr_1_1?crid=100BTNK8YSUT8&dchild=1&keywords=kubernetes+operators&qid=1591893369&sprefix=kubernetes+oper%2Caps%2C206&sr=8-1)

## Environment
- **Operating System**: Red Hat Enterprise Linux Server release 7.7 (Maipo)
- **Go **: go version go1.14.4 linux/amd64
- **operator-sdk**: v0.12.0+
- docker v17.03+, podman v1.2.0+, or buildah v1.7+
- OpenShift CLI (oc) v4.3+ installed
- Access to a cluster based on Kubernetes v1.12.0+
- Access to a container registry

## Steps
1. Git clone repository
```bash
git clone https://github.com/chengdol/k8s-operator-sdk-demo.git ~/k8s-operator-sdk-demo
```

2. Install Go language
Download and install from: https://golang.org/dl/

3. Install operator-sdk
https://sdk.operatorframework.io/docs/install-operator-sdk/
```bash
## select release version
RELEASE_VERSION=v0.12.0

## download release binary
curl -OJL https://github.com/operator-framework/operator-sdk/releases/download/${RELEASE_VERSION}/operator-sdk-${RELEASE_VERSION}-x86_64-linux-gnu

## Install binary to your PATH 
chmod +x operator-sdk-${RELEASE_VERSION}-x86_64-linux-gnu
sudo cp operator-sdk-${RELEASE_VERSION}-x86_64-linux-gnu /usr/local/bin/operator-sdk
rm operator-sdk-${RELEASE_VERSION}-x86_64-linux-gnu

## Verify installed correctly
operator-sdk version
```

4. Create Go-based operator
Generate operator skeleton:
```bash
##  
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
#export GO111MODULE=on

## no --type specified, default is go
OPERATOR_NAME=visitors-operator
OPERATOR_PATH=$GOPATH/src/demo
mkdir -p $OPERATOR_PATH
cd $OPERATOR_PATH
operator-sdk new $OPERATOR_NAME
```

Generate CRDs skeleton:
```bash
cd $OPERATOR_PATH/$OPERATOR_NAME
operator-sdk add api --api-version=example.com/v1 --kind=VisitorsApp
## from command outputs, you will see what files are generated
```

Copy or overwrite the 

## Test
