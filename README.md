## database
数据库方面; 
如：MySQL、Redis等

## 命名空间
`执行database-namespace.yaml文件`
```
kubectl create -f database-namespace.yaml
```
## MySQL
`执行一下yaml文件`
```
## 对外暴露端口
kubectl create -f  mysql-service.yaml

## pvc持久化存储卷
kubectl create -f  mysql-pvc.yaml

## MySQL配置文件
kubectl create -f  mysql-config.yaml

## deployment服务部署
kubectl create -f  mysql-deployment.yaml
```

## Redis
`执行一下yaml文件`
```
## 对外暴露端口
kubectl create -f  redis-service.yaml

## pvc持久化存储卷
kubectl create -f  redis-pvc.yaml

## Redis配置文件
kubectl create -f  redis-config.yaml

## deployment服务部署
kubectl create -f  redis-deployment.yaml
```

## 查看执行结果
`查看pod`
>[root@k8s-master ~]# kubectl get pod -n database 
```
NAME                     READY   STATUS    RESTARTS   AGE
mysql-8c44bb948-7z656    1/1     Running   0          40m
redis-5d4dbd59c6-64sfg   1/1     Running   0          5d20h
```
`查看config`
>[root@k8s-master ~]# kubectl get configmaps -n database
``` 
NAME           DATA   AGE
mysql-config   1      39m
redis-config   1      5d20h
```
`查看pvc`
>[root@k8s-master ~]# kubectl get pvc -n database 
```
NAME    STATUS   VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
mysql   Bound    mysql    50Gi       RWO                           5d19h
redis   Bound    redis    10Gi       RWO                           5d20h
```
`查看service`
>[root@k8s-master ~]# kubectl get service -n database 
```
NAME    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
mysql   ClusterIP   10.99.220.206   <none>        3306/TCP   5d19h
redis   ClusterIP   10.98.180.137   <none>        6379/TCP   5d20h
```
