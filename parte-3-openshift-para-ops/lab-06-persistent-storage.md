# Lab 06 - Persistent Storage

Usando a ferramenta OC para conectar ao cluster e visualizar configuracoes de rede

```text
1 - Acessa Interface Web
2 - Acessa Deployment config e seleciona Actions -> Add Storage
3 - Cria um Storage Claim
4 - Lista claims usando oc get pvc
5 - Visualiza pod travado
6 - Cria-se pv para dar suporte ao pvc
```

Sintaxe criacao PV

```text
apiVersion: v1
kind: PersistentVolume
metadata:
 name: <login>
spec:
 capacity:
   storage: 5Gi
 accessModes:
 - ReadWriteOnce
 nfs:
   path: /exports/pvs/<login>
   server: nfs.example.com
 persistentVolumeReclaimPolicy: Recycle
```

Para criacao do pv:

```text
oc create -f pv.yaml
```

 

