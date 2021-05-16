### 简述kubectl logs/describe/apply/delete功能
kubectl logs: 输出pod中一个容器的日志
kubectl describe: 输出指定的一个/多个资源的详细信息。
kubectl apply: 通过文件名或控制台输入，对资源进行配置,接受JSON和YAML格式的描述文件。
kubectl delete: 通过文件名、控制台输入、资源名或者label selector删除资源。 接受JSON和YAML格式的描述文件。


### 简述Pod, Node, Deployment, Service, Ingress, ReplicaSet, Namespace概念
Pod: pod是最小的部署单元，可以对其进行创建，调度和管理操作。一个Pod相当于一个共享context的配置组，在同一个context下，应用可能还会有独立的cgroup隔离机制，一个Pod是一个容器环境下的“逻辑主机”，它可能包含一个或者多个紧密相连的应用，这些应用可能是在同一个物理主机或虚拟机上。

Node: Node是Pod真正运行的主机，可以物理机，也可以是虚拟机。为了管理Pod，每个Node节点上至少要运行container runtime（比如docker或者rkt）、kubelet和kube-proxy服务。不像其他的资源（如Pod和Namespace），Node本质上不是Kubernetes来创建的，Kubernetes只是管理Node上的资源

Deployment: Deployment为Pod和ReplicaSet提供了一个声明式定义(declarative)方法，用来替代以前的ReplicationController来方便的管理应用, 可以定义Deployment来创建Pod和ReplicaSet、滚动升级和回滚应用、扩容和缩容、暂停和继续Deployment

Service: Service是一种k8s集群中访问pod的一种策略。k8s中的pod具有生命周期，且不可复活。每个pod有着自己的IP地址，pod的销毁与创建都会创新的IP地址。Service就是用来统一管理跟踪这些pod的变化，即使pod发生变化，对于前台的调用是无感知，前台无需进行任何修改。service肩负着服务发现与负载均衡等职能。

Ingress: 通常情况下，service和pod的IP仅可在集群内部访问。集群外部的请求需要通过负载均衡转发到service在Node上暴露的NodePort上，然后再由kube-proxy将其转发给相关的Pod。而Ingress就是为进入集群的请求提供路由规则的集合,Ingress可以给service提供集群外部访问的URL、负载均衡、SSL终止、HTTP路由等

ReplicaSet: ReplicaSet是下一代复本控制器, 他可确保指定数量的pod“replicas”在任何设定的时间运行

Namespace: Namespace是对一组资源和对象的抽象集合,常用来隔离不同的用户，比如可以用来将系统内部的对象划分为不同的项目组或用户组。常见的pods, services, replication controllers和deployments等都是属于某一个namespace的（默认是default）
