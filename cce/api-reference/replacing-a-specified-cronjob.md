# Replacing a Specified CronJob<a name="cce_02_0230"></a>

## Function<a name="section11097543"></a>

This API is used to replace a specified CronJob resource object.

The following fields can be updated:

-   metadata.selfLink
-   metadata.resourceVersion
-   metadata.generation
-   metadata.creationTimestamp
-   metadata.deletionTimestamp
-   metadata.labels
-   metadata.clusterName
-   metadata.generateName
-   metadata.annotations
-   spec.replicas
-   template.contaions
-   spec.restartPolicy
-   spec.activeDeadlineSeconds

## URI<a name="section32769029"></a>

PUT /apis/batch/v1beta1/namespaces/\{namespace\}/cronjobs/\{name\}

[Table 1](#d0e41812)  describes the parameters of this API.

**Table  1**  Parameter description

<a name="d0e41812"></a>
<table><thead align="left"><tr id="row66886321"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.1"><p id="p65652297517"><a name="p65652297517"></a><a name="p65652297517"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.2"><p id="p165661629135114"><a name="p165661629135114"></a><a name="p165661629135114"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.3"><p id="p14567629115114"><a name="p14567629115114"></a><a name="p14567629115114"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row43988572"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="p6304590"><a name="p6304590"></a><a name="p6304590"></a>pretty</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="p40909805"><a name="p40909805"></a><a name="p40909805"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="p25359904"><a name="p25359904"></a><a name="p25359904"></a>If 'true', then the output is pretty printed.</p>
</td>
</tr>
<tr id="row26912549"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="p32432850"><a name="p32432850"></a><a name="p32432850"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="p9815175"><a name="p9815175"></a><a name="p9815175"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="p56831725"><a name="p56831725"></a><a name="p56831725"></a>name of the Job</p>
</td>
</tr>
<tr id="row41723482"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="p24158859"><a name="p24158859"></a><a name="p24158859"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="p10710594"><a name="p10710594"></a><a name="p10710594"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="p62251748"><a name="p62251748"></a><a name="p62251748"></a>Object name and auth scope, such as for teams and projects.</p>
</td>
</tr>
</tbody>
</table>

## Request<a name="d0e41861"></a>

**Request parameters**:

For the description about request parameters, see  [Table 2](creating-a-cronjob.md#table8040885).

**Example request**:

```
{
  "kind": "CronJob",
  "apiVersion": "batch/v1beta1",
  "metadata": {
    "name": "cronjob-test",
    "namespace": "default",
    "selfLink": "/apis/batch/v1beta1/namespaces/default/cronjobs/cronjob-test/status",
    "uid": "7cf2c54b-2201-11e8-96aa-fa163ecd089c",
    "resourceVersion": "441600",
    "creationTimestamp": "2018-03-07T12:17:22Z",
    "enable": true
  },
  "spec": {
    "schedule": "*/59 * * * *",
    "concurrencyPolicy": "Forbid",
    "suspend": false,
    "jobTemplate": {
      "metadata": {
        "creationTimestamp": null,
        "enable": true
  },
      "spec": {
        "template": {
          "metadata": {
            "creationTimestamp": null,
            "labels": {
              "sjname": "cronjob-test"
            },
            "enable": true
  },
          "spec": {
            "containers": [
              {
                "name": "container-0",
                "image": "nginx:stable-perl",
                "resources": {

                },
                "lifecycle": {

                },
                "terminationMessagePath": "/dev/termination-log",
                "terminationMessagePolicy": "File",
                "imagePullPolicy": "IfNotPresent"
              }
            ],
            "restartPolicy": "OnFailure",
            "terminationGracePeriodSeconds": 30,
            "dnsPolicy": "ClusterFirst",
            "securityContext": {

            },
            "imagePullSecrets": [
              {
                "name": "default-secret"
              }
            ],
            "schedulerName": "default-scheduler"
          }
        }
      }
    },
    "successfulJobsHistoryLimit": 3,
    "failedJobsHistoryLimit": 1
  }
}
```

## Response<a name="section37045669"></a>

**Response parameters:**

For the description about response parameters, see the parameter description in  [Table 2](creating-a-cronjob.md#table8040885).

**Example response:**

```
{
    "kind": "CronJob",
    "apiVersion": "batch/v1beta1",
    "metadata": {
        "name": "cronjob-test",
        "namespace": "default",
        "selfLink": "/apis/batch/v1beta1/namespaces/default/cronjobs/cronjob-test",
        "uid": "7cf2c54b-2201-11e8-96aa-fa163ecd089c",
        "resourceVersion": "441884",
        "creationTimestamp": "2018-03-07T12:17:22Z",
        "enable": true
    },
    "spec": {
        "schedule": "*/59 * * * *",
        "concurrencyPolicy": "Forbid",
        "suspend": false,
        "jobTemplate": {
            "metadata": {
                "creationTimestamp": null,
                "enable": true
    },
            "spec": {
                "template": {
                    "metadata": {
                        "creationTimestamp": null,
                        "labels": {
                            "sjname": "cronjob-test"
                        },
                        "enable": true
    },
                    "spec": {
                        "containers": [
                            {
                                "name": "container-0",
                                "image": "nginx:stable-perl",
                                "resources": {},
                                "lifecycle": {},
                                "terminationMessagePath": "/dev/termination-log",
                                "terminationMessagePolicy": "File",
                                "imagePullPolicy": "IfNotPresent"
                            }
                        ],
                        "restartPolicy": "OnFailure",
                        "terminationGracePeriodSeconds": 30,
                        "dnsPolicy": "ClusterFirst",
                        "securityContext": {},
                        "imagePullSecrets": [
                            {
                                "name": "default-secret"
                            }
                        ],
                        "schedulerName": "default-scheduler"
                    }
                }
            }
        },
        "successfulJobsHistoryLimit": 3,
        "failedJobsHistoryLimit": 1
    },
    "status": {}
}
```

## Status Code<a name="section64975570"></a>

[Table 2](#d0e41904)  describes the status code of this API.

**Table  2**  Status code

<a name="d0e41904"></a>
<table><thead align="left"><tr id="row40602325"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p453999"><a name="p453999"></a><a name="p453999"></a>Status Code</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p36773941"><a name="p36773941"></a><a name="p36773941"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row25899281"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p17466984"><a name="p17466984"></a><a name="p17466984"></a>200</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p5539620"><a name="p5539620"></a><a name="p5539620"></a>This operation succeeds, and a Job resource object is returned.</p>
</td>
</tr>
</tbody>
</table>

For the description about status codes, see  [Status Code](status-code.md).

