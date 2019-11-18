# google-containers
google containers from gcr.io

1.  编写 Dockerfile (以 dashboard 为例)

<code>
#cd googlecontainer
# mkdir dashboard
# cd dashboard
# vim Dockerfile
<code>
 
FROM gcr.io/google_containers/kubernetes-dashboard-amd64:v1.7.1
MAINTAINER xxx@xxx.com

2.  提交克隆
# cd <克隆代码根目录>
# git add .
# git commit -m "kubernetes-dashboard-amd64:v1.7.1"
# git push

3.  最后提交完成后的代码结构
4.  登陆 DockerHub，创建 Automated Build 项目
    如未关联账号，会提示绑定 github 账号，按提示操作即可。
    如已绑定 github，则选择 github 方式的 Automated Build 项目，如图
    接着按照提示，选择 github 上我们的项目 googlecontainer 即可，仓库名设置为 dashboard
    配置 Build Settings
    指定 Dockerfile 所在的目录（到目录级即可），设置镜像 tag，先点 Save Changes，再点 Trigger
5.  编译完成后，我们就可以把镜像拉取到本地。
    自己改一下 tag 就是 gcr.io/google_containers/kubernetes-dashboard-amd64:v1.7.1 镜像了。
    
    
## Kubernets1.16.3 镜像（on CentOS after testing）：
k8s.gcr.io/kube-apiserver:v1.16.3
k8s.gcr.io/kube-controller-manager:v1.16.3
k8s.gcr.io/kube-scheduler:v1.16.3
k8s.gcr.io/kube-proxy:v1.16.3
k8s.gcr.io/pause:3.1
k8s.gcr.io/etcd:3.3.15-0
k8s.gcr.io/coredns:1.6.2
