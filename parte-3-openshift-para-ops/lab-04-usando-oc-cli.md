# Lab 04 - Usando OC Cli

Usando a ferramenta OC para conectar ao cluster e depurar problemas

## 1 - Login no Cluster {#_1_login_no_cluster}

```text
oc login https://openshift.example.com:8443
```

|  | Entrar com &lt;logincriado&gt; e senha redhat |
| :--- | :--- |


## 2 - Cria novo projeto {#_2_cria_novo_projeto}

```text
oc new-project <seu login>

oc new-app https://redhatbsb@bitbucket.org/redhatbsb/docker-phpapp.git --strategy=docker
```

## 3 - Usar OC para navegar no projeto {#_3_usar_oc_para_navegar_no_projeto}

```text
oc get all
oc get pods
```

## 4 - Depurar erros do pod {#_4_depurar_erros_do_pod}

```text
oc describe pod <nome do pod>

oc get events
oc logs <nome do pod>
```

 

