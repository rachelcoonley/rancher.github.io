---
title: Rancher API - project
layout: rancher-api-v2-beta-default-v1.6
version: v1.6
lang: en
apiVersion: v2-beta
#redirect_from:
#  - /rancher/v1.6/zh/api/v2-beta/api-resources/project/
---

## Project

A "project" in the API is referred to as an environment in the UI and Rancher documentation. In the API documentation, we'll use the UI terminology. All hosts and any Rancher resources (i.e. containers, load balancers, etc.) are created and belong to an [environment]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/environments/). Access control to who can view and manage these resources are then defined by the owner of the environment. Rancher currently supports the capability for each user to manage and invite other users to their environment and allows for the ability to create multiple environments for different workloads. For example, you may want to create a "dev" environment and a separate "production" environment with its own set of resources and limited user access for your application deployment.

### Resource Fields

#### Writeable Fields

Field | Type | Create | Update | Default | Notes
---|---|---|---|---|---
allowSystemRole | boolean | Optional | Yes | - | 
description | string | Optional | Yes | - | 
hostRemoveDelaySeconds | int | Optional | Yes | - | 
members | array[[projectMember]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/projectMember/)] | Optional | - | - | 
name | string | Optional | Yes | - | 
projectLinks | array[[project]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/project/)] | Optional | Yes | - | 
projectTemplateId | [projectTemplate]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/projectTemplate/) | Optional | - | - | 
servicesPortRange | [servicesPortRange]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/servicesPortRange/) | Optional | Yes | - | 
virtualMachine | boolean | Optional | Yes | - | 


#### Read Only Fields

Field | Type   | Notes
---|---|---
data | map[json]  | 
defaultNetworkId | [network]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/network/)  | 
healthState | string  | 
id | int  | The unique identifier for the project
orchestration | string  | 
version | string  | 


<br>

Please read more about the [common resource fields]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/common/). These fields are read only and applicable to almost every resource. We have segregated them from the list above.

### Operations
{::options parse_block_html="true" /}
<a id="create"></a>
<div class="action"><span class="header">Create<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects</code></span></span>
<div class="action-contents"> {% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
-H 'Content-Type: application/json' \
-d '{
	"allowSystemRole": false,
	"description": "string",
	"hostRemoveDelaySeconds": 0,
	"members": "array[projectMember]",
	"name": "string",
	"projectLinks": "array[reference[project]]",
	"projectTemplateId": "reference[projectTemplate]",
	"servicesPortRange": {
		"endPort": 0,
		"startPort": 0
	},
	"uuid": "string",
	"virtualMachine": false
}' 'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects'
{% endhighlight %}
</div></div>
<a id="delete"></a>
<div class="action"><span class="header">Delete<span class="headerright">DELETE:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}</code></span></span>
<div class="action-contents"> {% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X DELETE \
'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}'
{% endhighlight %}
</div></div>
<a id="update"></a>
<div class="action"><span class="header">Update<span class="headerright">PUT:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}</code></span></span>
<div class="action-contents"> {% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X PUT \
-H 'Content-Type: application/json' \
-d '{
	"allowSystemRole": false,
	"description": "string",
	"hostRemoveDelaySeconds": 0,
	"name": "string",
	"projectLinks": "array[reference[project]]",
	"servicesPortRange": {
		"endPort": 0,
		"startPort": 0
	},
	"virtualMachine": false
}' 'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}'
{% endhighlight %}
</div></div>



### Actions

<div class="action" id="activate">
<span class="header">
activate
<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=activate</code></span></span>
<div class="action-contents">

<br>
<span class="input">
<strong>Input:</strong>This action has no inputs</span>

<br>
{% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=activate'
{% endhighlight %}
<br>
<span class="output"><strong>Output:</strong> An updated copy of the <a href="{{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/account/">account</a> resource</span>
</div></div>

<div class="action" id="deactivate">
<span class="header">
deactivate
<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=deactivate</code></span></span>
<div class="action-contents">

<br>
<span class="input">
<strong>Input:</strong>This action has no inputs</span>

<br>
{% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=deactivate'
{% endhighlight %}
<br>
<span class="output"><strong>Output:</strong> An updated copy of the <a href="{{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/account/">account</a> resource</span>
</div></div>

<div class="action" id="defaultNetworkId">
<span class="header">
defaultNetworkId
<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=defaultNetworkId</code></span></span>
<div class="action-contents">

<br>
<span class="input">
<strong>Input:</strong>This action has no inputs</span>

<br>
{% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=defaultNetworkId'
{% endhighlight %}
<br>

</div></div>

<div class="action" id="setmembers">
<span class="header">
setmembers
<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=setmembers</code></span></span>
<div class="action-contents">

<br>
<span class="input">
<strong>Input:</strong> <a href="{{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/setProjectMembersInput/">SetProjectMembersInput</a></span>

Field | Type | Required | Default | Notes
---|---|---|---|---
members | array[[projectMember]({{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/projectMember/)] | Yes |  | 


<br>
{% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
-H 'Content-Type: application/json' \
-d '{
	"members": "array[projectMember]"
}' 'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=setmembers'
{% endhighlight %}
<br>
<span class="output"><strong>Output:</strong> An updated copy of the <a href="{{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/setProjectMembersInput/">setProjectMembersInput</a> resource</span>
</div></div>

<div class="action" id="upgrade">
<span class="header">
upgrade
<span class="headerright">POST:  <code>/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=upgrade</code></span></span>
<div class="action-contents">

<br>
<span class="input">
<strong>Input:</strong>This action has no inputs</span>

<br>
{% highlight json %}
curl -u "${RANCHER_ACCESS_KEY}:${RANCHER_SECRET_KEY}" \
-X POST \
'http://${RANCHER_URL}:8080/v2-beta/projects/${PROJECT_ID}/projects/${ID}?action=upgrade'
{% endhighlight %}
<br>
<span class="output"><strong>Output:</strong> An updated copy of the <a href="{{site.baseurl}}/rancher/{{page.version}}/{{page.lang}}/api/{{page.apiVersion}}/api-resources/account/">account</a> resource</span>
</div></div>


