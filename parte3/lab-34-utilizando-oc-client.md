# Developer CLI Operations

* [Overview](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#overview)
* [Common Operations](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#oc-common-operations)
* [Object Types](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#object-types)
* [Basic CLI Operations](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#basic-cli-operations)
  * [types](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#types)
  * [login](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#login)
  * [logout](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#logout)
  * [new-project](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#new-project)
  * [new-app](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#new-app)
  * [status](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#status)
  * [project](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#project)
* [Application Modification CLI Operations](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#application-modification-cli-operations)
  * [get](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#get)
  * [describe](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#describe)
  * [edit](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#edit)
  * [volume](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#volume)
  * [label](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#label)
  * [expose](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#expose)
  * [delete](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#delete)
  * [set](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#set)
* [Build and Deployment CLI Operations](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#build-and-deployment-cli-operations)
  * [start-build](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#start-build)
  * [deploy](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#deploy)
  * [rollback](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#rollback)
  * [new-build](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#new-build)
  * [cancel-build](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#cancel-build)
  * [import-image](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#import-image)
  * [scale](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#scale)
  * [tag](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#tag)
* [Advanced Commands](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#advanced-commands)
  * [create](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#create)
  * [replace](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#replace)
  * [process](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#process)
  * [run](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#run)
  * [patch](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#patch)
  * [export](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#export)
  * [policy](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#policy)
  * [secrets](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#secrets)
  * [autoscale](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#autoscale)
* [Troubleshooting and Debugging CLI Operations](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#troubleshooting-and-debugging-cli-operations)
  * [logs](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#logs)
  * [exec](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#exec)
  * [rsh](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#rsh)
  * [rsync](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#cli-operations-rsync)
  * [port-forward](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#port-forward)
  * [proxy](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#proxy)

## Overview {#overview}

This topic provides information on the developer CLI operations and their syntax. You must[setup and login](https://docs.openshift.org/latest/cli_reference/get_started_cli.html#cli-reference-get-started-cli)with the CLI before you can perform these operations.

The developer CLI uses the`oc`command, and is used for project-level operations. This differs from the[administrator CLI](https://docs.openshift.org/latest/cli_reference/admin_cli_operations.html#cli-reference-admin-cli-operations), which uses the`oc adm`command for more advanced, administrator operations.

## Common Operations {#oc-common-operations}

The developer CLI allows interaction with the various objects that are managed by OpenShift Origin. Many common`oc`operations are invoked using the following syntax:

```
$ oc <action> <object_type> <object_name>
```

This specifies:

* An`<action>`to perform, such as`get`or`describe`.

* The`<object_type>`to perform the action on, such as`service`or the abbreviated`svc`.

* The`<object_name>`of the specified`<object_type>`.

For example, the`oc get`operation returns a complete list of services that are currently defined:

```
$ oc get svc
NAME              LABELS                                    SELECTOR                  IP              PORT(S)
docker-registry   docker-registry=default                   docker-registry=default   172.30.78.158   5000/TCP
kubernetes        component=apiserver,provider=kubernetes   
<
none
>
                    172.30.0.2      443/TCP
kubernetes-ro     component=apiserver,provider=kubernetes   
<
none
>
                    172.30.0.1      80/TCP
```

The`oc describe`operation can then be used to return detailed information about a specific object:

```
$ oc describe svc docker-registry
Name:			docker-registry
Labels:			docker-registry=default
Selector:		docker-registry=default
IP:			172.30.78.158
Port:			
<
unnamed
>
	5000/TCP
Endpoints:		10.128.0.2:5000
Session Affinity:	None
No events.
```

|  | Versions of`oc`prior to 1.0.5 did not have the ability to negotiate API versions against a server. So if you are using`oc`up to 1.0.4 with a server that only supports v1 or higher versions of the API, make sure to pass`--api-version`in order to point the`oc`client to the correct API endpoint. For example:`oc get svc --api-version=v1`. |
| :--- | :--- |


## Object Types {#object-types}

The CLI supports the following object types, some of which have abbreviated syntax:

| Object Type | Abbreviated Version |
| :--- | :--- |
| `build` |  |
| `buildConfig` | `bc` |
| `deploymentConfig` | `dc` |
| `deployments`\(Technology Preview\) | `deploy` |
| `event` | `ev` |
| `imageStream` | `is` |
| `imageStreamTag` | `istag` |
| `imageStreamImage` | `isimage` |
| `job` |  |
| `LimitRange` | `limits` |
| `node` |  |
| `pod` | `po` |
| `ResourceQuota` | `quota` |
| `replicationController` | `rc` |
| `replicaSet`\(Technology Preview\) | `rs` |
| `secrets` |  |
| `service` | `svc` |
| `ServiceAccount` | `sa` |
| `persistentVolume` | `pv` |
| `persistentVolumeClaim` | `pvc` |

## Basic CLI Operations {#basic-cli-operations}

The following table describes basic`oc`operations and their general syntax:

### types {#types}

Display an introduction to some core OpenShift Origin concepts:

```
$ oc types
```

### login {#login}

Log in to the OpenShift Origin server:

```
$ oc login
```

### logout {#logout}

End the current session:

```
$ oc logout
```

### new-project {#new-project}

Create a new project:

```
$ oc new-project 
<
project_name
>
```

### new-app {#new-app}

[Creates a new application](https://docs.openshift.org/latest/dev_guide/application_lifecycle/new_app.html#dev-guide-new-app)based on the source code in the current directory:

```
$ oc new-app .
```

Creates a new application based on the source code in a remote repository:

```
$ oc new-app https://github.com/openshift/cakephp-ex
```

Creates a new application based on the source code in a private remote repository:

```
$ oc new-app https://github.com/youruser/yourprivaterepo --source-secret=yoursecret
```

### status {#status}

Show an overview of the current project:

```
$ oc status
```

### project {#project}

Switch to another project. Run without options to display the current project. To view all projects you have access to run`oc projects`. Run without options to display the current project. To view all projects you have access to run`oc projects`.

```
$ oc project 
<
project_name
>
```

## Application Modification CLI Operations {#application-modification-cli-operations}

### get {#get}

Return a list of objects for the specified[object type](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#object-types). If the optional`<object_name>`is included in the request, then the list of results is filtered by that value.

```
$ oc get 
<
object_type
>
 [
<
object_name
>
]
```

### describe {#describe}

Returns information about the specific object returned by the query. A specific`<object_name>`must be provided. The actual information that is available varies as described in[object type](https://docs.openshift.org/latest/cli_reference/basic_cli_operations.html#object-types).

```
$ oc describe 
<
object_type
>
<
object_name
>
```

### edit {#edit}

Edit the desired object type:

```
$ oc edit 
<
object_type
>
/
<
object_name
>
```

Edit the desired object type with a specified text editor:

```
$ OC_EDITOR="
<
text_editor
>
" oc edit 
<
object_type
>
/
<
object_name
>
```

Edit the desired object in a specified format \(eg: JSON\):

```
$ oc edit 
<
object_type
>
/
<
object_name
>
 \
    --output-version=
<
object_type_version
>
 \
    -o 
<
object_type_format
>
```

### volume {#volume}

Modify a[volume](https://docs.openshift.org/latest/dev_guide/volumes.html#dev-guide-volumes):

```
$ oc volume 
<
object_type
>
/
<
object_name
>
 [--option]
```

### label {#label}

Update the labels on a object:

```
$ oc label 
<
object_type
>
<
object_name
>
<
label
>
```

### expose {#expose}

Look up a service and expose it as a route. There is also the ability to expose a deployment configuration, replication controller, service, or pod as a new service on a specified port. If no labels are specified, the new object will re-use the labels from the object it exposes.

If you are exposing a service, the default generator is`--generator=route/v1`. For all other cases the default is`--generator=service/v2`, which leaves the port unnamed. Generally, there is no need to set a generator with the`oc expose`command. A third generator,`--generator=service/v1`, is available with the port name default.

```
$ oc expose 
<
object_type
>
<
object_name
>
```

### delete {#delete}

Delete the specified object. An object configuration can also be passed in through STDIN. The`oc delete all -l <label>`operation deletes all objects matching the specified`<label>`, including the[replication controller](https://docs.openshift.org/latest/architecture/core_concepts/deployments.html#replication-controllers)so that pods are not re-created.

```
$ oc delete -f 
<
file_path
>
```

```
$ oc delete 
<
object_type
>
<
object_name
>
```

```
$ oc delete 
<
object_type
>
 -l 
<
label
>
```

```
$ oc delete all -l 
<
label
>
```

### set {#set}

Modify a specific property of the specified object.

#### SET ENV {#set-env}

Sets an environment variable on a deployment configuration or a build configuration:

```
$ oc set env dc/mydc VAR1=value1
```

#### SET BUILD-SECRET {#set-build-secret}

Sets the name of a secret on a build configuration. The secret may be an image pull or push secret or a source repository secret:

```
$ oc set build-secret --source bc/mybc mysecret
```

## Build and Deployment CLI Operations {#build-and-deployment-cli-operations}

One of the fundamental capabilities of OpenShift Origin is the ability to build applications into a container from source.

OpenShift Origin provides CLI access to inspect and manipulate deployment configurations using standard`oc`resource operations, such as`get`,`create`, and`describe`.

### start-build {#start-build}

Manually start the build process with the specified build configuration file:

```
$ oc start-build 
<
buildconfig_name
>
```

Manually start the build process by specifying the name of a previous build as a starting point:

```
$ oc start-build --from-build=
<
build_name
>
```

Manually start the build process by specifying either a configuration file or the name of a previous build and retrieve its build logs:

```
$ oc start-build --from-build=
<
build_name
>
 --follow
```

```
$ oc start-build 
<
buildconfig_name
>
 --follow
```

Wait for a build to complete and exit with a non-zero return code if the build fails:

```
$ oc start-build --from-build=
<
build_name
>
 --wait
```

Set or override environment variables for the current build without changing the build configuration. Alternatively, use`-e`.

```
$ oc start-build --env 
<
var_name
>
=
<
value
>
```

Set or override the default build log level output during the build:

```
$ oc start-build --build-loglevel [0-5]
```

Specify the source code commit identifier the build should use; requires a build based on a Git repository:

```
$ oc start-build --commit=
<
hash
>
```

Re-run build with name`<build_name>`:

```
$ oc start-build --from-build=
<
build_name
>
```

Archive`<dir_name>`and build with it as the binary input:

```
$ oc start-build --from-dir=
<
dir_name
>
```

Use existing archive as the binary input; unlike`--from-file`the archive will be extracted by the builder prior to the build process:

```
$ oc start-build --from-archive=
<
archive_name
>
```

Use`<file_name>`as the binary input for the build. This file must be the only one in the build source. For example,_**pom.xml**_or_**Dockerfile**_.

```
$ oc start-build --from-file=
<
file_name
>
```

Download the binary input using HTTP or HTTPS instead of reading it from the file system:

```
$ oc start-build --from-file=
<
file_URL
>
```

Download an archive and use its contents as the build source:

```
$ oc start-build --from-archive=
<
archive_URL
>
```

The path to a local source code repository to use as the binary input for a build:

```
$ oc start-build --from-repo=
<
path_to_repo
>
```

Specify a webhook URL for an existing build configuration to trigger:

```
$ oc start-build --from-webhook=
<
webhook_URL
>
```

The contents of the post-receive hook to trigger a build:

```
$ oc start-build --git-post-receive=
<
contents
>
```

The path to the Git repository for post-receive; defaults to the current directory:

```
$ oc start-build --git-repository=
<
path_to_repo
>
```

List the webhooks for the specified build configuration or build; accepts`all`,`generic`, or`github`:

```
$ oc start-build --list-webhooks
```

Override the**Spec.Strategy.SourceStrategy.Incremental**option of a source-strategy build:

```
$ oc start-build --incremental
```

Override the**Spec.Strategy.DockerStrategy.NoCache**option of a docker-strategy build:

```
$oc start-build --no-cache
```

### deploy {#deploy}

View a deployment, or manually start, cancel, or retry a deployment:

```
$ oc deploy 
<
deploymentconfig
>
```

### rollback {#rollback}

Perform a[rollback](https://docs.openshift.org/latest/dev_guide/deployments/basic_deployment_operations.html#rolling-back-a-deployment):

```
$ oc rollback 
<
deployment_name
>
```

### new-build {#new-build}

Create a build configuration based on the source code in the current Git repository \(with a public remote\) and a container image:

```
$ oc new-build .
```

Create a build configuration based on a remote git repository:

```
$ oc new-build https://github.com/openshift/cakephp-ex
```

Create a build configuration based on a private remote git repository:

```
$ oc new-build https://github.com/youruser/yourprivaterepo --source-secret=yoursecret
```

### cancel-build {#cancel-build}

Stop a build that is in progress:

```
$ oc cancel-build 
<
build_name
>
```

Cancel multiple builds at the same time:

```
$ oc cancel-build 
<
build1_name
>
<
build2_name
>
<
build3_name
>
```

Cancel all builds created from the build configuration:

```
$ oc cancel-build bc/
<
buildconfig_name
>
```

Specify the builds to be canceled:

```
$ oc cancel-build bc/
<
buildconfig_name
>
 --state=
<
state
>
```

Example values for**`state`**are**new**or**pending**.

### import-image {#import-image}

Import tag and image information from an external image repository:

```
$ oc import-image 
<
image_stream
>
```

### scale {#scale}

Set the number of desired replicas for a[replication controller](https://docs.openshift.org/latest/architecture/core_concepts/deployments.html#replication-controllers)or a deployment configuration to the number of specified replicas:

```
$ oc scale 
<
object_type
>
<
object_name
>
 --replicas=
<
#_of_replicas
>
```

### tag {#tag}

Take an existing tag or image from an image stream, or a container image "pull spec", and set it as the most recent image for a tag in one or more other image streams:

```
$ oc tag 
<
current_image
>
<
image_stream
>
```

## Advanced Commands {#advanced-commands}

### create {#create}

Parse a configuration file and create one or more OpenShift Origin objects based on the file contents. The`-f`flag can be passed multiple times with different file or directory paths. When the flag is passed multiple times,`oc create`iterates through each one, creating the objects described in all of the indicated files. Any existing resources are ignored.

```
$ oc create -f 
<
file_or_dir_path
>
```

### replace {#replace}

Attempt to modify an existing object based on the contents of the specified configuration file. The`-f`flag can be passed multiple times with different file or directory paths. When the flag is passed multiple times,`oc replace`iterates through each one, updating the objects described in all of the indicated files.

```
$ oc replace -f 
<
file_or_dir_path
>
```

### process {#process}

Transform a project[template](https://docs.openshift.org/latest/dev_guide/templates.html#dev-guide-templates)into a project configuration file:

```
$ oc process -f 
<
template_file_path
>
```

### run {#run}

Create and run a particular image, possibly replicated. By default, create a deployment configuration to manage the created container\(s\). You can choose to create a different resource using the`--generator`flag:

| API Resource | `--generator` | Option |
| :--- | :--- | :--- |
|  | Deployment configuration | `deploymentconfig/v1`\(default\) |
|  | Pod | `run-pod/v1` |
|  | Replication controller | `run/v1` |
|  | Deployment using`extensions/v1beta1`endpoint | `deployment/v1beta1` |
|  | Deployment using`apps/v1beta1`endpoint | `deployment/apps.v1beta1` |
|  | Job | `job/v1` |
|  | Cron job | `cronjob/v2alpha1` |

You can choose to run in the foreground for an interactive container execution.

```
$ oc run NAME --image=
<
image
>
 \
    [--generator=
<
resource
>
] \
    [--port=
<
port
>
] \
    [--replicas=
<
replicas
>
] \
    [--dry-run=
<
bool
>
] \
    [--overrides=
<
inline_json
>
] \
    [options]
```

### patch {#patch}

Updates one or more fields of an object using strategic merge patch:

```
$ oc patch 
<
object_type
>
<
object_name
>
 -p 
<
changes
>
```

The &lt;changes&gt; is a JSON or YAML expression containing the new fields and the values. For example, to update the`spec.unschedulable`field of the node`node1`to the value`true`, the json expression is:

```
$ oc patch node node1 -p '{"spec":{"unschedulable":true}}'
```

### export {#export}

Export resources to be used elsewhere:

```
$ oc export 
<
object_type
>
 [--options]
```

See[Creating a Template from Existing Objects](https://docs.openshift.org/latest/dev_guide/templates.html#export-as-template)for more information on exporting existing objects from your project in template form.

### policy {#policy}

Manage authorization policies:

```
$ oc policy [--options]
```

### secrets {#secrets}

Configure[secrets](https://docs.openshift.org/latest/dev_guide/secrets.html#dev-guide-secrets):

```
$ oc secrets [--options] path/to/ssh_key
```

### autoscale {#autoscale}

Setup an[autoscaler](https://docs.openshift.org/latest/dev_guide/pod_autoscaling.html#dev-guide-pod-autoscaling)for your application. Requires metrics to be enabled in the cluster. See[Enabling Cluster Metrics](https://docs.openshift.org/latest/install_config/cluster_metrics.html#install-config-cluster-metrics)for cluster administrator instructions, if needed.

```
$ oc autoscale dc/
<
dc_name
>
 [--options]
```

## Troubleshooting and Debugging CLI Operations {#troubleshooting-and-debugging-cli-operations}

### logs {#logs}

Retrieve the log output for a specific build, deployment, or pod. This command works for builds, build configurations, deployment configurations, and pods.

```
$ oc logs -f 
<
pod
>
```

### exec {#exec}

Execute a command in an already-running container. You can optionally specify a container ID, otherwise it defaults to the first container.

```
$ oc exec 
<
pod
>
 [-c 
<
container
>
] 
<
command
>
```

### rsh {#rsh}

Open a remote shell session to a container:

```
$ oc rsh 
<
pod
>
```

### rsync {#cli-operations-rsync}

Copy the contents to or from a directory in an already-running pod container. If you do not specify a container, it defaults to the first container in the pod.

To copy contents from a local directory to a directory in a pod:

```
$ oc rsync 
<
local_dir
>
<
pod
>
:
<
pod_dir
>
 -c 
<
container
>
```

To copy contents from a directory in a pod to a local directory:

```
$ oc rsync 
<
pod
>
:
<
pod_dir
>
<
local_dir
>
 -c 
<
container
>
```

### port-forward {#port-forward}

[Forward one or more local ports](https://docs.openshift.org/latest/dev_guide/port_forwarding.html#dev-guide-port-forwarding)to a pod:

```
$ oc port-forward 
<
pod
>
<
local_port
>
:
<
remote_port
>
```

### proxy {#proxy}

Run a proxy to the Kubernetes API server:

```
$ oc proxy --port=
<
port
>
 --www=
<
static_directory
>
```

|  | [For security purposes](https://access.redhat.com/errata/RHSA-2015:1650), the`oc exec`command does not work when accessing privileged containers. Instead, administrators can SSH into a node host, then use the`docker exec`command on the desired container. |
| :--- | :--- |



