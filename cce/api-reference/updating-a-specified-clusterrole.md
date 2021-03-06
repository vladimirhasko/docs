# Updating a Specified ClusterRole<a name="cce_02_0287"></a>

## Function<a name="section672913236390"></a>

This API is used to partially update a specified ClusterRole.

## URL<a name="section6472741193912"></a>

PATCH /apis/rbac.authorization.k8s.io/v1/clusterroles/\{name\}

[Table 1](#d0e42906)  describes the parameters of this API.

**Table  1**  Parameter description

<a name="d0e42906"></a>
<table><thead align="left"><tr id="row10640301"><th class="cellrowborder" valign="top" width="22.220000000000002%" id="mcps1.2.4.1.1"><p id="p65652297517"><a name="p65652297517"></a><a name="p65652297517"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="17.169999999999998%" id="mcps1.2.4.1.2"><p id="p165661629135114"><a name="p165661629135114"></a><a name="p165661629135114"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="60.61%" id="mcps1.2.4.1.3"><p id="p14567629115114"><a name="p14567629115114"></a><a name="p14567629115114"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row19095777"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p3254085"><a name="p3254085"></a><a name="p3254085"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p62254326"><a name="p62254326"></a><a name="p62254326"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p9435611"><a name="p9435611"></a><a name="p9435611"></a>Name of the ClusterRole.</p>
</td>
</tr>
<tr id="row17811636"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p33456451"><a name="p33456451"></a><a name="p33456451"></a>pretty</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p25618043"><a name="p25618043"></a><a name="p25618043"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p61795587"><a name="p61795587"></a><a name="p61795587"></a>If 'true', then the output is pretty printed.</p>
</td>
</tr>
<tr id="row26391471649"><td class="cellrowborder" valign="top" width="22.220000000000002%" headers="mcps1.2.4.1.1 "><p id="p14640471145"><a name="p14640471145"></a><a name="p14640471145"></a>body</p>
</td>
<td class="cellrowborder" valign="top" width="17.169999999999998%" headers="mcps1.2.4.1.2 "><p id="p064011716413"><a name="p064011716413"></a><a name="p064011716413"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="60.61%" headers="mcps1.2.4.1.3 "><p id="p46408710414"><a name="p46408710414"></a><a name="p46408710414"></a>-</p>
</td>
</tr>
</tbody>
</table>

## Request<a name="section1097017235815"></a>

**Request parameters:**

For the description about request parameters, see  [Table 2](creating-a-clusterrole.md#table1154814995615).

For the description about the  **Content-Type**  field, see  [Patch Request Method Operation Description](patch-request-method-operation-description.md).

**Example request:**

```
{
	"kind": "ClusterRole",
	"apiVersion": "rbac.authorization.k8s.io/v1",
	"metadata": {
		"name": "secret-reader",
		"selfLink": "/apis/rbac.authorization.k8s.io/v1/clusterroles/secret-reader",
		"uid": "6a044ac2-f213-11e8-b449-fa163ec24e06",
		"resourceVersion": "44658",
		"creationTimestamp": "2018-11-27T07:09:43Z"
	},
	"rules": [{
		"verbs": ["get","list"],
		"apiGroups": [""],
		"resources": ["secrets"]
	}]
}
```

## Response<a name="section13598181712916"></a>

**Response parameters:**

For the description about response parameters, see  [Table 2](creating-a-clusterrole.md#table1154814995615).

**Example response:**

```
{
	"kind": "ClusterRole",
	"apiVersion": "rbac.authorization.k8s.io/v1",
	"metadata": {
		"name": "secret-reader",
		"selfLink": "/apis/rbac.authorization.k8s.io/v1/clusterroles/secret-reader",
		"uid": "c5986470-f2d5-11e8-b449-fa163ec24e06",
		"resourceVersion": "225014",
		"creationTimestamp": "2018-11-28T06:20:59Z"
	},
	"rules": [{
		"verbs": ["get","list"],
		"apiGroups": [""],
		"resources": ["secrets"]
	}]
}
```

## Status Code<a name="section14947131610112"></a>

[Table 2](#d0e43055)  describes the status code of this API.

**Table  2**  Status Code

<a name="d0e43055"></a>
<table><thead align="left"><tr id="row20813512"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p8172937"><a name="p8172937"></a><a name="p8172937"></a>Status Code</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p58028199"><a name="p58028199"></a><a name="p58028199"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row2663689"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p14432280"><a name="p14432280"></a><a name="p14432280"></a>200</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p13489144118012"><a name="p13489144118012"></a><a name="p13489144118012"></a>OK</p>
</td>
</tr>
</tbody>
</table>

