# Lab 05 - Networking

Usando a ferramenta OC para conectar ao cluster e depurar problemas

## 1 - Login no Cluster {#_1_login_no_cluster}

```text
oc login https://35.198.6.223:8443
```

## 2 - Scale up pod para duas replicas {#_2_scale_up_pod_para_duas_replicas}

```text
oc get all
oc scale deploymentconfig docker-phpapp --replicas=2
```

## 3 - Verifica configuracoes IP {#_3_verifica_configuracoes_ip}

```text
oc describe pod <nome do pod> | grep IP
```

## 4 - Ping entre containers {#_4_ping_entre_containers}

```text
oc describe pod <nome do pod> | grep IP
oc rsh <nome do pod>

# ping <ip do outro pod>
```

 

