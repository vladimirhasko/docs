# Creating a Cluster and Running a Job<a name="EN-US_TOPIC_0172486173"></a>

## Function<a name="s37afee5a7f0344fa98179a36b0556841"></a>

This API is used to create an MRS cluster and submit a job in the cluster. This API is incompatible with Sahara.

A maximum of 10 clusters can be concurrently created. You can set the  **enterprise\_project\_id**  parameter to perform fine-grained authorization for resources.

Before using the API, you need to obtain the resources listed in  [Table 1](#tbbd2986d18874f82a8ab886ac25a57f8).

**Table  1**  Obtaining resources

<a name="tbbd2986d18874f82a8ab886ac25a57f8"></a>
<table><thead align="left"><tr id="rb8d7bb617c8e401d835b3c77bad750eb"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.3.1.1"><p id="a7230cc50da2046438b7ce546b0df50b0"><a name="a7230cc50da2046438b7ce546b0df50b0"></a><a name="a7230cc50da2046438b7ce546b0df50b0"></a>Resource</p>
</th>
<th class="cellrowborder" valign="top" width="80%" id="mcps1.2.3.1.2"><p id="abea8810be493490e91e9d5ba4b2a37f9"><a name="abea8810be493490e91e9d5ba4b2a37f9"></a><a name="abea8810be493490e91e9d5ba4b2a37f9"></a>How to Obtain</p>
</th>
</tr>
</thead>
<tbody><tr id="r86ba4472ec2c4913adeb0cfbb9c5b679"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="afedb9fba77044b72981436b1c265fa34"><a name="afedb9fba77044b72981436b1c265fa34"></a><a name="afedb9fba77044b72981436b1c265fa34"></a>VPC</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><p id="af90e107da77844efb1b16b47eb089751"><a name="af90e107da77844efb1b16b47eb089751"></a><a name="af90e107da77844efb1b16b47eb089751"></a>See operation instructions in <span class="parmvalue" id="parmvalue458414556244"><a name="parmvalue458414556244"></a><a name="parmvalue458414556244"></a><b>VPC &gt; Creating a VPC</b></span> and <span class="parmvalue" id="parmvalue16584155192417"><a name="parmvalue16584155192417"></a><a name="parmvalue16584155192417"></a><b>VPC &gt; Create a VPC</b></span> in the <i><cite id="cite86741a76c6df44d989f53cfbdf23fdbd150712"><a name="cite86741a76c6df44d989f53cfbdf23fdbd150712"></a><a name="cite86741a76c6df44d989f53cfbdf23fdbd150712"></a>VPC API Reference</cite></i>.</p>
</td>
</tr>
<tr id="re8a14fa01edb4772ab9da326952a8401"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="affe524418f25422ab47ed9e2a3718584"><a name="affe524418f25422ab47ed9e2a3718584"></a><a name="affe524418f25422ab47ed9e2a3718584"></a>Subnet</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><p id="ae4ce4a66af554a60b2cf8681be434531"><a name="ae4ce4a66af554a60b2cf8681be434531"></a><a name="ae4ce4a66af554a60b2cf8681be434531"></a>See operation instructions in <span class="parmvalue" id="parmvalue1551615511259"><a name="parmvalue1551615511259"></a><a name="parmvalue1551615511259"></a><b>Subnet &gt; Querying Subnets</b></span> and <span class="parmvalue" id="parmvalue1851612512511"><a name="parmvalue1851612512511"></a><a name="parmvalue1851612512511"></a><b>Subnet &gt; Creating a Subnet</b></span> in the <i><cite id="citedf8f339d4ca2452cbf7e65adba07af49150712"><a name="citedf8f339d4ca2452cbf7e65adba07af49150712"></a><a name="citedf8f339d4ca2452cbf7e65adba07af49150712"></a>VPC API Reference</cite></i>.</p>
</td>
</tr>
<tr id="r2e91958f22114a4ca9dadd9bc99c9579"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="a9f9e837842c2421093ff2278b2799ac3"><a name="a9f9e837842c2421093ff2278b2799ac3"></a><a name="a9f9e837842c2421093ff2278b2799ac3"></a>Key Pair</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><p id="a84edd7cf268441518c10fb14dd6caf19"><a name="a84edd7cf268441518c10fb14dd6caf19"></a><a name="a84edd7cf268441518c10fb14dd6caf19"></a>See operation instructions in <span class="parmvalue" id="parmvalue310042415259"><a name="parmvalue310042415259"></a><a name="parmvalue310042415259"></a><b>ECS SSH Key Management &gt; Querying SSH Key Pairs</b></span> and <span class="parmvalue" id="parmvalue4100724122517"><a name="parmvalue4100724122517"></a><a name="parmvalue4100724122517"></a><b>ECS SSH Key Management &gt; Querying SSH Key Pairs</b></span> in the <i><cite id="citeac62c6d6698d41aaab4b6decb6aa6deb150712"><a name="citeac62c6d6698d41aaab4b6decb6aa6deb150712"></a><a name="citeac62c6d6698d41aaab4b6decb6aa6deb150712"></a>ECS API Reference</cite></i>.</p>
</td>
</tr>
<tr id="r7d55c3c90c82441f9f123f81dcf78e85"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="a95fc2f7c9caf4bb3bbbc6c25a58b7c7f"><a name="a95fc2f7c9caf4bb3bbbc6c25a58b7c7f"></a><a name="a95fc2f7c9caf4bb3bbbc6c25a58b7c7f"></a>Region</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><p id="aa5e85a0b34ff4c4e8ca5917c0827a0f6"><a name="aa5e85a0b34ff4c4e8ca5917c0827a0f6"></a><a name="aa5e85a0b34ff4c4e8ca5917c0827a0f6"></a>Obtain the region and AZ information from the . For more information about regions and AZs, see <a href="https://docs.otc.t-systems.com/en-us/endpoint/index.html" target="_blank" rel="noopener noreferrer">Regions and Endpoints</a>.</p>
</td>
</tr>
<tr id="reda47ef0882f40ef9e8b0001b85173d2"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="aa6e817b43e73414d8d9207fc1a3ee9fc"><a name="aa6e817b43e73414d8d9207fc1a3ee9fc"></a><a name="aa6e817b43e73414d8d9207fc1a3ee9fc"></a>Version</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><p id="a9334cfb209d64c8ea37b0d68bf5d34a2"><a name="a9334cfb209d64c8ea37b0d68bf5d34a2"></a><a name="a9334cfb209d64c8ea37b0d68bf5d34a2"></a>Currently, MRS 1.6.3, MRS 1.7.2, MRS 1.9.2, and MRS 2.1.0 are supported.</p>
</td>
</tr>
<tr id="r6144e644976b479a86047bcefe793c8a"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.3.1.1 "><p id="ac16550178799462ea759a53171a44ded"><a name="ac16550178799462ea759a53171a44ded"></a><a name="ac16550178799462ea759a53171a44ded"></a>Component</p>
</td>
<td class="cellrowborder" valign="top" width="80%" headers="mcps1.2.3.1.2 "><a name="ub1cf1cf2361e4c7b9323e3d82b9da2b3"></a><a name="ub1cf1cf2361e4c7b9323e3d82b9da2b3"></a><ul id="ub1cf1cf2361e4c7b9323e3d82b9da2b3"><li>MRS 1.6.3, MRS 1.7.2, MRS 1.9.2, and MRS 2.1.0 support the following components:<div class="p" id="ab58f9c8de0b4421d84ee8871f2421f73"><a name="ab58f9c8de0b4421d84ee8871f2421f73"></a><a name="ab58f9c8de0b4421d84ee8871f2421f73"></a>Components of an analysis cluster are as follows:<a name="u99b484d40af2401988ba8007a4e66786"></a><a name="u99b484d40af2401988ba8007a4e66786"></a><ul id="u99b484d40af2401988ba8007a4e66786"><li>Presto (Supported in MRS 2.1.0 or later)</li><li>Hadoop</li><li>Spark</li><li>HBase</li><li>OpenTSDB (Supported in MRS 1.9.2)</li><li>Hive</li><li>Tez</li><li>Hue</li><li>Loader</li><li>Flink (Supported in MRS 1.9.2 or later)</li><li>Alluxio (Supported in 1.9.2)</li><li>Ranger (Supported in MRS 1.9.2)</li></ul>
</div>
<div class="p" id="ab15063bdc69e4afe81fb8ed9e3119016"><a name="ab15063bdc69e4afe81fb8ed9e3119016"></a><a name="ab15063bdc69e4afe81fb8ed9e3119016"></a>Components of a streaming cluster are as follows:<a name="u23af1f95320b415085f2b9e173d175a5"></a><a name="u23af1f95320b415085f2b9e173d175a5"></a><ul id="u23af1f95320b415085f2b9e173d175a5"><li>Kafka</li><li>KafkaManager (Supported in MRS 1.9.2)</li><li>Storm</li><li>Flume</li></ul>
</div>
</li></ul>
</td>
</tr>
</tbody>
</table>

## URI<a name="s6021ea57b9ae43f096883a282a7c2d72"></a>

-   Format

    POST /v1.1/\{project\_id\}/run-job-flow

-   Parameter description

    **Table  2**  URI parameter description

    <a name="t47fe814870a44b5785f69a3b809579e9"></a>
    <table><thead align="left"><tr id="re9bbd9c922ba426989455a0ad002d5fa"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.4.1.1"><p id="a6ff125100aeb488ab3c691f6aebbe842"><a name="a6ff125100aeb488ab3c691f6aebbe842"></a><a name="a6ff125100aeb488ab3c691f6aebbe842"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="25%" id="mcps1.2.4.1.2"><p id="en-us_topic_0110581924_p141410194812"><a name="en-us_topic_0110581924_p141410194812"></a><a name="en-us_topic_0110581924_p141410194812"></a>Mandatory</p>
    </th>
    <th class="cellrowborder" valign="top" width="50%" id="mcps1.2.4.1.3"><p id="a356b6b93d49344c8bd18420f01efeb80"><a name="a356b6b93d49344c8bd18420f01efeb80"></a><a name="a356b6b93d49344c8bd18420f01efeb80"></a>Description</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="re0bbc7647af140e296dc427ad3a27834"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.1 "><p id="a06f652cb33d1470abf4b4075e646a0f1"><a name="a06f652cb33d1470abf4b4075e646a0f1"></a><a name="a06f652cb33d1470abf4b4075e646a0f1"></a>project_id</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.2 "><p id="a07565704d44b42bc9132dec65a94c293"><a name="a07565704d44b42bc9132dec65a94c293"></a><a name="a07565704d44b42bc9132dec65a94c293"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.4.1.3 "><p id="a035761cd241e41f89277fd848546a676"><a name="a035761cd241e41f89277fd848546a676"></a><a name="a035761cd241e41f89277fd848546a676"></a>Project ID. For details on how to obtain the project ID, see <a href="obtaining-a-project-id.md">Obtaining a Project ID</a>.</p>
    </td>
    </tr>
    </tbody>
    </table>


## Request<a name="s1a12826783b346baa5bdee496b666d24"></a>

**Table  3**  Request parameter description

<a name="t352e878f834349219bc14d236769d2dc"></a>
<table><thead align="left"><tr id="re983cdf247ec452f85b2bde422b984b9"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="a2a61b82bf43946429e79489ebaf3ff69"><a name="a2a61b82bf43946429e79489ebaf3ff69"></a><a name="a2a61b82bf43946429e79489ebaf3ff69"></a><strong id="b11838192435817"><a name="b11838192435817"></a><a name="b11838192435817"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="abb89a1c172364c0581c70ff6c18f10e5"><a name="abb89a1c172364c0581c70ff6c18f10e5"></a><a name="abb89a1c172364c0581c70ff6c18f10e5"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="en-us_topic_0110581924_p748325710328"><a name="en-us_topic_0110581924_p748325710328"></a><a name="en-us_topic_0110581924_p748325710328"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="en-us_topic_0110581924_p216409810328"><a name="en-us_topic_0110581924_p216409810328"></a><a name="en-us_topic_0110581924_p216409810328"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="rf33c21d0560547b187d77d486dac3e0b"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a83fcdfe345364ddcace3ab1b7f0ee7c4"><a name="a83fcdfe345364ddcace3ab1b7f0ee7c4"></a><a name="a83fcdfe345364ddcace3ab1b7f0ee7c4"></a>billing_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a2da384665ec94a12824d5456fe5f9f95"><a name="a2da384665ec94a12824d5456fe5f9f95"></a><a name="a2da384665ec94a12824d5456fe5f9f95"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a223d58355d174ae6a6512728e2e640cb"><a name="a223d58355d174ae6a6512728e2e640cb"></a><a name="a223d58355d174ae6a6512728e2e640cb"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p9774145225117"><a name="p9774145225117"></a><a name="p9774145225117"></a>Billing mode of a cluster. Set this parameter to <strong id="b1788128135318"><a name="b1788128135318"></a><a name="b1788128135318"></a>12</strong>.</p>
</td>
</tr>
<tr id="r73921e70517f428d9d95585c7e2ddc08"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p936958414737"><a name="en-us_topic_0110581924_p936958414737"></a><a name="en-us_topic_0110581924_p936958414737"></a>data_center</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a374f49fd04a24f6c946d9c283c8d3318"><a name="a374f49fd04a24f6c946d9c283c8d3318"></a><a name="a374f49fd04a24f6c946d9c283c8d3318"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p212377514737"><a name="en-us_topic_0110581924_p212377514737"></a><a name="en-us_topic_0110581924_p212377514737"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a2bf00699e5414e21a291d53979747d58"><a name="a2bf00699e5414e21a291d53979747d58"></a><a name="a2bf00699e5414e21a291d53979747d58"></a>Region of the cluster. For details, see <a href="https://docs.otc.t-systems.com/en-us/endpoint/index.html" target="_blank" rel="noopener noreferrer">Regions and Endpoints</a>.</p>
</td>
</tr>
<tr id="rcfd474d92b37404f9f0aa24daab8f6f8"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a5cd6eaa41149421b8f15b6688ca0764a"><a name="a5cd6eaa41149421b8f15b6688ca0764a"></a><a name="a5cd6eaa41149421b8f15b6688ca0764a"></a>master_node_num</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a43c8e1c6659944108270bdbcf063d2ce"><a name="a43c8e1c6659944108270bdbcf063d2ce"></a><a name="a43c8e1c6659944108270bdbcf063d2ce"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p653869210328"><a name="en-us_topic_0110581924_p653869210328"></a><a name="en-us_topic_0110581924_p653869210328"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ab2ae801eb5c8404ab5456c59376b0391"><a name="ab2ae801eb5c8404ab5456c59376b0391"></a><a name="ab2ae801eb5c8404ab5456c59376b0391"></a>Number of Master nodes. If cluster HA is enabled, set this parameter to 2. If cluster HA is disabled, set this parameter to 1.</p>
</td>
</tr>
<tr id="r9db971d872c7402b91a22aa647415195"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae0999bf207a74347965bccebfe21ea90"><a name="ae0999bf207a74347965bccebfe21ea90"></a><a name="ae0999bf207a74347965bccebfe21ea90"></a>master_node_size</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a3dad4ca7b7794bc1b11e1c03fcb6609c"><a name="a3dad4ca7b7794bc1b11e1c03fcb6609c"></a><a name="a3dad4ca7b7794bc1b11e1c03fcb6609c"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p491146010328"><a name="en-us_topic_0110581924_p491146010328"></a><a name="en-us_topic_0110581924_p491146010328"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ad01e9ad191694f6aa53b3afd86badcf4"><a name="ad01e9ad191694f6aa53b3afd86badcf4"></a><a name="ad01e9ad191694f6aa53b3afd86badcf4"></a>Instance specifications of the Master node, for example, c2.2xlarge.linux.mrs. MRS supports host specifications determined by CPU, memory, and disk space. For details about instance specifications, see <a href="ecs-specifications-used-by-mrs.md">ECS Specifications Used by MRS</a>.</p>
</td>
</tr>
<tr id="r877f6a982eac4bae8a0ef0205f1af67c"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="abe2bf31876ad4f4db597e02dfc065bdb"><a name="abe2bf31876ad4f4db597e02dfc065bdb"></a><a name="abe2bf31876ad4f4db597e02dfc065bdb"></a>core_node_num</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a435f76dfcc154f8aa0e7b300a72336bd"><a name="a435f76dfcc154f8aa0e7b300a72336bd"></a><a name="a435f76dfcc154f8aa0e7b300a72336bd"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a7b70a00e082c42b2b38f161d92711da8"><a name="a7b70a00e082c42b2b38f161d92711da8"></a><a name="a7b70a00e082c42b2b38f161d92711da8"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ae4f95d4370044afe845001e2973e694f"><a name="ae4f95d4370044afe845001e2973e694f"></a><a name="ae4f95d4370044afe845001e2973e694f"></a>Number of Core nodes </p>
<p id="abe34c5bef79040669b6ec20841f95737"><a name="abe34c5bef79040669b6ec20841f95737"></a><a name="abe34c5bef79040669b6ec20841f95737"></a>Value range: 1 to 500</p>
<p id="a3051b5639aad422fa5c90872e94086cd"><a name="a3051b5639aad422fa5c90872e94086cd"></a><a name="a3051b5639aad422fa5c90872e94086cd"></a>A maximum of 500 Core nodes are supported by default. If more than 500 Core nodes are required, contact technical support.</p>
</td>
</tr>
<tr id="r5ba4ec1743054256837995fe74814ead"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae12fdb14cc0844f79f0820c90d74291a"><a name="ae12fdb14cc0844f79f0820c90d74291a"></a><a name="ae12fdb14cc0844f79f0820c90d74291a"></a>core_node_size</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="afa6c2407288846a5943a7d12ea543d90"><a name="afa6c2407288846a5943a7d12ea543d90"></a><a name="afa6c2407288846a5943a7d12ea543d90"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="aa5272848817f4c65a9af69ac02779280"><a name="aa5272848817f4c65a9af69ac02779280"></a><a name="aa5272848817f4c65a9af69ac02779280"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a702e3567369646a4a0851f7b1b2312d4"><a name="a702e3567369646a4a0851f7b1b2312d4"></a><a name="a702e3567369646a4a0851f7b1b2312d4"></a>Instance specifications of the Core node, for example, c2.2xlarge.linux.mrs. </p>
</td>
</tr>
<tr id="r1238a19a3f9a4ee0806b59b44f1878e9"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aac716485e43246bb897da07516e358ed"><a name="aac716485e43246bb897da07516e358ed"></a><a name="aac716485e43246bb897da07516e358ed"></a>available_zone_id</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a4a9c8007119d4fd09cb935907b706cd0"><a name="a4a9c8007119d4fd09cb935907b706cd0"></a><a name="a4a9c8007119d4fd09cb935907b706cd0"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="ae1812b9ff8b44eb19fac110e339a9beb"><a name="ae1812b9ff8b44eb19fac110e339a9beb"></a><a name="ae1812b9ff8b44eb19fac110e339a9beb"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a8ed99a72a38f43f58e6c3c5c99c0b361"><a name="a8ed99a72a38f43f58e6c3c5c99c0b361"></a><a name="a8ed99a72a38f43f58e6c3c5c99c0b361"></a>AZ ID. For details, see <a href="https://docs.otc.t-systems.com/en-us/endpoint/index.html" target="_blank" rel="noopener noreferrer">Regions and Endpoints</a>.</p>
<a name="ul14495142818418"></a><a name="ul14495142818418"></a><ul id="ul14495142818418"><li>AZ1(eu-de-01):bf84aba586ce4e948da0b97d9a7d62fb</li><li>AZ2(eu-de-02):bf84aba586ce4e948da0b97d9a7d62fc</li></ul>
</td>
</tr>
<tr id="r6f024d769ed64c83ba896eac6166aead"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae2538261d74e439ebff18c3cbeb49f0a"><a name="ae2538261d74e439ebff18c3cbeb49f0a"></a><a name="ae2538261d74e439ebff18c3cbeb49f0a"></a>cluster_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a5620a97d17884f028fdb168d871808c3"><a name="a5620a97d17884f028fdb168d871808c3"></a><a name="a5620a97d17884f028fdb168d871808c3"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a3ca2ba599e8b4fc4b8cfe2bab0274488"><a name="a3ca2ba599e8b4fc4b8cfe2bab0274488"></a><a name="a3ca2ba599e8b4fc4b8cfe2bab0274488"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ab1b64ac2983342eab0fa713b22ad046b"><a name="ab1b64ac2983342eab0fa713b22ad046b"></a><a name="ab1b64ac2983342eab0fa713b22ad046b"></a>Cluster name. It must be unique. </p>
<p id="a8c13a43932644cd194446a3ddc9b4222"><a name="a8c13a43932644cd194446a3ddc9b4222"></a><a name="a8c13a43932644cd194446a3ddc9b4222"></a>It contains only 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.</p>
</td>
</tr>
<tr id="r8267e706522e4364b16a2a80b2d672a0"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p231175711111"><a name="en-us_topic_0110581924_p231175711111"></a><a name="en-us_topic_0110581924_p231175711111"></a>vpc</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ad9ec84dd494146488426063a3c368beb"><a name="ad9ec84dd494146488426063a3c368beb"></a><a name="ad9ec84dd494146488426063a3c368beb"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p83647611111"><a name="en-us_topic_0110581924_p83647611111"></a><a name="en-us_topic_0110581924_p83647611111"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p64570211111"><a name="en-us_topic_0110581924_p64570211111"></a><a name="en-us_topic_0110581924_p64570211111"></a>Name of the VPC where the subnet locates</p>
<p id="a57b6b4d149ce42609b1a777a8bc11456"><a name="a57b6b4d149ce42609b1a777a8bc11456"></a><a name="a57b6b4d149ce42609b1a777a8bc11456"></a>Perform the following operations to obtain the VPC name from the VPC management console:</p>
<a name="oa28c49c20dcf42e2a0b88dda52da437a"></a><a name="oa28c49c20dcf42e2a0b88dda52da437a"></a><ol id="oa28c49c20dcf42e2a0b88dda52da437a"><li>Log in to the management console.</li><li>Click <strong id="b871804817174"><a name="b871804817174"></a><a name="b871804817174"></a>Virtual Private Cloud</strong> and select <strong id="b69764531811"><a name="b69764531811"></a><a name="b69764531811"></a>Virtual Private Cloud</strong> from the left list.</li></ol>
<p id="en-us_topic_0110581924_p209150614269"><a name="en-us_topic_0110581924_p209150614269"></a><a name="en-us_topic_0110581924_p209150614269"></a>On the <strong id="b151095279183"><a name="b151095279183"></a><a name="b151095279183"></a>Virtual Private Cloud</strong> page, obtain the VPC name from the list.</p>
</td>
</tr>
<tr id="r24b572338f34482fa4dddeb126e76368"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a37a04c7bba1746118bbc8c3b6036abc7"><a name="a37a04c7bba1746118bbc8c3b6036abc7"></a><a name="a37a04c7bba1746118bbc8c3b6036abc7"></a>vpc_id</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a7b72e511b3384dd9b2948f04f52b0794"><a name="a7b72e511b3384dd9b2948f04f52b0794"></a><a name="a7b72e511b3384dd9b2948f04f52b0794"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a9fbde6a6735d49e29054cb15e33339be"><a name="a9fbde6a6735d49e29054cb15e33339be"></a><a name="a9fbde6a6735d49e29054cb15e33339be"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p19859110328"><a name="en-us_topic_0110581924_p19859110328"></a><a name="en-us_topic_0110581924_p19859110328"></a>ID of the VPC where the subnet locates</p>
<p id="a8f02b526cc0a4f5ba71ef6f5d50d76e5"><a name="a8f02b526cc0a4f5ba71ef6f5d50d76e5"></a><a name="a8f02b526cc0a4f5ba71ef6f5d50d76e5"></a>Perform the following operations to obtain the VPC ID from the VPC management console:</p>
<a name="o2461c8fa0af04786b2b17b0a9f6bc527"></a><a name="o2461c8fa0af04786b2b17b0a9f6bc527"></a><ol id="o2461c8fa0af04786b2b17b0a9f6bc527"><li>Log in to the management console.</li><li>Click <strong id="b370954616187"><a name="b370954616187"></a><a name="b370954616187"></a>Virtual Private Cloud</strong> and select <strong id="b1972414613182"><a name="b1972414613182"></a><a name="b1972414613182"></a>Virtual Private Cloud</strong> from the left list.</li></ol>
<p id="a666e64a589424e32a0648a91f67bbbaf"><a name="a666e64a589424e32a0648a91f67bbbaf"></a><a name="a666e64a589424e32a0648a91f67bbbaf"></a>On the <strong id="b94507484181"><a name="b94507484181"></a><a name="b94507484181"></a>Virtual Private Cloud</strong> page, obtain the VPC ID from the list.</p>
</td>
</tr>
<tr id="r21ff3099f24a43968cbd6e3846ba5dec"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ad0842a95be3c4969acf0d0e1e46f3cc7"><a name="ad0842a95be3c4969acf0d0e1e46f3cc7"></a><a name="ad0842a95be3c4969acf0d0e1e46f3cc7"></a>subnet_id</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a1dcf56a892544512ba995a27c1df21d0"><a name="a1dcf56a892544512ba995a27c1df21d0"></a><a name="a1dcf56a892544512ba995a27c1df21d0"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a92ad9320b5724220bfbf21da513583bf"><a name="a92ad9320b5724220bfbf21da513583bf"></a><a name="a92ad9320b5724220bfbf21da513583bf"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p90948410328"><a name="en-us_topic_0110581924_p90948410328"></a><a name="en-us_topic_0110581924_p90948410328"></a>Network ID</p>
<p id="a3b7712e151864723a8b155ceb8aa010b"><a name="a3b7712e151864723a8b155ceb8aa010b"></a><a name="a3b7712e151864723a8b155ceb8aa010b"></a>Perform the following operations to obtain the network ID of the VPC from the VPC management console:</p>
<a name="o08b882ea36524cb485f1fbe1815c2801"></a><a name="o08b882ea36524cb485f1fbe1815c2801"></a><ol id="o08b882ea36524cb485f1fbe1815c2801"><li>Log in to the management console.</li><li>Click <strong id="b1777052612215"><a name="b1777052612215"></a><a name="b1777052612215"></a>Virtual Private Cloud</strong> and select <strong id="b27716269215"><a name="b27716269215"></a><a name="b27716269215"></a>Virtual Private Cloud</strong> from the left list.</li></ol>
<p id="a89c751cf382443aab397f778503230c4"><a name="a89c751cf382443aab397f778503230c4"></a><a name="a89c751cf382443aab397f778503230c4"></a>On the <strong id="b149559284213"><a name="b149559284213"></a><a name="b149559284213"></a>Virtual Private Cloud</strong> page, obtain the network ID of the VPC from the list.</p>
</td>
</tr>
<tr id="rf9beb10a403b4466a3839b0488da39c8"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a6f6642bf68a640ae87b0ba27e6a98d26"><a name="a6f6642bf68a640ae87b0ba27e6a98d26"></a><a name="a6f6642bf68a640ae87b0ba27e6a98d26"></a>subnet_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a7a63abe0b83844a0b3dc5a62f542bedb"><a name="a7a63abe0b83844a0b3dc5a62f542bedb"></a><a name="a7a63abe0b83844a0b3dc5a62f542bedb"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="ace39838b445a44d4a1ac0872693d96e4"><a name="ace39838b445a44d4a1ac0872693d96e4"></a><a name="ace39838b445a44d4a1ac0872693d96e4"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a7fd95e18858c4aa1993e31d4a318722b"><a name="a7fd95e18858c4aa1993e31d4a318722b"></a><a name="a7fd95e18858c4aa1993e31d4a318722b"></a>Subnet name</p>
<p id="acffbf66d63104342af65d443a7c2535b"><a name="acffbf66d63104342af65d443a7c2535b"></a><a name="acffbf66d63104342af65d443a7c2535b"></a>Perform the following operations to obtain the subnet name from the VPC management console:</p>
<a name="en-us_topic_0110581924_ol66489142912"></a><a name="en-us_topic_0110581924_ol66489142912"></a><ol id="en-us_topic_0110581924_ol66489142912"><li>Log in to the management console.</li><li>Click <strong id="b19285111183219"><a name="b19285111183219"></a><a name="b19285111183219"></a>Virtual Private Cloud</strong> and select <strong id="b11286171118326"><a name="b11286171118326"></a><a name="b11286171118326"></a>Virtual Private Cloud</strong> from the left list.</li></ol>
<p id="a4a33d5804be0482da913a259fb838194"><a name="a4a33d5804be0482da913a259fb838194"></a><a name="a4a33d5804be0482da913a259fb838194"></a>On the <strong id="b1659413223320"><a name="b1659413223320"></a><a name="b1659413223320"></a>Virtual Private Cloud</strong> page, obtain the subnet name of the VPC from the list.</p>
</td>
</tr>
<tr id="r55e9f77ac29e4b65bc2ffce020dcb6ab"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p090158114114"><a name="en-us_topic_0110581924_p090158114114"></a><a name="en-us_topic_0110581924_p090158114114"></a>security_groups_id</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p39014815412"><a name="en-us_topic_0110581924_p39014815412"></a><a name="en-us_topic_0110581924_p39014815412"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="ac09e921f6e784a6d8d787efdac5ff221"><a name="ac09e921f6e784a6d8d787efdac5ff221"></a><a name="ac09e921f6e784a6d8d787efdac5ff221"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p655125052610"><a name="p655125052610"></a><a name="p655125052610"></a>Security group ID of the cluster </p>
<a name="ul81965217266"></a><a name="ul81965217266"></a><ul id="ul81965217266"><li>If this parameter is left blank, MRS automatically creates a security group, whose name starts with <strong id="b8759613193415"><a name="b8759613193415"></a><a name="b8759613193415"></a>mrs_{cluster_name}</strong>.</li><li>If this parameter is not left blank, a fixed security group is used to create a cluster. The transferred ID must be the security group ID owned by the current tenant. The security group must include an inbound rule in which all protocols and all ports are allowed and the source is the IP address of the specified node on the management plane.</li></ul>
</td>
</tr>
<tr id="r7f530a05ee7246e498acc21421f95981"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p759171819510"><a name="en-us_topic_0110581924_p759171819510"></a><a name="en-us_topic_0110581924_p759171819510"></a>tags</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p9591518958"><a name="en-us_topic_0110581924_p9591518958"></a><a name="en-us_topic_0110581924_p9591518958"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p959118458"><a name="en-us_topic_0110581924_p959118458"></a><a name="en-us_topic_0110581924_p959118458"></a>Array</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p185913183511"><a name="en-us_topic_0110581924_p185913183511"></a><a name="en-us_topic_0110581924_p185913183511"></a>Cluster tag</p>
<a name="ul126231909273"></a><a name="ul126231909273"></a><ul id="ul126231909273"><li>A cluster allows a maximum of 10 tags. A tag name (key) must be unique in a cluster.</li><li>A tag key or value cannot contain the following special characters: =*&lt;&gt;\,|/</li></ul>
</td>
</tr>
<tr id="ra6d0439a4ead42f29b3945d1d029a02b"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a60e886dd64c3490ebf4af986527c4a3f"><a name="a60e886dd64c3490ebf4af986527c4a3f"></a><a name="a60e886dd64c3490ebf4af986527c4a3f"></a>cluster_version</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p403882154628"><a name="en-us_topic_0110581924_p403882154628"></a><a name="en-us_topic_0110581924_p403882154628"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a6ac7ae7a1b24415c90f55556ea00d93e"><a name="a6ac7ae7a1b24415c90f55556ea00d93e"></a><a name="a6ac7ae7a1b24415c90f55556ea00d93e"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a03e4f05c48db4feab596857da020bed1"><a name="a03e4f05c48db4feab596857da020bed1"></a><a name="a03e4f05c48db4feab596857da020bed1"></a>Cluster version</p>
<p id="p201665831918"><a name="p201665831918"></a><a name="p201665831918"></a>Possible values are as follows:</p>
<a name="ul894116248197"></a><a name="ul894116248197"></a><ul id="ul894116248197"><li>MRS 1.6.3</li><li>MRS 1.7.2</li><li>MRS 1.9.2</li><li>MRS 2.1.0</li></ul>
</td>
</tr>
<tr id="rcc5a86cd3faf423db664babda2486802"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aa7d04691c05c4d748781407fcdefd9d2"><a name="aa7d04691c05c4d748781407fcdefd9d2"></a><a name="aa7d04691c05c4d748781407fcdefd9d2"></a>cluster_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aa1232053fe674087848851a56b436858"><a name="aa1232053fe674087848851a56b436858"></a><a name="aa1232053fe674087848851a56b436858"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="abc95826a36a44c03a6dea750f2cf289c"><a name="abc95826a36a44c03a6dea750f2cf289c"></a><a name="abc95826a36a44c03a6dea750f2cf289c"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a146b91e54fc349bbb5f324b965041189"><a name="a146b91e54fc349bbb5f324b965041189"></a><a name="a146b91e54fc349bbb5f324b965041189"></a>Cluster type</p>
<a name="u1e20920759264945bb30f2cfa746af30"></a><a name="u1e20920759264945bb30f2cfa746af30"></a><ul id="u1e20920759264945bb30f2cfa746af30"><li>0: analysis cluster</li><li>1: streaming cluster</li></ul>
<p id="ab03270ad58d74b27b9364c6dc1f187b8"><a name="ab03270ad58d74b27b9364c6dc1f187b8"></a><a name="ab03270ad58d74b27b9364c6dc1f187b8"></a>The default value is <strong id="b13598101354513"><a name="b13598101354513"></a><a name="b13598101354513"></a>0</strong>.</p>
<p id="p685974821918"><a name="p685974821918"></a><a name="p685974821918"></a>Note: Currently, hybrid clusters cannot be created using APIs.</p>
</td>
</tr>
<tr id="r3648604054654729b22f57bc1bbdc30b"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae44d1b265f134f71b6e61f1735d2c69f"><a name="ae44d1b265f134f71b6e61f1735d2c69f"></a><a name="ae44d1b265f134f71b6e61f1735d2c69f"></a>master_data_volume_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a5fd10cc3570a47ff88cee60405d48491"><a name="a5fd10cc3570a47ff88cee60405d48491"></a><a name="a5fd10cc3570a47ff88cee60405d48491"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="adb55e4760f5640ab902c6ac3d150dd6a"><a name="adb55e4760f5640ab902c6ac3d150dd6a"></a><a name="adb55e4760f5640ab902c6ac3d150dd6a"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="acc9bcc4411864783a083da1ed7f9ee17"><a name="acc9bcc4411864783a083da1ed7f9ee17"></a><a name="acc9bcc4411864783a083da1ed7f9ee17"></a>This parameter is a multi-disk parameter, indicating the data disk storage type of the Master node. Currently, SATA, SAS, and SSD are supported.</p>
</td>
</tr>
<tr id="r813218b5d09c48c1aa4c05011cde8fc3"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aadd2460a64ca43639f4e4438ff7bf2f4"><a name="aadd2460a64ca43639f4e4438ff7bf2f4"></a><a name="aadd2460a64ca43639f4e4438ff7bf2f4"></a>master_data_volume_size</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aa3a7e247ed354f94b041802e60778266"><a name="aa3a7e247ed354f94b041802e60778266"></a><a name="aa3a7e247ed354f94b041802e60778266"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="affe454d2af9346738267d1f837a5c0e1"><a name="affe454d2af9346738267d1f837a5c0e1"></a><a name="affe454d2af9346738267d1f837a5c0e1"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a5be89321ff3c4d969f8298e366696d99"><a name="a5be89321ff3c4d969f8298e366696d99"></a><a name="a5be89321ff3c4d969f8298e366696d99"></a>This parameter is a multi-disk parameter, indicating the data disk storage space of the Master node. To increase data storage capacity, you can add disks at the same time when creating a cluster.</p>
<p id="a6efed07980e5480b82a5eac9764441db"><a name="a6efed07980e5480b82a5eac9764441db"></a><a name="a6efed07980e5480b82a5eac9764441db"></a>Value range: 100 GB to 32,000 GB</p>
</td>
</tr>
<tr id="r94b50a753a1a496db0cdfd40caf20271"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a981882a6502848dfb5ca8a68e3dcfaa5"><a name="a981882a6502848dfb5ca8a68e3dcfaa5"></a><a name="a981882a6502848dfb5ca8a68e3dcfaa5"></a>master_data_volume_count</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a128dd5f655374031a730ff57b11e356e"><a name="a128dd5f655374031a730ff57b11e356e"></a><a name="a128dd5f655374031a730ff57b11e356e"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a275bbeb1cb7241f49ef5074df0fcd030"><a name="a275bbeb1cb7241f49ef5074df0fcd030"></a><a name="a275bbeb1cb7241f49ef5074df0fcd030"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="aa490089a63c94300b70d99031675ceae"><a name="aa490089a63c94300b70d99031675ceae"></a><a name="aa490089a63c94300b70d99031675ceae"></a>This parameter is a multi-disk parameter, indicating the number of data disks of the Master node.</p>
<p id="a78b76ca869b642498190fe852aeaca67"><a name="a78b76ca869b642498190fe852aeaca67"></a><a name="a78b76ca869b642498190fe852aeaca67"></a>The value can be set to <strong id="b842352706192224"><a name="b842352706192224"></a><a name="b842352706192224"></a>1</strong> only.</p>
</td>
</tr>
<tr id="r59c4a86e34534d9394f3e9f03c713a67"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae0cf8fe1bd144503a47d53ef6ca14720"><a name="ae0cf8fe1bd144503a47d53ef6ca14720"></a><a name="ae0cf8fe1bd144503a47d53ef6ca14720"></a>core_data_volume_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ac0e6be63960a46ebacbe856ba2aedc48"><a name="ac0e6be63960a46ebacbe856ba2aedc48"></a><a name="ac0e6be63960a46ebacbe856ba2aedc48"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a5ce5091c00714514964e01a370bc8402"><a name="a5ce5091c00714514964e01a370bc8402"></a><a name="a5ce5091c00714514964e01a370bc8402"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ab066d4c910c549c5b7f69daf1cf18af9"><a name="ab066d4c910c549c5b7f69daf1cf18af9"></a><a name="ab066d4c910c549c5b7f69daf1cf18af9"></a>This parameter is a multi-disk parameter, indicating the data disk storage type of the Core node. Currently, SATA, SAS, and SSD are supported.</p>
</td>
</tr>
<tr id="r61be420c5d5a40fe9f297c797759ec6a"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a641156512ce444eb84a96496b5ac5742"><a name="a641156512ce444eb84a96496b5ac5742"></a><a name="a641156512ce444eb84a96496b5ac5742"></a>core_data_volume_size</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a2e5e546ee52e4b4d8538d4e8626be538"><a name="a2e5e546ee52e4b4d8538d4e8626be538"></a><a name="a2e5e546ee52e4b4d8538d4e8626be538"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a7ab4e016bc384d058ddd4496186312d4"><a name="a7ab4e016bc384d058ddd4496186312d4"></a><a name="a7ab4e016bc384d058ddd4496186312d4"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a2460f861704b49a582c4bedf042de284"><a name="a2460f861704b49a582c4bedf042de284"></a><a name="a2460f861704b49a582c4bedf042de284"></a>This parameter is a multi-disk parameter, indicating the data disk storage space of the Core node. To increase data storage capacity, you can add disks at the same time when creating a cluster.</p>
<p id="a288229dd4a46414a828a607fab69a959"><a name="a288229dd4a46414a828a607fab69a959"></a><a name="a288229dd4a46414a828a607fab69a959"></a>Value range: 100 GB to 32,000 GB</p>
</td>
</tr>
<tr id="r63cb6f2991204b6c92914351a319f721"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a84ecd52b117a49bfbce623f486d95eea"><a name="a84ecd52b117a49bfbce623f486d95eea"></a><a name="a84ecd52b117a49bfbce623f486d95eea"></a>core_data_volume_count</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aa1a42c10290848a6a0bc398da74d7aee"><a name="aa1a42c10290848a6a0bc398da74d7aee"></a><a name="aa1a42c10290848a6a0bc398da74d7aee"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="aeb10a457f25b4b71b3e2e57eba6c4a2d"><a name="aeb10a457f25b4b71b3e2e57eba6c4a2d"></a><a name="aeb10a457f25b4b71b3e2e57eba6c4a2d"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a6dbfd4d4fe3044e6b18adb8731039c9e"><a name="a6dbfd4d4fe3044e6b18adb8731039c9e"></a><a name="a6dbfd4d4fe3044e6b18adb8731039c9e"></a>This parameter is a multi-disk parameter, indicating the number of data disks of the Core node.</p>
<p id="a14ff995c15fa470b9a7fcb6b02c9ebf3"><a name="a14ff995c15fa470b9a7fcb6b02c9ebf3"></a><a name="a14ff995c15fa470b9a7fcb6b02c9ebf3"></a>Value range: 1 to 10</p>
</td>
</tr>
<tr id="r6348f4c90bf94844aa100811f3c7b433"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a70c9f5fa400e4489a3d73ed8e49adeda"><a name="a70c9f5fa400e4489a3d73ed8e49adeda"></a><a name="a70c9f5fa400e4489a3d73ed8e49adeda"></a>volume_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aa86988cb9a074de7bae2a0f9a10e4ce1"><a name="aa86988cb9a074de7bae2a0f9a10e4ce1"></a><a name="aa86988cb9a074de7bae2a0f9a10e4ce1"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p394768110328"><a name="en-us_topic_0110581924_p394768110328"></a><a name="en-us_topic_0110581924_p394768110328"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p195029410529"><a name="p195029410529"></a><a name="p195029410529"></a>Data disk storage type of the Master and Core nodes. Currently, SATA, SAS, and SSD are supported. Disk parameters can be represented by <strong id="b294412501536"><a name="b294412501536"></a><a name="b294412501536"></a>volume_type</strong> and <strong id="b1440153125416"><a name="b1440153125416"></a><a name="b1440153125416"></a>volume_size</strong>, or multi-disk parameters. If the <strong id="b0691233175413"><a name="b0691233175413"></a><a name="b0691233175413"></a>volume_type</strong> and <strong id="b9209123795419"><a name="b9209123795419"></a><a name="b9209123795419"></a>volume_size</strong> parameters coexist with the multi-disk parameters, the system reads the <strong id="b1240116273557"><a name="b1240116273557"></a><a name="b1240116273557"></a>volume_type</strong> and <strong id="b49589302555"><a name="b49589302555"></a><a name="b49589302555"></a>volume_size</strong> parameters first. You are advised to use the multi-disk parameters.</p>
<a name="ua00ec6fb27414751bf2c5f846ca0612d"></a><a name="ua00ec6fb27414751bf2c5f846ca0612d"></a><ul id="ua00ec6fb27414751bf2c5f846ca0612d"><li>SATA: Common I/O</li><li>SAS: High I/O</li><li>SSD: Ultra-high I/O</li></ul>
</td>
</tr>
<tr id="re7e2ad9ec254419d860e5643684eeb56"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a01fb73e1669d4620ad2e5cc51234be13"><a name="a01fb73e1669d4620ad2e5cc51234be13"></a><a name="a01fb73e1669d4620ad2e5cc51234be13"></a>volume_size</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a5ee7cc2d2a064f6dab129749dba160c2"><a name="a5ee7cc2d2a064f6dab129749dba160c2"></a><a name="a5ee7cc2d2a064f6dab129749dba160c2"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a4bde3a89be5f4d359132a0b0f3d0a796"><a name="a4bde3a89be5f4d359132a0b0f3d0a796"></a><a name="a4bde3a89be5f4d359132a0b0f3d0a796"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="afd5319373a664eb190d7a8bdc5494422"><a name="afd5319373a664eb190d7a8bdc5494422"></a><a name="afd5319373a664eb190d7a8bdc5494422"></a>Data disk storage space of the Master and Core nodes. To increase data storage capacity, you can add disks at the same time when creating a cluster. Select a proper disk storage space based on the following application scenarios:</p>
<a name="u86560e592a8c444c9ca1267fc1f02d63"></a><a name="u86560e592a8c444c9ca1267fc1f02d63"></a><ul id="u86560e592a8c444c9ca1267fc1f02d63"><li>Separation of data storage and computing: Data is stored in the OBS system. Costs of clusters are relatively low but computing performance is poor. The clusters can be deleted at any time. It is recommended when data computing is infrequently performed.</li><li>Integration of data storage and computing: Data is stored in the HDFS system. Costs of clusters are relatively high but computing performance is good. The clusters cannot be deleted in a short term. It is recommended when data computing is frequently performed.</li></ul>
<p id="a1a0e7f05917e4ff2b4f891278c99e9f1"><a name="a1a0e7f05917e4ff2b4f891278c99e9f1"></a><a name="a1a0e7f05917e4ff2b4f891278c99e9f1"></a>Value range: 100 GB to 32,000 GB</p>
<p id="a5438c4ee7b2e4f0bbcc8c0f36301a58b"><a name="a5438c4ee7b2e4f0bbcc8c0f36301a58b"></a><a name="a5438c4ee7b2e4f0bbcc8c0f36301a58b"></a>This parameter is not recommended. For details, see the description of the <strong id="b1529113016017"><a name="b1529113016017"></a><a name="b1529113016017"></a>volume_type</strong> parameter.</p>
</td>
</tr>
<tr id="r8c1959f6c69c4e749d91c7a7c1303b1a"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a83df1e4195d5424683648236dc74aa41"><a name="a83df1e4195d5424683648236dc74aa41"></a><a name="a83df1e4195d5424683648236dc74aa41"></a>safe_mode</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="afd9a5e0d3d574ee59366353c09a0d1d5"><a name="afd9a5e0d3d574ee59366353c09a0d1d5"></a><a name="afd9a5e0d3d574ee59366353c09a0d1d5"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="afee6c1e47aa043ad80b1798a1e71cd39"><a name="afee6c1e47aa043ad80b1798a1e71cd39"></a><a name="afee6c1e47aa043ad80b1798a1e71cd39"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a3a3ca03d99ba4fe199b6c23c120164e2"><a name="a3a3ca03d99ba4fe199b6c23c120164e2"></a><a name="a3a3ca03d99ba4fe199b6c23c120164e2"></a>Running mode of an MRS cluster</p>
<a name="ubb9871076dcd44fb92ba967e206511b3"></a><a name="ubb9871076dcd44fb92ba967e206511b3"></a><ul id="ubb9871076dcd44fb92ba967e206511b3"><li>0: common cluster. In a common cluster, Kerberos authentication is disabled, and users can use all functions provided by the cluster.</li><li>1: security cluster. In a security cluster, Kerberos authentication is enabled, and common users cannot use the file management and job management functions of an MRS cluster or view cluster resource usage and the job records of Hadoop and Spark. To use these functions, the users must obtain the relevant permissions from the MRS Manager administrator.</li></ul>
<div class="note" id="note938717461375"><a name="note938717461375"></a><a name="note938717461375"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="p19518152191312"><a name="p19518152191312"></a><a name="p19518152191312"></a>For MRS 1.7.2 or earlier, the request body contains the <strong id="b99191967713"><a name="b99191967713"></a><a name="b99191967713"></a>cluster_admin_secret</strong> field only when <span class="parmname" id="parmname109202061717"><a name="parmname109202061717"></a><a name="parmname109202061717"></a><b>safe_mode</b></span> is set to <span class="parmvalue" id="parmvalue2092086971"><a name="parmvalue2092086971"></a><a name="parmvalue2092086971"></a><b>1</b></span>.</p>
</div></div>
</td>
</tr>
<tr id="r1c161bb47651479a892b1228fb2c6c24"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ab0fbedb070e3437cbc3dbcc5902574ea"><a name="ab0fbedb070e3437cbc3dbcc5902574ea"></a><a name="ab0fbedb070e3437cbc3dbcc5902574ea"></a>cluster_admin_secret</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a6a090963f52e4148b07a50a289689c7e"><a name="a6a090963f52e4148b07a50a289689c7e"></a><a name="a6a090963f52e4148b07a50a289689c7e"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a2875562d7ebf4667a3bab2f291bc70f2"><a name="a2875562d7ebf4667a3bab2f291bc70f2"></a><a name="a2875562d7ebf4667a3bab2f291bc70f2"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a87b16cda51ac40ce8d25df387256e4b5"><a name="a87b16cda51ac40ce8d25df387256e4b5"></a><a name="a87b16cda51ac40ce8d25df387256e4b5"></a>Password of the MRS Manager administrator</p>
<a name="u88ba71e55f4f48ada1d11d7b6c7e08ba"></a><a name="u88ba71e55f4f48ada1d11d7b6c7e08ba"></a><ul id="u88ba71e55f4f48ada1d11d7b6c7e08ba"><li>Must contain 8 to 32 characters.</li><li>Must contain at least three of the following:<a name="ufd001451aea440ac968e789c42558d99"></a><a name="ufd001451aea440ac968e789c42558d99"></a><ul id="ufd001451aea440ac968e789c42558d99"><li>Lowercase letters</li><li>Uppercase letters</li><li>Digits</li><li>Special characters: `~!@#$%^&amp;*()-_=+\|[{}];:'",&lt;.&gt;/?</li><li>Spaces</li></ul>
</li><li>Cannot be the username or the username spelled backwards.</li></ul>
<div class="note" id="note18568310123815"><a name="note18568310123815"></a><a name="note18568310123815"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="p972913610134"><a name="p972913610134"></a><a name="p972913610134"></a>For MRS 1.7.2 or earlier, this parameter is mandatory only when <span class="parmname" id="parmname2088912242718"><a name="parmname2088912242718"></a><a name="parmname2088912242718"></a><b>safe_mode</b></span> is set to <span class="parmvalue" id="parmvalue178898241279"><a name="parmvalue178898241279"></a><a name="parmvalue178898241279"></a><b>1</b></span>.</p>
</div></div>
</td>
</tr>
<tr id="row3407851141016"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aa1effddbb84243e990fe04b4ff430d9c"><a name="aa1effddbb84243e990fe04b4ff430d9c"></a><a name="aa1effddbb84243e990fe04b4ff430d9c"></a>node_public_cert_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a467154f22d3e4d7aacd5e864e5176639"><a name="a467154f22d3e4d7aacd5e864e5176639"></a><a name="a467154f22d3e4d7aacd5e864e5176639"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a9a65674559ad4407ab33ee1ee36f5b80"><a name="a9a65674559ad4407ab33ee1ee36f5b80"></a><a name="a9a65674559ad4407ab33ee1ee36f5b80"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ad6d0f114069448f3bc07f3310816d275"><a name="ad6d0f114069448f3bc07f3310816d275"></a><a name="ad6d0f114069448f3bc07f3310816d275"></a>Name of a key pair You can use a key pair to log in to the Master node in the cluster.</p>
</td>
</tr>
<tr id="rac82746e33e84b35be1dea6bf50d4093"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a0850f085eedf43e0b3b1db28acefdd2f"><a name="a0850f085eedf43e0b3b1db28acefdd2f"></a><a name="a0850f085eedf43e0b3b1db28acefdd2f"></a>log_collection</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ab0530a1ecdeb4c0bbec752b732cd96a9"><a name="ab0530a1ecdeb4c0bbec752b732cd96a9"></a><a name="ab0530a1ecdeb4c0bbec752b732cd96a9"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p866360175815"><a name="en-us_topic_0110581924_p866360175815"></a><a name="en-us_topic_0110581924_p866360175815"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="aa23b3e822680412e9be93ea7e2babc14"><a name="aa23b3e822680412e9be93ea7e2babc14"></a><a name="aa23b3e822680412e9be93ea7e2babc14"></a>Whether to collect logs when cluster creation fails</p>
<a name="u34c5777de77a452d9fda2b3813e7127b"></a><a name="u34c5777de77a452d9fda2b3813e7127b"></a><ul id="u34c5777de77a452d9fda2b3813e7127b"><li>0: Do not collect</li><li>1: Collect</li></ul>
<p id="a343eafaf494045edae28e20940d7acd0"><a name="a343eafaf494045edae28e20940d7acd0"></a><a name="a343eafaf494045edae28e20940d7acd0"></a>The default value is <strong id="b519217713712"><a name="b519217713712"></a><a name="b519217713712"></a>1</strong>, indicating that OBS buckets will be created and only used to collect logs that record MRS cluster creation failures.</p>
</td>
</tr>
<tr id="r75cebc827f60476b84139558aa5955f1"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ac0ed6b384a864d97bc857954b8a68bfa"><a name="ac0ed6b384a864d97bc857954b8a68bfa"></a><a name="ac0ed6b384a864d97bc857954b8a68bfa"></a>task_node_groups</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p171245311115"><a name="en-us_topic_0110581924_p171245311115"></a><a name="en-us_topic_0110581924_p171245311115"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p449097931115"><a name="en-us_topic_0110581924_p449097931115"></a><a name="en-us_topic_0110581924_p449097931115"></a>Array</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a41ca039424704ba6a3292f401709bf7d"><a name="a41ca039424704ba6a3292f401709bf7d"></a><a name="a41ca039424704ba6a3292f401709bf7d"></a>List of Task nodes For more parameter description, see <a href="#tc6bfa2a3d7a348d786a901f3a9327b50">Table 4</a>.</p>
</td>
</tr>
<tr id="r84186836086749f4bf05018f8e29636f"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a02894ad7eb84477f94217019a54d490c"><a name="a02894ad7eb84477f94217019a54d490c"></a><a name="a02894ad7eb84477f94217019a54d490c"></a>component_list</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a82d79867f08d4c6fbdb42856fe7717ab"><a name="a82d79867f08d4c6fbdb42856fe7717ab"></a><a name="a82d79867f08d4c6fbdb42856fe7717ab"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a41fabee86a5c41b6bd34548f78a1962e"><a name="a41fabee86a5c41b6bd34548f78a1962e"></a><a name="a41fabee86a5c41b6bd34548f78a1962e"></a>Array</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a04b1e6724ff84e4fa4d5db059774e9e2"><a name="a04b1e6724ff84e4fa4d5db059774e9e2"></a><a name="a04b1e6724ff84e4fa4d5db059774e9e2"></a>List of service components to be installed. For more parameter description, see <a href="#te1288dba79844d3fa5973939a3739d34">Table 5</a>.</p>
</td>
</tr>
<tr id="r9cd8370dd28049aabc1f1e3ac6289db2"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p511038810328"><a name="en-us_topic_0110581924_p511038810328"></a><a name="en-us_topic_0110581924_p511038810328"></a>add_jobs</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ac05fca7f28084bcaab1e0cfa3f467757"><a name="ac05fca7f28084bcaab1e0cfa3f467757"></a><a name="ac05fca7f28084bcaab1e0cfa3f467757"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a82ebf7cf79904c59bdb4cd7338d624e8"><a name="a82ebf7cf79904c59bdb4cd7338d624e8"></a><a name="a82ebf7cf79904c59bdb4cd7338d624e8"></a>Array</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="af6eb2690cf094db69403b3164682ce91"><a name="af6eb2690cf094db69403b3164682ce91"></a><a name="af6eb2690cf094db69403b3164682ce91"></a>Jobs can be submitted when a cluster is created. Currently, only one job can be created. For details about job parameters, see <a href="#t8ded0b3ae11742cea98a467ce26fd093">Table 6</a>.</p>
</td>
</tr>
<tr id="row1741144112371"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p144118412377"><a name="p144118412377"></a><a name="p144118412377"></a>bootstrap_scripts</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p1941194113370"><a name="p1941194113370"></a><a name="p1941194113370"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p241241133713"><a name="p241241133713"></a><a name="p241241133713"></a>Array</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p12412410370"><a name="p12412410370"></a><a name="p12412410370"></a>Bootstrap action script information. For more parameter description, see <a href="#table1258382865010">Table 13</a>.</p>
<p id="p1110620143419"><a name="p1110620143419"></a><a name="p1110620143419"></a>MRS 1.7.2 or later supports this parameter.</p>
</td>
</tr>
</tbody>
</table>

**Table  4** **task\_node\_groups**  parameter description

<a name="tc6bfa2a3d7a348d786a901f3a9327b50"></a>
<table><thead align="left"><tr id="r1a37300bb46a41338e703224fc485c99"><th class="cellrowborder" valign="top" width="24.97%" id="mcps1.2.5.1.1"><p id="a6eaa1791f3904b7dbe56de95fd33cd70"><a name="a6eaa1791f3904b7dbe56de95fd33cd70"></a><a name="a6eaa1791f3904b7dbe56de95fd33cd70"></a><strong id="b1531011183425"><a name="b1531011183425"></a><a name="b1531011183425"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15.040000000000001%" id="mcps1.2.5.1.2"><p id="ad9ae88673d734fbeb3d848c8f4bd5ad3"><a name="ad9ae88673d734fbeb3d848c8f4bd5ad3"></a><a name="ad9ae88673d734fbeb3d848c8f4bd5ad3"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15.09%" id="mcps1.2.5.1.3"><p id="a48532de540ed4ca3b8c7b46d4f6b5fb5"><a name="a48532de540ed4ca3b8c7b46d4f6b5fb5"></a><a name="a48532de540ed4ca3b8c7b46d4f6b5fb5"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="44.9%" id="mcps1.2.5.1.4"><p id="ade86233d865a4011b59fdf9de047c522"><a name="ade86233d865a4011b59fdf9de047c522"></a><a name="ade86233d865a4011b59fdf9de047c522"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r6fdb29bbcaef43ecbe866941289f39ed"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="a44eefa8cae2e4c7e83ee9809363e5702"><a name="a44eefa8cae2e4c7e83ee9809363e5702"></a><a name="a44eefa8cae2e4c7e83ee9809363e5702"></a>node_num</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="a9c724acc63d6415b90b1dfae03fe71fc"><a name="a9c724acc63d6415b90b1dfae03fe71fc"></a><a name="a9c724acc63d6415b90b1dfae03fe71fc"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="a020e74a5c3504133955c016ab7a42668"><a name="a020e74a5c3504133955c016ab7a42668"></a><a name="a020e74a5c3504133955c016ab7a42668"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="ab7629c14cf834c4a8b9c353eacff507a"><a name="ab7629c14cf834c4a8b9c353eacff507a"></a><a name="ab7629c14cf834c4a8b9c353eacff507a"></a>Number of Task nodes. The value ranges from 0 to 500 and the total number of Core and Task nodes cannot exceed 500.</p>
</td>
</tr>
<tr id="r47f8c9c293bb48d7918b5827b88c7db5"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p425651111412"><a name="en-us_topic_0110581924_p425651111412"></a><a name="en-us_topic_0110581924_p425651111412"></a>node_size</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p423278111181"><a name="en-us_topic_0110581924_p423278111181"></a><a name="en-us_topic_0110581924_p423278111181"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p60006581181"><a name="en-us_topic_0110581924_p60006581181"></a><a name="en-us_topic_0110581924_p60006581181"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="a44ae0aab454b4af299ddbbfeec3018b7"><a name="a44ae0aab454b4af299ddbbfeec3018b7"></a><a name="a44ae0aab454b4af299ddbbfeec3018b7"></a>Instance specifications of the Task node, for example, c2.2xlarge.linux.mrs. For details about instance specifications, see <a href="ecs-specifications-used-by-mrs.md">ECS Specifications Used by MRS</a>.</p>
</td>
</tr>
<tr id="rae832cc846e8455498d506478a4fc5b8"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="a0495e244c9a54419aa24d4b47e20aae3"><a name="a0495e244c9a54419aa24d4b47e20aae3"></a><a name="a0495e244c9a54419aa24d4b47e20aae3"></a>data_volume_type</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="af89499eb58014567969353a8c7d304f8"><a name="af89499eb58014567969353a8c7d304f8"></a><a name="af89499eb58014567969353a8c7d304f8"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="a5b28b65b252c4bfc8d4e0571ca2289fa"><a name="a5b28b65b252c4bfc8d4e0571ca2289fa"></a><a name="a5b28b65b252c4bfc8d4e0571ca2289fa"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="a183a26e0f49d4151bf35f7ebd5a150c1"><a name="a183a26e0f49d4151bf35f7ebd5a150c1"></a><a name="a183a26e0f49d4151bf35f7ebd5a150c1"></a>Data disk storage type of the Task node, supporting SATA, SAS, and SSD currently</p>
<a name="ud8f7e3414f904a0682bbf04c3c29150a"></a><a name="ud8f7e3414f904a0682bbf04c3c29150a"></a><ul id="ud8f7e3414f904a0682bbf04c3c29150a"><li>SATA: Common I/O</li><li>SAS: High I/O</li><li>SSD: Ultra-high I/O</li></ul>
</td>
</tr>
<tr id="r89c6b58511de4f68ba1ddb80c8e80201"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="ace81aa8fb01d4c1a8aa672a332025746"><a name="ace81aa8fb01d4c1a8aa672a332025746"></a><a name="ace81aa8fb01d4c1a8aa672a332025746"></a>data_volume_count</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="a67bedd11a0d243a0a2948a55a302e7f4"><a name="a67bedd11a0d243a0a2948a55a302e7f4"></a><a name="a67bedd11a0d243a0a2948a55a302e7f4"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="a8329a17977054c39948ba9ca80004a49"><a name="a8329a17977054c39948ba9ca80004a49"></a><a name="a8329a17977054c39948ba9ca80004a49"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="a6a790166ce0045558e8213954d7f8dc3"><a name="a6a790166ce0045558e8213954d7f8dc3"></a><a name="a6a790166ce0045558e8213954d7f8dc3"></a>Number of data disks of a Task node</p>
<p id="ac4db83a0e8814cfd82a6a511a6a59c7b"><a name="ac4db83a0e8814cfd82a6a511a6a59c7b"></a><a name="ac4db83a0e8814cfd82a6a511a6a59c7b"></a>Value range: 0 to 10</p>
</td>
</tr>
<tr id="r6c2cb46c21f34dc0ab0f420c9e95bbbb"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="af87d1b3fd56b48f798774318741daa6e"><a name="af87d1b3fd56b48f798774318741daa6e"></a><a name="af87d1b3fd56b48f798774318741daa6e"></a>data_volume_size</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="a929916ba39fb4dd7af6990d64f1c829d"><a name="a929916ba39fb4dd7af6990d64f1c829d"></a><a name="a929916ba39fb4dd7af6990d64f1c829d"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="a05ab66104ab84ffd888576762664ae99"><a name="a05ab66104ab84ffd888576762664ae99"></a><a name="a05ab66104ab84ffd888576762664ae99"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="a558efee3b7f647a2a0675c0778bd7f8e"><a name="a558efee3b7f647a2a0675c0778bd7f8e"></a><a name="a558efee3b7f647a2a0675c0778bd7f8e"></a>Data disk storage space of a Task node</p>
<p id="a021924d1b294426395ea4936c5df0db8"><a name="a021924d1b294426395ea4936c5df0db8"></a><a name="a021924d1b294426395ea4936c5df0db8"></a>Value range: 100 GB to 32,000 GB</p>
</td>
</tr>
<tr id="r50ca495e02254299996f171943f2b352"><td class="cellrowborder" valign="top" width="24.97%" headers="mcps1.2.5.1.1 "><p id="af4b059bb961e40b39e7ba868228df78b"><a name="af4b059bb961e40b39e7ba868228df78b"></a><a name="af4b059bb961e40b39e7ba868228df78b"></a>auto_scaling_policy</p>
</td>
<td class="cellrowborder" valign="top" width="15.040000000000001%" headers="mcps1.2.5.1.2 "><p id="a16abcedd8b6b4725a47c49b54fb20cb2"><a name="a16abcedd8b6b4725a47c49b54fb20cb2"></a><a name="a16abcedd8b6b4725a47c49b54fb20cb2"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15.09%" headers="mcps1.2.5.1.3 "><p id="a6d7594c328f043049239c2ef0a6ffbc1"><a name="a6d7594c328f043049239c2ef0a6ffbc1"></a><a name="a6d7594c328f043049239c2ef0a6ffbc1"></a>AutoScalingPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="44.9%" headers="mcps1.2.5.1.4 "><p id="a843f55e3857048b3822853a8d5c86cf6"><a name="a843f55e3857048b3822853a8d5c86cf6"></a><a name="a843f55e3857048b3822853a8d5c86cf6"></a>Auto scaling policy. For details, see <a href="#t6d6054a35d6342dc9dc5b3b8580fec7c">Table 7</a>.</p>
</td>
</tr>
</tbody>
</table>

**Table  5** **component\_list**  parameter description

<a name="te1288dba79844d3fa5973939a3739d34"></a>
<table><thead align="left"><tr id="r50261cf675f5482893037618d7f2fca2"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="aae2b73a196294c08bf748f7fcbd0d09e"><a name="aae2b73a196294c08bf748f7fcbd0d09e"></a><a name="aae2b73a196294c08bf748f7fcbd0d09e"></a><strong id="b3794184112451"><a name="b3794184112451"></a><a name="b3794184112451"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="a27798ab6d8fb4940b410e17062ab0e73"><a name="a27798ab6d8fb4940b410e17062ab0e73"></a><a name="a27798ab6d8fb4940b410e17062ab0e73"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="a86a363a84be649de92a4e67c3a3c813d"><a name="a86a363a84be649de92a4e67c3a3c813d"></a><a name="a86a363a84be649de92a4e67c3a3c813d"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="a53ef033dd69e4761b0f237689df0fb13"><a name="a53ef033dd69e4761b0f237689df0fb13"></a><a name="a53ef033dd69e4761b0f237689df0fb13"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r9fc416ea11cb4e5286c2a9386af0d21e"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a1da866fe310f4b24bef24d54814ab6d4"><a name="a1da866fe310f4b24bef24d54814ab6d4"></a><a name="a1da866fe310f4b24bef24d54814ab6d4"></a>component_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a22f706e02b144172b68c84984c2619ff"><a name="a22f706e02b144172b68c84984c2619ff"></a><a name="a22f706e02b144172b68c84984c2619ff"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a66088909406747b0a005daab84c645ff"><a name="a66088909406747b0a005daab84c645ff"></a><a name="a66088909406747b0a005daab84c645ff"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ae726ee1933c7444082ca0a0f18d3a463"><a name="ae726ee1933c7444082ca0a0f18d3a463"></a><a name="ae726ee1933c7444082ca0a0f18d3a463"></a>Component name</p>
<a name="ul4211784545"></a><a name="ul4211784545"></a><ul id="ul4211784545"><li>MRS 2.1.0 or later support the following components: Presto, Hadoop, Spark, HBase, Hive, Tez, Hue, Loader, Flink, Flume, Kafka, and Storm</li><li>MRS 1.9.2 supports the following components: Presto, Hadoop, Spark, HBase, OpenTSDB, Hive, Hue, Loader, Tez, Flink, Alluxio, Ranger, Flume, Kafka, KafkaManager, and Storm</li><li>MRS 1.7.2 and MRS 1.6.3 support the following components: Hadoop, Spark, HBase, Hive, Hue, Loader, Flume, Kafka, and Storm</li></ul>
</td>
</tr>
</tbody>
</table>

**Table  6** **add\_jobs**  parameter description

<a name="t8ded0b3ae11742cea98a467ce26fd093"></a>
<table><thead align="left"><tr id="r1406471483f44e598e5093114179e024"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="a11b4047a0dff4f028e4039ab650d8b53"><a name="a11b4047a0dff4f028e4039ab650d8b53"></a><a name="a11b4047a0dff4f028e4039ab650d8b53"></a><strong id="b689670115117"><a name="b689670115117"></a><a name="b689670115117"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="a2c3cfcf9d8214be9aa459fb5556232d8"><a name="a2c3cfcf9d8214be9aa459fb5556232d8"></a><a name="a2c3cfcf9d8214be9aa459fb5556232d8"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="a95ee1f9181e0433fa8e16c8796a9432f"><a name="a95ee1f9181e0433fa8e16c8796a9432f"></a><a name="a95ee1f9181e0433fa8e16c8796a9432f"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="a067577438c5947b888a4e71fcaaea88c"><a name="a067577438c5947b888a4e71fcaaea88c"></a><a name="a067577438c5947b888a4e71fcaaea88c"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r5f2c4162393343e1ba734ba5391b97ef"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a869331fce762494390ec8dc5e4a0ba82"><a name="a869331fce762494390ec8dc5e4a0ba82"></a><a name="a869331fce762494390ec8dc5e4a0ba82"></a>job_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ae231a7fd6f8543c0b9fa1f5c541016cf"><a name="ae231a7fd6f8543c0b9fa1f5c541016cf"></a><a name="ae231a7fd6f8543c0b9fa1f5c541016cf"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a6fdcaa9f137e4975a1c031c7f9e90c9f"><a name="a6fdcaa9f137e4975a1c031c7f9e90c9f"></a><a name="a6fdcaa9f137e4975a1c031c7f9e90c9f"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p336024810328"><a name="en-us_topic_0110581924_p336024810328"></a><a name="en-us_topic_0110581924_p336024810328"></a>Job type code</p>
<a name="u1bbe8e3884694971a9802247a68566f7"></a><a name="u1bbe8e3884694971a9802247a68566f7"></a><ul id="u1bbe8e3884694971a9802247a68566f7"><li>1: MapReduce</li><li>2: Spark</li><li>3: Hive Script</li><li>4: HiveQL (not supported currently)</li><li>5: DistCp, importing and exporting data (not supported currently)</li><li>6: Spark Script</li><li>7: Spark SQL, submitting Spark SQL statements (not supported currently).<div class="note" id="n0a1813ff8eb84d79a4b2f13af6d5a8a7"><a name="n0a1813ff8eb84d79a4b2f13af6d5a8a7"></a><a name="n0a1813ff8eb84d79a4b2f13af6d5a8a7"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="a244a862f23ea434e9723f1464f6a1ea0"><a name="a244a862f23ea434e9723f1464f6a1ea0"></a><a name="a244a862f23ea434e9723f1464f6a1ea0"></a>Spark and Hive jobs can be added to only clusters that include Spark and Hive components.</p>
</div></div>
</li></ul>
</td>
</tr>
<tr id="ra545977a99554f39be9d31a370f955f6"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p364797810328"><a name="en-us_topic_0110581924_p364797810328"></a><a name="en-us_topic_0110581924_p364797810328"></a>job_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ae9ec2aa05bc546b59f93bfebadb7cb2d"><a name="ae9ec2aa05bc546b59f93bfebadb7cb2d"></a><a name="ae9ec2aa05bc546b59f93bfebadb7cb2d"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="aedf5aa2a6956470f9c5513a81aadce02"><a name="aedf5aa2a6956470f9c5513a81aadce02"></a><a name="aedf5aa2a6956470f9c5513a81aadce02"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a03bb9947168d4aa48229842da6245f3f"><a name="a03bb9947168d4aa48229842da6245f3f"></a><a name="a03bb9947168d4aa48229842da6245f3f"></a>Job name. It contains 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.</p>
<div class="note" id="neab0e91a89844387a6d28e3383b1a591"><a name="neab0e91a89844387a6d28e3383b1a591"></a><a name="neab0e91a89844387a6d28e3383b1a591"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="a824e620530bd493bafaa3eec44e70778"><a name="a824e620530bd493bafaa3eec44e70778"></a><a name="a824e620530bd493bafaa3eec44e70778"></a>Identical job names are allowed but not recommended.</p>
</div></div>
</td>
</tr>
<tr id="ra1cb5f7d11664ec2b090c4bc92028564"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aae5cb8363c8d4ec696600e7394dcf09c"><a name="aae5cb8363c8d4ec696600e7394dcf09c"></a><a name="aae5cb8363c8d4ec696600e7394dcf09c"></a>jar_path</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p287569010328"><a name="en-us_topic_0110581924_p287569010328"></a><a name="en-us_topic_0110581924_p287569010328"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a24ef09ee03894d78a2c14fb60ef8a608"><a name="a24ef09ee03894d78a2c14fb60ef8a608"></a><a name="a24ef09ee03894d78a2c14fb60ef8a608"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p981695710328"><a name="en-us_topic_0110581924_p981695710328"></a><a name="en-us_topic_0110581924_p981695710328"></a>Path of the JAR or SQL file for program execution. The parameter must meet the following requirements:</p>
<a name="ue3629268b08343339d7421380a9d1653"></a><a name="ue3629268b08343339d7421380a9d1653"></a><ul id="ue3629268b08343339d7421380a9d1653"><li>Contains a maximum of 1,023 characters, excluding special characters such as ;|&amp;&gt;&lt;'$. The parameter value cannot be empty or full of spaces.</li><li>Files can be stored in HDFS or OBS. The path varies depending on the file system.<a name="en-us_topic_0110581924_ul56833471484"></a><a name="en-us_topic_0110581924_ul56833471484"></a><ul id="en-us_topic_0110581924_ul56833471484"><li>OBS: The path must start with <span class="parmvalue" id="p7addae73a6d04a3a8c9d93972ed6039d"><a name="p7addae73a6d04a3a8c9d93972ed6039d"></a><a name="p7addae73a6d04a3a8c9d93972ed6039d"></a><b>s3a://</b></span>. Files or programs encrypted by KMS are not supported.</li><li>HDFS: The path starts with <span class="parmvalue" id="pee15970daa044de1af6e19920c2672f4"><a name="pee15970daa044de1af6e19920c2672f4"></a><a name="pee15970daa044de1af6e19920c2672f4"></a><b>/</b></span>.</li></ul>
</li><li><span>Spark Script must end with </span><span class="parmvalue" id="p3f1c52d30e994432aa417b0b16e8191c"><a name="p3f1c52d30e994432aa417b0b16e8191c"></a><a name="p3f1c52d30e994432aa417b0b16e8191c"></a><b>.sql</b></span><span> while MapReduce and Spark Jar must end with </span><span class="parmvalue" id="pd88ebb6bea614a6098ff4c46567c4c0f"><a name="pd88ebb6bea614a6098ff4c46567c4c0f"></a><a name="pd88ebb6bea614a6098ff4c46567c4c0f"></a><b>.jar</b></span><span>. </span><span class="parmvalue" id="parmvalue10319175814292"><a name="parmvalue10319175814292"></a><a name="parmvalue10319175814292"></a><b>sql</b></span><span> and </span><span class="parmvalue" id="parmvalue1128641253013"><a name="parmvalue1128641253013"></a><a name="parmvalue1128641253013"></a><b>jar</b></span><span> are case-insensitive.</span></li></ul>
</td>
</tr>
<tr id="r082bccdc7c1b41c08a362fe9b2f23e57"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a4d4f374e54b64a1984e759a3b582cae6"><a name="a4d4f374e54b64a1984e759a3b582cae6"></a><a name="a4d4f374e54b64a1984e759a3b582cae6"></a>arguments</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a7a8ba8615e6140be94c7df4a296f5d1e"><a name="a7a8ba8615e6140be94c7df4a296f5d1e"></a><a name="a7a8ba8615e6140be94c7df4a296f5d1e"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a8b482a914e9b48d9a5e09baa2ea33018"><a name="a8b482a914e9b48d9a5e09baa2ea33018"></a><a name="a8b482a914e9b48d9a5e09baa2ea33018"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a56f54fd58b7f4a88a78b3301118e358c"><a name="a56f54fd58b7f4a88a78b3301118e358c"></a><a name="a56f54fd58b7f4a88a78b3301118e358c"></a>Key parameter for program execution. The parameter is specified by the function of the user's program. MRS is only responsible for loading the parameter.</p>
<p id="af260bc2d789a4ffd9a801b2c388937d6"><a name="af260bc2d789a4ffd9a801b2c388937d6"></a><a name="af260bc2d789a4ffd9a801b2c388937d6"></a>The parameter contains a maximum of 2,047 characters, excluding special characters such as ;|&amp;&gt;'&lt;$, and can be left blank.</p>
</td>
</tr>
<tr id="r5f76a1c980b945b6b9be2112c853032a"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a240ef0ea4fa14fd8b4ff5ef66cc651cd"><a name="a240ef0ea4fa14fd8b4ff5ef66cc651cd"></a><a name="a240ef0ea4fa14fd8b4ff5ef66cc651cd"></a>input</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a87f3a222d7404447a6b2f856cc1d6b8f"><a name="a87f3a222d7404447a6b2f856cc1d6b8f"></a><a name="a87f3a222d7404447a6b2f856cc1d6b8f"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p644882010328"><a name="en-us_topic_0110581924_p644882010328"></a><a name="en-us_topic_0110581924_p644882010328"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ae66710c5e07e45e4b7fad4d8994760c3"><a name="ae66710c5e07e45e4b7fad4d8994760c3"></a><a name="ae66710c5e07e45e4b7fad4d8994760c3"></a>Address for inputting data.</p>
<div class="p" id="ae71baaff5e234d8d8f871af7142086c7"><a name="ae71baaff5e234d8d8f871af7142086c7"></a><a name="ae71baaff5e234d8d8f871af7142086c7"></a>Files can be stored in HDFS or OBS. The path varies depending on the file system.<a name="u053b159914fc4cdb9238d81925d0ad3c"></a><a name="u053b159914fc4cdb9238d81925d0ad3c"></a><ul id="u053b159914fc4cdb9238d81925d0ad3c"><li>OBS: The path must start with <span class="parmvalue" id="parmvalue47194518336"><a name="parmvalue47194518336"></a><a name="parmvalue47194518336"></a><b>s3a://</b></span>. Files or programs encrypted by KMS are not supported.</li><li>HDFS: The path starts with <span class="parmvalue" id="parmvalue64431648153315"><a name="parmvalue64431648153315"></a><a name="parmvalue64431648153315"></a><b>/</b></span>.</li></ul>
</div>
<p id="aa83c637c498e4208a3c21310dcfeac38"><a name="aa83c637c498e4208a3c21310dcfeac38"></a><a name="aa83c637c498e4208a3c21310dcfeac38"></a>The parameter contains a maximum of 1,023 characters, excluding special characters such as ;|&amp;&gt;'&lt;$, and can be left blank.</p>
</td>
</tr>
<tr id="r19caa026be7644ec89853f511ff24e57"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aa7416d43efd149b1aaae01e2393dfd71"><a name="aa7416d43efd149b1aaae01e2393dfd71"></a><a name="aa7416d43efd149b1aaae01e2393dfd71"></a>output</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a4467222d621049c2a7dd6d69c153dc57"><a name="a4467222d621049c2a7dd6d69c153dc57"></a><a name="a4467222d621049c2a7dd6d69c153dc57"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a1ec06fa96d674b538557ba325057b2ca"><a name="a1ec06fa96d674b538557ba325057b2ca"></a><a name="a1ec06fa96d674b538557ba325057b2ca"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a68624f7985ca4999a15ed56e5ba239a5"><a name="a68624f7985ca4999a15ed56e5ba239a5"></a><a name="a68624f7985ca4999a15ed56e5ba239a5"></a>Address for outputting data.</p>
<div class="p" id="aff5a969c034940bc8f5595975c93727d"><a name="aff5a969c034940bc8f5595975c93727d"></a><a name="aff5a969c034940bc8f5595975c93727d"></a>Files can be stored in HDFS or OBS. The path varies depending on the file system.<a name="u567ba92ca6ce4526a8fbe7559d415c73"></a><a name="u567ba92ca6ce4526a8fbe7559d415c73"></a><ul id="u567ba92ca6ce4526a8fbe7559d415c73"><li>OBS: The path must start with <span class="parmvalue" id="parmvalue12220717153416"><a name="parmvalue12220717153416"></a><a name="parmvalue12220717153416"></a><b>s3a://</b></span>.</li><li>HDFS: The path starts with <span class="parmvalue" id="parmvalue11408191820343"><a name="parmvalue11408191820343"></a><a name="parmvalue11408191820343"></a><b>/</b></span>.</li></ul>
</div>
<p id="a1ea20927905f4d98ab025e6c139a6e49"><a name="a1ea20927905f4d98ab025e6c139a6e49"></a><a name="a1ea20927905f4d98ab025e6c139a6e49"></a>If the specified path does not exist, the system will automatically create it.</p>
<p id="a33780072c5ca4afb805b553183081a0a"><a name="a33780072c5ca4afb805b553183081a0a"></a><a name="a33780072c5ca4afb805b553183081a0a"></a>The parameter contains a maximum of 1,023 characters, excluding special characters such as ;|&amp;&gt;'&lt;$, and can be left blank.</p>
</td>
</tr>
<tr id="rcebde39651a34a3ebc0e383b3ea0609e"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="afba4723d32e64349a2fd483d3aec7f8e"><a name="afba4723d32e64349a2fd483d3aec7f8e"></a><a name="afba4723d32e64349a2fd483d3aec7f8e"></a>job_log</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="abf09aba3956248b0bcad4eaf18c1ffe3"><a name="abf09aba3956248b0bcad4eaf18c1ffe3"></a><a name="abf09aba3956248b0bcad4eaf18c1ffe3"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a786558e005ef4409998180f06d9e8854"><a name="a786558e005ef4409998180f06d9e8854"></a><a name="a786558e005ef4409998180f06d9e8854"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0110581924_p34006410328"><a name="en-us_topic_0110581924_p34006410328"></a><a name="en-us_topic_0110581924_p34006410328"></a>Path for storing job logs that record job running status.</p>
<div class="p" id="a197b22cd360f41029e4986c7631e13e9"><a name="a197b22cd360f41029e4986c7631e13e9"></a><a name="a197b22cd360f41029e4986c7631e13e9"></a>Files can be stored in HDFS or OBS. The path varies depending on the file system.<a name="u59cddc2a224b4316addc8c265b5d4e7a"></a><a name="u59cddc2a224b4316addc8c265b5d4e7a"></a><ul id="u59cddc2a224b4316addc8c265b5d4e7a"><li>OBS: The path must start with <span class="parmvalue" id="parmvalue1855113063611"><a name="parmvalue1855113063611"></a><a name="parmvalue1855113063611"></a><b>s3a://</b></span>.</li><li>HDFS: The path starts with <span class="parmvalue" id="parmvalue1992183133620"><a name="parmvalue1992183133620"></a><a name="parmvalue1992183133620"></a><b>/</b></span>.</li></ul>
</div>
<p id="a57d5612e81ab4daa9fcba35202cc2ac6"><a name="a57d5612e81ab4daa9fcba35202cc2ac6"></a><a name="a57d5612e81ab4daa9fcba35202cc2ac6"></a>The parameter contains a maximum of 1,023 characters, excluding special characters such as ;|&amp;&gt;'&lt;$, and can be left blank.</p>
</td>
</tr>
<tr id="r71b3a4b056fa4a6693ee1ccbf01354e3"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a6180a48948304eebafb48522459c400f"><a name="a6180a48948304eebafb48522459c400f"></a><a name="a6180a48948304eebafb48522459c400f"></a>shutdown_cluster</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0110581924_p78350310328"><a name="en-us_topic_0110581924_p78350310328"></a><a name="en-us_topic_0110581924_p78350310328"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a24e8cde5f6804c39bb85af587a53ac88"><a name="a24e8cde5f6804c39bb85af587a53ac88"></a><a name="a24e8cde5f6804c39bb85af587a53ac88"></a>Bool</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a24011056348d4e08bf19f8cf13770fd5"><a name="a24011056348d4e08bf19f8cf13770fd5"></a><a name="a24011056348d4e08bf19f8cf13770fd5"></a>Whether to delete the cluster after the job execution is complete</p>
<a name="u283ed191b20545218c2495ce20019235"></a><a name="u283ed191b20545218c2495ce20019235"></a><ul id="u283ed191b20545218c2495ce20019235"><li>true: Yes</li><li>false: No</li></ul>
</td>
</tr>
<tr id="r38c9b7d97d1843818d8257e369625b5e"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a211ab5a8d91a4e179e47355dbb7154e9"><a name="a211ab5a8d91a4e179e47355dbb7154e9"></a><a name="a211ab5a8d91a4e179e47355dbb7154e9"></a>file_action</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a4daebfd86bbd407788ddd47e28aaa3ab"><a name="a4daebfd86bbd407788ddd47e28aaa3ab"></a><a name="a4daebfd86bbd407788ddd47e28aaa3ab"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a2f6ecf2eae4143edb7a98c02ad86e627"><a name="a2f6ecf2eae4143edb7a98c02ad86e627"></a><a name="a2f6ecf2eae4143edb7a98c02ad86e627"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a6337ab64727c4932a880bbd30cee64c6"><a name="a6337ab64727c4932a880bbd30cee64c6"></a><a name="a6337ab64727c4932a880bbd30cee64c6"></a>Data import and export</p>
<a name="ubd8933d2af864220afae2e8a2fe1f8db"></a><a name="ubd8933d2af864220afae2e8a2fe1f8db"></a><ul id="ubd8933d2af864220afae2e8a2fe1f8db"><li>import</li><li>export</li></ul>
</td>
</tr>
<tr id="r3c17d75523474f6db92ef448256836f0"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a1efac31efc0848f4b563366ce3605f32"><a name="a1efac31efc0848f4b563366ce3605f32"></a><a name="a1efac31efc0848f4b563366ce3605f32"></a>submit_job_once_cluster_run</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a17d13126934042558ea30306f971ec9c"><a name="a17d13126934042558ea30306f971ec9c"></a><a name="a17d13126934042558ea30306f971ec9c"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a39048ed76bbe4a93abedc722a7bd9c1f"><a name="a39048ed76bbe4a93abedc722a7bd9c1f"></a><a name="a39048ed76bbe4a93abedc722a7bd9c1f"></a>Bool</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><a name="u252aadfb54da4baaa43f5c40ec014fc0"></a><a name="u252aadfb54da4baaa43f5c40ec014fc0"></a><ul id="u252aadfb54da4baaa43f5c40ec014fc0"><li>true: Submit a job during cluster creation.</li><li>false: Submit a job after the cluster is created.</li></ul>
<p id="en-us_topic_0110581924_p461478810328"><a name="en-us_topic_0110581924_p461478810328"></a><a name="en-us_topic_0110581924_p461478810328"></a>Set this parameter to <strong id="b84235270695121"><a name="b84235270695121"></a><a name="b84235270695121"></a>true</strong> in this example.</p>
</td>
</tr>
<tr id="r1bd160512f794dc1b8a5e74830dd8a77"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0110581924_p873773110328"><a name="en-us_topic_0110581924_p873773110328"></a><a name="en-us_topic_0110581924_p873773110328"></a>hql</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a39913072b23344fdb036976d9691218f"><a name="a39913072b23344fdb036976d9691218f"></a><a name="a39913072b23344fdb036976d9691218f"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a46d625ddf92f47db9e977423ea813e93"><a name="a46d625ddf92f47db9e977423ea813e93"></a><a name="a46d625ddf92f47db9e977423ea813e93"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ac34bbce1af534068b6f90c07b819940e"><a name="ac34bbce1af534068b6f90c07b819940e"></a><a name="ac34bbce1af534068b6f90c07b819940e"></a>HiveQL statement</p>
</td>
</tr>
<tr id="rfd31d8bc4ed144509d335fbaa00187ad"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ae4877c908b65427f8e6b13547916aaa9"><a name="ae4877c908b65427f8e6b13547916aaa9"></a><a name="ae4877c908b65427f8e6b13547916aaa9"></a>hive_script_path</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ad5e9d85fc0eb467c851e6a1caada5571"><a name="ad5e9d85fc0eb467c851e6a1caada5571"></a><a name="ad5e9d85fc0eb467c851e6a1caada5571"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a154c57b5b1b647da9292441acf1e672a"><a name="a154c57b5b1b647da9292441acf1e672a"></a><a name="a154c57b5b1b647da9292441acf1e672a"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="aee167b6ea6fa4d72ae3dd62da9118e1d"><a name="aee167b6ea6fa4d72ae3dd62da9118e1d"></a><a name="aee167b6ea6fa4d72ae3dd62da9118e1d"></a>SQL program path. This parameter is needed by Spark Script and Hive Script jobs only, and must meet the following requirements:</p>
<a name="u9852e5488841460c9a61db547eec1126"></a><a name="u9852e5488841460c9a61db547eec1126"></a><ul id="u9852e5488841460c9a61db547eec1126"><li>Contains a maximum of 1,023 characters, excluding special characters such as ;|&amp;&gt;&lt;'$. The parameter value cannot be empty or full of spaces.</li><li>Files can be stored in HDFS or OBS. The path varies depending on the file system.<a name="u057d8e72682642968fa26aff11564901"></a><a name="u057d8e72682642968fa26aff11564901"></a><ul id="u057d8e72682642968fa26aff11564901"><li>OBS: The path must start with <span class="parmvalue" id="parmvalue8998418471"><a name="parmvalue8998418471"></a><a name="parmvalue8998418471"></a><b>s3a://</b></span>. Files or programs encrypted by KMS are not supported.</li><li>HDFS: The path starts with <span class="parmvalue" id="parmvalue08242411474"><a name="parmvalue08242411474"></a><a name="parmvalue08242411474"></a><b>/</b></span>.</li></ul>
</li><li><span>Ends with </span><span class="parmvalue" id="ped754121c03f48188a0dc13d9fe665ae"><a name="ped754121c03f48188a0dc13d9fe665ae"></a><a name="ped754121c03f48188a0dc13d9fe665ae"></a><b>.sql</b></span><span>. </span><strong id="b131626419487"><a name="b131626419487"></a><a name="b131626419487"></a>sql</strong><span> is case-insensitive.</span></li></ul>
</td>
</tr>
</tbody>
</table>

**Table  7** **auto\_scaling\_policy**  parameter description

<a name="t6d6054a35d6342dc9dc5b3b8580fec7c"></a>
<table><thead align="left"><tr id="raf51026a1f504a8788e1403658120f2f"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="a6b57643863a6437a8c107916b9c7695d"><a name="a6b57643863a6437a8c107916b9c7695d"></a><a name="a6b57643863a6437a8c107916b9c7695d"></a><strong id="b1784095713486"><a name="b1784095713486"></a><a name="b1784095713486"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="a3fff5ea955e54459addfcbbb35b643ec"><a name="a3fff5ea955e54459addfcbbb35b643ec"></a><a name="a3fff5ea955e54459addfcbbb35b643ec"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="aa1457e2336bd448ea6d9616e20227777"><a name="aa1457e2336bd448ea6d9616e20227777"></a><a name="aa1457e2336bd448ea6d9616e20227777"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="a5321d724cd884c23b9ae748f98ba4424"><a name="a5321d724cd884c23b9ae748f98ba4424"></a><a name="a5321d724cd884c23b9ae748f98ba4424"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="ra90fcd7439104b2c98d8b7081bfdef71"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a8e70a35d4222449cb92a4041ef7f0137"><a name="a8e70a35d4222449cb92a4041ef7f0137"></a><a name="a8e70a35d4222449cb92a4041ef7f0137"></a>auto_scaling_enable</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ae90c66ff525b4f18b199fba818fcc23e"><a name="ae90c66ff525b4f18b199fba818fcc23e"></a><a name="ae90c66ff525b4f18b199fba818fcc23e"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a2c10267f0ea74faba0b9fb771d478e67"><a name="a2c10267f0ea74faba0b9fb771d478e67"></a><a name="a2c10267f0ea74faba0b9fb771d478e67"></a>Boolean</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a8b16bd6c0885436e8051b80f0aea7c8d"><a name="a8b16bd6c0885436e8051b80f0aea7c8d"></a><a name="a8b16bd6c0885436e8051b80f0aea7c8d"></a>Whether to enable the auto scaling rule</p>
</td>
</tr>
<tr id="r1fe6b7d60f7345d3b8d1c1d8cb8806bd"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a379d490f2095437fad3072496b931b39"><a name="a379d490f2095437fad3072496b931b39"></a><a name="a379d490f2095437fad3072496b931b39"></a>min_capacity</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a67bf7a6b811a47d1accfd408095436fb"><a name="a67bf7a6b811a47d1accfd408095436fb"></a><a name="a67bf7a6b811a47d1accfd408095436fb"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0110581924_p230787112654"><a name="en-us_topic_0110581924_p230787112654"></a><a name="en-us_topic_0110581924_p230787112654"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a6339dac619fd4e838c5285c78f3162f9"><a name="a6339dac619fd4e838c5285c78f3162f9"></a><a name="a6339dac619fd4e838c5285c78f3162f9"></a>Minimum number of nodes left in the node group</p>
<p id="ac2a776ad7e134fadb625996c4d1d83d6"><a name="ac2a776ad7e134fadb625996c4d1d83d6"></a><a name="ac2a776ad7e134fadb625996c4d1d83d6"></a>Value range: 0 to 500</p>
</td>
</tr>
<tr id="r8b569e44ff74496d9a7eb20ac8a742e4"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a7eaed7f858d7454b8c65783319c39b04"><a name="a7eaed7f858d7454b8c65783319c39b04"></a><a name="a7eaed7f858d7454b8c65783319c39b04"></a>max_capacity</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a67bf8fb9a84542bd8757eeb97a31418f"><a name="a67bf8fb9a84542bd8757eeb97a31418f"></a><a name="a67bf8fb9a84542bd8757eeb97a31418f"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a3ecf064ee466445781aeb1a335395cba"><a name="a3ecf064ee466445781aeb1a335395cba"></a><a name="a3ecf064ee466445781aeb1a335395cba"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a27bf42b5a44f47378f54aad66fef804f"><a name="a27bf42b5a44f47378f54aad66fef804f"></a><a name="a27bf42b5a44f47378f54aad66fef804f"></a>Maximum number of nodes in the node group</p>
<p id="a480eee70830e4129964adad7def22b88"><a name="a480eee70830e4129964adad7def22b88"></a><a name="a480eee70830e4129964adad7def22b88"></a>Value range: 0 to 500</p>
</td>
</tr>
<tr id="row109862440157"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p99881444155"><a name="p99881444155"></a><a name="p99881444155"></a>resources_plans</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p1998854481510"><a name="p1998854481510"></a><a name="p1998854481510"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p59886442157"><a name="p59886442157"></a><a name="p59886442157"></a>List</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p189881644171514"><a name="p189881644171514"></a><a name="p189881644171514"></a>Resource plan list. For details, see <a href="#table10281451162111">Table 8</a>. If this parameter is left blank, the resource plan is disabled.</p>
<p id="p9402141913220"><a name="p9402141913220"></a><a name="p9402141913220"></a>When auto scaling is enabled, either a resource plan or an auto scaling rule must be configured.</p>
<p id="p332510443181"><a name="p332510443181"></a><a name="p332510443181"></a>MRS 1.6.3 or later supports this parameter.</p>
</td>
</tr>
<tr id="row36011313174"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p337232320178"><a name="p337232320178"></a><a name="p337232320178"></a>exec_scripts</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p337220231170"><a name="p337220231170"></a><a name="p337220231170"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p11372152341713"><a name="p11372152341713"></a><a name="p11372152341713"></a>List</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p93729233178"><a name="p93729233178"></a><a name="p93729233178"></a>List of custom scaling automation scripts. For details, see <a href="#table1921110172216">Table 9</a>. If this parameter is left blank, a hook script is disabled.</p>
<p id="p03726234173"><a name="p03726234173"></a><a name="p03726234173"></a>MRS 1.7.2 or later supports this parameter.</p>
</td>
</tr>
<tr id="r4755a3babff849968d83bd43129dc7eb"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a308e43c85e40439b8c59d08440843dc6"><a name="a308e43c85e40439b8c59d08440843dc6"></a><a name="a308e43c85e40439b8c59d08440843dc6"></a>rules</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a98d5257b9540482989b03783ec10a561"><a name="a98d5257b9540482989b03783ec10a561"></a><a name="a98d5257b9540482989b03783ec10a561"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="ae314628f2d8a4766924313079bbabe68"><a name="ae314628f2d8a4766924313079bbabe68"></a><a name="ae314628f2d8a4766924313079bbabe68"></a>List</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="ac2e02b36ba1e434fb0df7479bd8acd50"><a name="ac2e02b36ba1e434fb0df7479bd8acd50"></a><a name="ac2e02b36ba1e434fb0df7479bd8acd50"></a>List of auto scaling rules. For details, see <a href="#t4c9e3e169631470d81d260543affb7e1">Table 10</a>.</p>
<p id="p6516143522217"><a name="p6516143522217"></a><a name="p6516143522217"></a>When auto scaling is enabled, either a resource plan or an auto scaling rule must be configured.</p>
</td>
</tr>
</tbody>
</table>

**Table  8** **resources\_plan**  parameter description

<a name="table10281451162111"></a>
<table><thead align="left"><tr id="row21077515215"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="p11361051162118"><a name="p11361051162118"></a><a name="p11361051162118"></a><strong id="b7261143718239"><a name="b7261143718239"></a><a name="b7261143718239"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="p1815835115218"><a name="p1815835115218"></a><a name="p1815835115218"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="p2018015511218"><a name="p2018015511218"></a><a name="p2018015511218"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="p5198351122117"><a name="p5198351122117"></a><a name="p5198351122117"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row1121555192110"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p18632144118282"><a name="p18632144118282"></a><a name="p18632144118282"></a>period_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p4632164118286"><a name="p4632164118286"></a><a name="p4632164118286"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p166321418282"><a name="p166321418282"></a><a name="p166321418282"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p963214419289"><a name="p963214419289"></a><a name="p963214419289"></a>Cycle type of a resource plan. Currently, only the following cycle type is supported:</p>
<a name="ul363284116288"></a><a name="ul363284116288"></a><ul id="ul363284116288"><li>daily</li></ul>
</td>
</tr>
<tr id="row1531855116213"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p11633174182818"><a name="p11633174182818"></a><a name="p11633174182818"></a>start_time</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p196331041132814"><a name="p196331041132814"></a><a name="p196331041132814"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p19633114122816"><a name="p19633114122816"></a><a name="p19633114122816"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p13633154112816"><a name="p13633154112816"></a><a name="p13633154112816"></a>Start time of a resources plan. The value is in the format of <strong id="b972495515249"><a name="b972495515249"></a><a name="b972495515249"></a>hour:minute</strong>, indicating that the time ranges from 0:00 to 23:59.</p>
</td>
</tr>
<tr id="row7405105118211"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p126333415281"><a name="p126333415281"></a><a name="p126333415281"></a>end_time</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p2063344114284"><a name="p2063344114284"></a><a name="p2063344114284"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p863364112819"><a name="p863364112819"></a><a name="p863364112819"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p2633174117282"><a name="p2633174117282"></a><a name="p2633174117282"></a>End time of a resources plan. The value is in the same format as that of <span class="parmname" id="parmname108341828162917"><a name="parmname108341828162917"></a><a name="parmname108341828162917"></a><b>start_time</b></span>. The interval between <strong id="b1917973215256"><a name="b1917973215256"></a><a name="b1917973215256"></a>end_time</strong> and <strong id="b149161137152511"><a name="b149161137152511"></a><a name="b149161137152511"></a>start_time</strong> must be greater than or equal to 30 minutes.</p>
</td>
</tr>
<tr id="row19532851132116"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p206334415288"><a name="p206334415288"></a><a name="p206334415288"></a>min_capacity</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p2633184112285"><a name="p2633184112285"></a><a name="p2633184112285"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p116331241202817"><a name="p116331241202817"></a><a name="p116331241202817"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p6633141102810"><a name="p6633141102810"></a><a name="p6633141102810"></a>Minimum number of the preserved nodes in a node group in a resource plan.</p>
<p id="p3629135317296"><a name="p3629135317296"></a><a name="p3629135317296"></a>Value range: 0 to 500</p>
</td>
</tr>
<tr id="row176245516217"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p263304119287"><a name="p263304119287"></a><a name="p263304119287"></a>max_capacity</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p146331041172818"><a name="p146331041172818"></a><a name="p146331041172818"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p156331241162818"><a name="p156331241162818"></a><a name="p156331241162818"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p19633174118288"><a name="p19633174118288"></a><a name="p19633174118288"></a>Maximum number of the preserved nodes in a node group in a resource plan.</p>
<p id="p16373013020"><a name="p16373013020"></a><a name="p16373013020"></a>Value range: 0 to 500</p>
</td>
</tr>
</tbody>
</table>

**Table  9** **exec\_script**  parameter description

<a name="table1921110172216"></a>
<table><thead align="left"><tr id="row1428214111224"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="p15297171172210"><a name="p15297171172210"></a><a name="p15297171172210"></a><strong id="b14579436112615"><a name="b14579436112615"></a><a name="b14579436112615"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="p8318816229"><a name="p8318816229"></a><a name="p8318816229"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="p19332191122219"><a name="p19332191122219"></a><a name="p19332191122219"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="p934614122220"><a name="p934614122220"></a><a name="p934614122220"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row16364151162210"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p2716626113010"><a name="p2716626113010"></a><a name="p2716626113010"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p9716122653011"><a name="p9716122653011"></a><a name="p9716122653011"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p12716172613308"><a name="p12716172613308"></a><a name="p12716172613308"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p1271632643011"><a name="p1271632643011"></a><a name="p1271632643011"></a>Name of a custom automation script. It must be unique in a same cluster.</p>
<p id="p971662623010"><a name="p971662623010"></a><a name="p971662623010"></a>The value can contain only digits, letters, spaces, hyphens (-), and underscores (_) and cannot start with a space.</p>
<p id="p2716192613010"><a name="p2716192613010"></a><a name="p2716192613010"></a>The value can contain 1 to 64 characters.</p>
</td>
</tr>
<tr id="row1446317117222"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p1671632619307"><a name="p1671632619307"></a><a name="p1671632619307"></a>uri</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p771612265306"><a name="p771612265306"></a><a name="p771612265306"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p37169268302"><a name="p37169268302"></a><a name="p37169268302"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p15716132603020"><a name="p15716132603020"></a><a name="p15716132603020"></a>Path of a custom automation script. Set this parameter to an OBS bucket path or a local VM path.</p>
<a name="ul2716122616303"></a><a name="ul2716122616303"></a><ul id="ul2716122616303"><li>OBS bucket path: Enter a script path manually, for example, <strong id="b862319216300"><a name="b862319216300"></a><a name="b862319216300"></a>s3a://<em id="i17361161133015"><a name="i17361161133015"></a><a name="i17361161133015"></a>XXX</em>/scale.sh</strong>.</li><li>Local VM path: Enter a script path. The script path must start with a slash (/) and end with <strong id="b2635103117309"><a name="b2635103117309"></a><a name="b2635103117309"></a>.sh</strong>.</li></ul>
</td>
</tr>
<tr id="row25607102210"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p361414413374"><a name="p361414413374"></a><a name="p361414413374"></a>parameters</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p361484123715"><a name="p361484123715"></a><a name="p361484123715"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p146149414371"><a name="p146149414371"></a><a name="p146149414371"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p8614746374"><a name="p8614746374"></a><a name="p8614746374"></a>Parameters of a custom automation script</p>
<a name="ul19405172713813"></a><a name="ul19405172713813"></a><ul id="ul19405172713813"><li>Multiple parameters are separated by space.</li><li>The following predefined system parameters can be transferred:<a name="ul740512275389"></a><a name="ul740512275389"></a><ul id="ul740512275389"><li>${mrs_scale_node_num}: Number of the nodes to be added or removed</li><li>${mrs_scale_type}: Scaling type. The value can be <strong id="b209806114324"><a name="b209806114324"></a><a name="b209806114324"></a>scale_out</strong> or <strong id="b16355132010329"><a name="b16355132010329"></a><a name="b16355132010329"></a>scale_in</strong>.</li><li>${mrs_scale_node_hostnames}: Host names of the nodes to be added or removed</li><li>${mrs_scale_node_ips}: IP addresses of the nodes to be added or removed</li><li>${mrs_scale_rule_name}: Name of the rule that triggers auto scaling</li></ul>
</li><li>Other user-defined parameters are used in the same way as those of common shell scripts. Parameters are separated by space.</li></ul>
</td>
</tr>
<tr id="row870514172210"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p106161244377"><a name="p106161244377"></a><a name="p106161244377"></a>nodes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p661616418371"><a name="p661616418371"></a><a name="p661616418371"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p14616244375"><a name="p14616244375"></a><a name="p14616244375"></a>List&lt;String&gt;</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p56161649373"><a name="p56161649373"></a><a name="p56161649373"></a>Type of a node where the custom automation script is executed. The node type can be Master, Core, or Task.</p>
</td>
</tr>
<tr id="row67891315228"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p1733982111374"><a name="p1733982111374"></a><a name="p1733982111374"></a>active_master</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p153391921173710"><a name="p153391921173710"></a><a name="p153391921173710"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p4339142163715"><a name="p4339142163715"></a><a name="p4339142163715"></a>Boolean</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p833952163716"><a name="p833952163716"></a><a name="p833952163716"></a>Whether the custom automation script runs only on the active Master node.</p>
<p id="p13391218375"><a name="p13391218375"></a><a name="p13391218375"></a>The default value is <strong id="b98671943018"><a name="b98671943018"></a><a name="b98671943018"></a>false</strong>, indicating that the custom automation script can run on all Master nodes.</p>
</td>
</tr>
<tr id="row3891131122219"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p195951338133710"><a name="p195951338133710"></a><a name="p195951338133710"></a>action_stage</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p1759563815377"><a name="p1759563815377"></a><a name="p1759563815377"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p195951038123720"><a name="p195951038123720"></a><a name="p195951038123720"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p5595438133717"><a name="p5595438133717"></a><a name="p5595438133717"></a>Time when a script is executed.</p>
<p id="p175951038193717"><a name="p175951038193717"></a><a name="p175951038193717"></a>The following four options are supported:</p>
<a name="ul959511385379"></a><a name="ul959511385379"></a><ul id="ul959511385379"><li>before_scale_out: before scale-out</li><li>before_scale_in: before scale-in</li><li>after_scale_out: after scale-out</li><li>after_scale_in: after scale-in</li></ul>
</td>
</tr>
<tr id="row173493683712"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p1595838193720"><a name="p1595838193720"></a><a name="p1595838193720"></a>fail_action</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p1595138123712"><a name="p1595138123712"></a><a name="p1595138123712"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p159611387376"><a name="p159611387376"></a><a name="p159611387376"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p959633833712"><a name="p959633833712"></a><a name="p959633833712"></a>Whether to continue to execute subsequent scripts and create a cluster after the custom automation script fails to be executed.</p>
<a name="ul1859673813372"></a><a name="ul1859673813372"></a><ul id="ul1859673813372"><li>continue: Continue to execute subsequent scripts.</li><li>errorout: Stop the action.<div class="note" id="note1637813387373"><a name="note1637813387373"></a><a name="note1637813387373"></a><span class="notetitle"> NOTE: </span><div class="notebody"><a name="ul117517425369"></a><a name="ul117517425369"></a><ul id="ul117517425369"><li>You are advised to set this parameter to <strong id="b842352706114220"><a name="b842352706114220"></a><a name="b842352706114220"></a>continue</strong> in the commissioning phase so that the cluster can continue to be installed and started no matter whether the custom automation script is executed successfully.</li><li>The scale-in operation cannot be undone. Therefore <span class="parmname" id="parmname47251253810"><a name="parmname47251253810"></a><a name="parmname47251253810"></a><b>fail_action</b></span> must be set to <span class="parmvalue" id="parmvalue7529192612381"><a name="parmvalue7529192612381"></a><a name="parmvalue7529192612381"></a><b>continue</b></span> for the scripts that are executed after scale-in.</li></ul>
</div></div>
</li></ul>
</td>
</tr>
</tbody>
</table>

**Table  10** **rules**  parameter description

<a name="t4c9e3e169631470d81d260543affb7e1"></a>
<table><thead align="left"><tr id="r04dab5da98994243b13ab537426a3a97"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="ad679ccb275b24cc496175d3841c71d4a"><a name="ad679ccb275b24cc496175d3841c71d4a"></a><a name="ad679ccb275b24cc496175d3841c71d4a"></a><strong id="b136101356781"><a name="b136101356781"></a><a name="b136101356781"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="a640760dee401468b9b46729570e2c885"><a name="a640760dee401468b9b46729570e2c885"></a><a name="a640760dee401468b9b46729570e2c885"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="acb08948a5f1440c3b9925d7b25fd1cfc"><a name="acb08948a5f1440c3b9925d7b25fd1cfc"></a><a name="acb08948a5f1440c3b9925d7b25fd1cfc"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="ae3354bfaa9f549358e263c7ff419fb0b"><a name="ae3354bfaa9f549358e263c7ff419fb0b"></a><a name="ae3354bfaa9f549358e263c7ff419fb0b"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="rb70a6fabcd634bb488830fad4df3ec23"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a30a512ec6a824430b85d412a03a87f01"><a name="a30a512ec6a824430b85d412a03a87f01"></a><a name="a30a512ec6a824430b85d412a03a87f01"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a9821fa2ef3a545c6918722356913f19d"><a name="a9821fa2ef3a545c6918722356913f19d"></a><a name="a9821fa2ef3a545c6918722356913f19d"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a79be49bbaf734f838a223ef00e505777"><a name="a79be49bbaf734f838a223ef00e505777"></a><a name="a79be49bbaf734f838a223ef00e505777"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="aba48112f6b6643379185e9024b158818"><a name="aba48112f6b6643379185e9024b158818"></a><a name="aba48112f6b6643379185e9024b158818"></a>Name of an auto scaling rule</p>
<p id="ad2dfd75a61e449daba07a8aec95b70af"><a name="ad2dfd75a61e449daba07a8aec95b70af"></a><a name="ad2dfd75a61e449daba07a8aec95b70af"></a>It contains only 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.</p>
<p id="a4fb8ccd95fd84f4e9167a742ea119278"><a name="a4fb8ccd95fd84f4e9167a742ea119278"></a><a name="a4fb8ccd95fd84f4e9167a742ea119278"></a>Rule names must be unique in a node group.</p>
</td>
</tr>
<tr id="r43e582bae8d7452ba656dde618f5200c"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a4db367e43bb943eeb5a845fa7b3209a6"><a name="a4db367e43bb943eeb5a845fa7b3209a6"></a><a name="a4db367e43bb943eeb5a845fa7b3209a6"></a>description</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aa3ce5a5274894b5c8ff040dbda4d893a"><a name="aa3ce5a5274894b5c8ff040dbda4d893a"></a><a name="aa3ce5a5274894b5c8ff040dbda4d893a"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a5229ef45bcb04550a546ed9ef4541966"><a name="a5229ef45bcb04550a546ed9ef4541966"></a><a name="a5229ef45bcb04550a546ed9ef4541966"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a54e73e7a5fe84ea68e0c68c676c69078"><a name="a54e73e7a5fe84ea68e0c68c676c69078"></a><a name="a54e73e7a5fe84ea68e0c68c676c69078"></a>Description about an auto scaling rule.</p>
<p id="a3913d07fc617486c800f3e34ebc28224"><a name="a3913d07fc617486c800f3e34ebc28224"></a><a name="a3913d07fc617486c800f3e34ebc28224"></a>It contains a maximum of 1024 characters.</p>
</td>
</tr>
<tr id="r63d765b129664dad957626f380819572"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a44f544e08b0a41de95dabf9bf4e1434a"><a name="a44f544e08b0a41de95dabf9bf4e1434a"></a><a name="a44f544e08b0a41de95dabf9bf4e1434a"></a>adjustment_type</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aeef54466240a420aa0b5613dbb65143d"><a name="aeef54466240a420aa0b5613dbb65143d"></a><a name="aeef54466240a420aa0b5613dbb65143d"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a433b89c3fb244d7e954a41597d978cf8"><a name="a433b89c3fb244d7e954a41597d978cf8"></a><a name="a433b89c3fb244d7e954a41597d978cf8"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="afb3bb8888f944246b9b844cf271c4ab2"><a name="afb3bb8888f944246b9b844cf271c4ab2"></a><a name="afb3bb8888f944246b9b844cf271c4ab2"></a>Auto scaling rule adjustment type. The options are as follows:</p>
<a name="u18ec9abfa0234393b376df8ff616d19b"></a><a name="u18ec9abfa0234393b376df8ff616d19b"></a><ul id="u18ec9abfa0234393b376df8ff616d19b"><li>scale_out: cluster scale-out</li><li>scale_in: cluster scale-in</li></ul>
</td>
</tr>
<tr id="r6f9ebcd76459417a908a73ec838efe7c"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a8f20410dbaee433abb560ec4458140af"><a name="a8f20410dbaee433abb560ec4458140af"></a><a name="a8f20410dbaee433abb560ec4458140af"></a>cool_down_minutes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ace0d1386b05a420fad2f53bd4dbd7f4f"><a name="ace0d1386b05a420fad2f53bd4dbd7f4f"></a><a name="ace0d1386b05a420fad2f53bd4dbd7f4f"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a125498882f804fa99362663be962a9ec"><a name="a125498882f804fa99362663be962a9ec"></a><a name="a125498882f804fa99362663be962a9ec"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a962e8faec9684b4b9388ddaae5f20f25"><a name="a962e8faec9684b4b9388ddaae5f20f25"></a><a name="a962e8faec9684b4b9388ddaae5f20f25"></a>Cluster cooling time after an auto scaling rule is triggered, when no auto scaling operation is performed. The unit is minute.</p>
<p id="a934200a982984f90a54b157715b28542"><a name="a934200a982984f90a54b157715b28542"></a><a name="a934200a982984f90a54b157715b28542"></a>Value range: 0 to 10080. One week is equal to 10080 minutes.</p>
</td>
</tr>
<tr id="r83dc95f88c514f349fe399e2daec1acf"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a1bf156eb290c4eacac485c8e69bb9b8a"><a name="a1bf156eb290c4eacac485c8e69bb9b8a"></a><a name="a1bf156eb290c4eacac485c8e69bb9b8a"></a>scaling_adjustment</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ac34a827ef47d41c19cb0a362521c1749"><a name="ac34a827ef47d41c19cb0a362521c1749"></a><a name="ac34a827ef47d41c19cb0a362521c1749"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a8ed38e14158144d1a1feee5d0c6672f9"><a name="a8ed38e14158144d1a1feee5d0c6672f9"></a><a name="a8ed38e14158144d1a1feee5d0c6672f9"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="acf6914ca275e493ba883ebb8a607a1ad"><a name="acf6914ca275e493ba883ebb8a607a1ad"></a><a name="acf6914ca275e493ba883ebb8a607a1ad"></a>Number of nodes that can be adjusted once</p>
<p id="a665de6492d5f41e183c5fdfa2a65629a"><a name="a665de6492d5f41e183c5fdfa2a65629a"></a><a name="a665de6492d5f41e183c5fdfa2a65629a"></a>Value range: 1 to 100</p>
</td>
</tr>
<tr id="r66369f0421994b56a9ed58368cc08d5a"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a5817b59eda8846d1ae9d530bd1ab342d"><a name="a5817b59eda8846d1ae9d530bd1ab342d"></a><a name="a5817b59eda8846d1ae9d530bd1ab342d"></a>trigger</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="aee6e5978de8143a7bfdc40db6e9304b2"><a name="aee6e5978de8143a7bfdc40db6e9304b2"></a><a name="aee6e5978de8143a7bfdc40db6e9304b2"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="afd9beb4a2ace493390bc25ced1fecf8d"><a name="afd9beb4a2ace493390bc25ced1fecf8d"></a><a name="afd9beb4a2ace493390bc25ced1fecf8d"></a>Trigger</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a2c60fdaa8e8b434d91a9aaf1e369eff6"><a name="a2c60fdaa8e8b434d91a9aaf1e369eff6"></a><a name="a2c60fdaa8e8b434d91a9aaf1e369eff6"></a>Condition for triggering a rule. For details, see <a href="#t03bd10dc0ec94a3babc71b2d5d57c3fe">Table 11</a>.</p>
</td>
</tr>
</tbody>
</table>

**Table  11** **trigger**  parameter description

<a name="t03bd10dc0ec94a3babc71b2d5d57c3fe"></a>
<table><thead align="left"><tr id="rff8c363cdf464eb5a3a11207ffdf1cd8"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="af7ff5d0628724b4fa7b5cf884ea1b773"><a name="af7ff5d0628724b4fa7b5cf884ea1b773"></a><a name="af7ff5d0628724b4fa7b5cf884ea1b773"></a><strong id="b476928132219"><a name="b476928132219"></a><a name="b476928132219"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="a56f9bf71c2fc47b5a8e8e7c679965679"><a name="a56f9bf71c2fc47b5a8e8e7c679965679"></a><a name="a56f9bf71c2fc47b5a8e8e7c679965679"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="a8933d7f27ddb4c9798f80813eb864963"><a name="a8933d7f27ddb4c9798f80813eb864963"></a><a name="a8933d7f27ddb4c9798f80813eb864963"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="a1f9301595b084bb0a1226a00ef63cf3a"><a name="a1f9301595b084bb0a1226a00ef63cf3a"></a><a name="a1f9301595b084bb0a1226a00ef63cf3a"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="re14becd52b854699886dab346ddbbca9"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="ad3f42958ab364805946248b8a97a5681"><a name="ad3f42958ab364805946248b8a97a5681"></a><a name="ad3f42958ab364805946248b8a97a5681"></a>metric_name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a5e62e69cca49432484b604bd6c10da4f"><a name="a5e62e69cca49432484b604bd6c10da4f"></a><a name="a5e62e69cca49432484b604bd6c10da4f"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="af5d60c6023c64eb3af69213451e45a08"><a name="af5d60c6023c64eb3af69213451e45a08"></a><a name="af5d60c6023c64eb3af69213451e45a08"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="a67c5bbe2340144a0ac4ae630da919fdb"><a name="a67c5bbe2340144a0ac4ae630da919fdb"></a><a name="a67c5bbe2340144a0ac4ae630da919fdb"></a>Metric name</p>
<p id="ad6898742fd8c4b3d90f62a110092174a"><a name="ad6898742fd8c4b3d90f62a110092174a"></a><a name="ad6898742fd8c4b3d90f62a110092174a"></a>This triggering condition makes a judgment according to the value of the metric.</p>
<p id="adb15d44ef9cd49719e1558f955af8fe0"><a name="adb15d44ef9cd49719e1558f955af8fe0"></a><a name="adb15d44ef9cd49719e1558f955af8fe0"></a>A metric name contains a maximum of 64 characters.</p>
<p id="a249e5e0f422a474eb818f01e56c3c6e2"><a name="a249e5e0f422a474eb818f01e56c3c6e2"></a><a name="a249e5e0f422a474eb818f01e56c3c6e2"></a><a href="#t27de3279a99a48968dacb015c498d9cb">Table 12</a> lists the supported metric names.</p>
</td>
</tr>
<tr id="rdf8d159ee61f4397920756d6db18f225"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="aaefe5f406be947a9bc590420af9fa60a"><a name="aaefe5f406be947a9bc590420af9fa60a"></a><a name="aaefe5f406be947a9bc590420af9fa60a"></a>metric_value</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ad6ce5627219640d1a928ec145a5c9543"><a name="ad6ce5627219640d1a928ec145a5c9543"></a><a name="ad6ce5627219640d1a928ec145a5c9543"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="ae5eed36b433c4a778931e35c51c255c0"><a name="ae5eed36b433c4a778931e35c51c255c0"></a><a name="ae5eed36b433c4a778931e35c51c255c0"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="af6f48d7468d64a0394a3a4213d2a2268"><a name="af6f48d7468d64a0394a3a4213d2a2268"></a><a name="af6f48d7468d64a0394a3a4213d2a2268"></a>Metric threshold to trigger a rule</p>
<p id="a9cb6280b4c514776b95dd786fe3b71b9"><a name="a9cb6280b4c514776b95dd786fe3b71b9"></a><a name="a9cb6280b4c514776b95dd786fe3b71b9"></a>The parameter value must be an integer or number with two decimal places only. <a href="#t27de3279a99a48968dacb015c498d9cb">Table 12</a> provides values types and ranges corresponding to <strong id="b1161104445418"><a name="b1161104445418"></a><a name="b1161104445418"></a>metric_name</strong>.</p>
</td>
</tr>
<tr id="re4671e894e4448eb87e9d7ff852aecb5"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="af47cf271b63941ac96944f24e87910b2"><a name="af47cf271b63941ac96944f24e87910b2"></a><a name="af47cf271b63941ac96944f24e87910b2"></a>comparison_operator</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="ab55411f4b2a54e7195864b2dc799f3bb"><a name="ab55411f4b2a54e7195864b2dc799f3bb"></a><a name="ab55411f4b2a54e7195864b2dc799f3bb"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="a933e80262e8c483dbfbf38aa2ec35333"><a name="a933e80262e8c483dbfbf38aa2ec35333"></a><a name="a933e80262e8c483dbfbf38aa2ec35333"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="adf4bb9d515db4212bee56e7a4389a892"><a name="adf4bb9d515db4212bee56e7a4389a892"></a><a name="adf4bb9d515db4212bee56e7a4389a892"></a>Metric judgment logic operator. The options are as follows:</p>
<a name="u7169b3049e9342e185a5074148528db2"></a><a name="u7169b3049e9342e185a5074148528db2"></a><ul id="u7169b3049e9342e185a5074148528db2"><li>LT: less than</li><li>GT: greater than</li><li>LTOE: less than or equal to</li><li>GTOE: greater than or equal to</li></ul>
</td>
</tr>
<tr id="rf50d0c4b959f434f956a9cd587368b68"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="a03c9f551658b4130989f42292477ab3a"><a name="a03c9f551658b4130989f42292477ab3a"></a><a name="a03c9f551658b4130989f42292477ab3a"></a>evaluation_periods</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="a036fbc2365fe431f9752b41bf56b6913"><a name="a036fbc2365fe431f9752b41bf56b6913"></a><a name="a036fbc2365fe431f9752b41bf56b6913"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="aaf1bc273e1ea46b3bd11b243b4223b90"><a name="aaf1bc273e1ea46b3bd11b243b4223b90"></a><a name="aaf1bc273e1ea46b3bd11b243b4223b90"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="aac0eda51209e440da2832133da986fe2"><a name="aac0eda51209e440da2832133da986fe2"></a><a name="aac0eda51209e440da2832133da986fe2"></a>Number of consecutive five-minute periods, during which a metric threshold is reached</p>
<p id="ab1eaebbe8f6a4f64ba521a9e4558f4b4"><a name="ab1eaebbe8f6a4f64ba521a9e4558f4b4"></a><a name="ab1eaebbe8f6a4f64ba521a9e4558f4b4"></a>Value range: 1 to 288</p>
</td>
</tr>
</tbody>
</table>

**Table  12**  Auto scaling metrics

<a name="t27de3279a99a48968dacb015c498d9cb"></a>
<table><thead align="left"><tr id="r6f513581428249f08e517a602d698e15"><th class="cellrowborder" valign="top" width="15.598440155984402%" id="mcps1.2.5.1.1"><p id="a438235aa61f14211bfc4a1a5b83eb558"><a name="a438235aa61f14211bfc4a1a5b83eb558"></a><a name="a438235aa61f14211bfc4a1a5b83eb558"></a>Cluster Type</p>
</th>
<th class="cellrowborder" valign="top" width="24.437556244375564%" id="mcps1.2.5.1.2"><p id="abe5e348bbff341ce8105e23a1ed1773b"><a name="abe5e348bbff341ce8105e23a1ed1773b"></a><a name="abe5e348bbff341ce8105e23a1ed1773b"></a>Metric Name</p>
</th>
<th class="cellrowborder" valign="top" width="15.22847715228477%" id="mcps1.2.5.1.3"><p id="a682d9e227f744055822e498bf9c5856d"><a name="a682d9e227f744055822e498bf9c5856d"></a><a name="a682d9e227f744055822e498bf9c5856d"></a>Value Type</p>
</th>
<th class="cellrowborder" valign="top" width="44.73552644735527%" id="mcps1.2.5.1.4"><p id="a253484a6f10b4e48932213cd57a12322"><a name="a253484a6f10b4e48932213cd57a12322"></a><a name="a253484a6f10b4e48932213cd57a12322"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r3d35885bfaf34dd19a45669ca955ca07"><td class="cellrowborder" rowspan="7" valign="top" width="15.598440155984402%" headers="mcps1.2.5.1.1 "><p id="a5114f66cbef24be89bf81e8698e641bf"><a name="a5114f66cbef24be89bf81e8698e641bf"></a><a name="a5114f66cbef24be89bf81e8698e641bf"></a>Streaming cluster</p>
</td>
<td class="cellrowborder" valign="top" width="24.437556244375564%" headers="mcps1.2.5.1.2 "><p id="ac72545b57c754656979548eb610a6870"><a name="ac72545b57c754656979548eb610a6870"></a><a name="ac72545b57c754656979548eb610a6870"></a>StormSlotAvailable</p>
</td>
<td class="cellrowborder" valign="top" width="15.22847715228477%" headers="mcps1.2.5.1.3 "><p id="a335961e130ae43bbad38525916ff3c50"><a name="a335961e130ae43bbad38525916ff3c50"></a><a name="a335961e130ae43bbad38525916ff3c50"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="44.73552644735527%" headers="mcps1.2.5.1.4 "><p id="a6798fd17f81446d7bc23b65c206e62df"><a name="a6798fd17f81446d7bc23b65c206e62df"></a><a name="a6798fd17f81446d7bc23b65c206e62df"></a>Number of available Storm slots</p>
<p id="af8a8f569acf143b1b0641749d9a8958c"><a name="af8a8f569acf143b1b0641749d9a8958c"></a><a name="af8a8f569acf143b1b0641749d9a8958c"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="rb933f33ebd4043ba9e917d0d2f4852e3"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="ab02fb123f43e415b8bb10a908a8acb3b"><a name="ab02fb123f43e415b8bb10a908a8acb3b"></a><a name="ab02fb123f43e415b8bb10a908a8acb3b"></a>StormSlotAvailablePercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a52893a2e940f4c5ab48c2e5473ce2f0a"><a name="a52893a2e940f4c5ab48c2e5473ce2f0a"></a><a name="a52893a2e940f4c5ab48c2e5473ce2f0a"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a019e6f8ac83a4aa88544fb69ef775a38"><a name="a019e6f8ac83a4aa88544fb69ef775a38"></a><a name="a019e6f8ac83a4aa88544fb69ef775a38"></a>Percentage of available Storm slots, that is, the proportion of the available slots to total slots</p>
<p id="ac2fa579fd8b34e32bee870e7fc7f2ac9"><a name="ac2fa579fd8b34e32bee870e7fc7f2ac9"></a><a name="ac2fa579fd8b34e32bee870e7fc7f2ac9"></a>Value range: 0 to 100</p>
</td>
</tr>
<tr id="r08070c64771a42b6a113d6febbfaa29d"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a691509a26b894eb482bc9ba4b595edb1"><a name="a691509a26b894eb482bc9ba4b595edb1"></a><a name="a691509a26b894eb482bc9ba4b595edb1"></a>StormSlotUsed</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="abe031b1f053a4e3ead22c147dcafa3aa"><a name="abe031b1f053a4e3ead22c147dcafa3aa"></a><a name="abe031b1f053a4e3ead22c147dcafa3aa"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a277ae72eb6754de2bf11608cd9e6e12e"><a name="a277ae72eb6754de2bf11608cd9e6e12e"></a><a name="a277ae72eb6754de2bf11608cd9e6e12e"></a>Number of the used Storm slots</p>
<p id="ae765f078f7354dacb24c79349c9a5e6c"><a name="ae765f078f7354dacb24c79349c9a5e6c"></a><a name="ae765f078f7354dacb24c79349c9a5e6c"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="re0b727e5886646b49fe255ac2e7a2951"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="afd137ca4d82b4bceb58798293de6c8d4"><a name="afd137ca4d82b4bceb58798293de6c8d4"></a><a name="afd137ca4d82b4bceb58798293de6c8d4"></a>StormSlotUsedPercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a880db12e66534c39810fd1d0bd16093a"><a name="a880db12e66534c39810fd1d0bd16093a"></a><a name="a880db12e66534c39810fd1d0bd16093a"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="ad49e3d813f2d4239a469338f348c3077"><a name="ad49e3d813f2d4239a469338f348c3077"></a><a name="ad49e3d813f2d4239a469338f348c3077"></a>Percentage of the used Storm slots, that is, the proportion of the used slots to total slots</p>
<p id="ada4c81170b0d4b93b744a65a698d5174"><a name="ada4c81170b0d4b93b744a65a698d5174"></a><a name="ada4c81170b0d4b93b744a65a698d5174"></a>Value range: 0 to 100</p>
</td>
</tr>
<tr id="row177919386154"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p135088571721"><a name="p135088571721"></a><a name="p135088571721"></a>StormSupervisorMemAverageUsage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1950845719217"><a name="p1950845719217"></a><a name="p1950845719217"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p165082571219"><a name="p165082571219"></a><a name="p165082571219"></a>Average memory usage of the Supervisor process of Storm</p>
<p id="p165194141793"><a name="p165194141793"></a><a name="p165194141793"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="row631194414155"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p188210636"><a name="p188210636"></a><a name="p188210636"></a>StormSupervisorMemAverageUsagePercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p6821801732"><a name="p6821801732"></a><a name="p6821801732"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p88213018314"><a name="p88213018314"></a><a name="p88213018314"></a>Average percentage of the used memory of the Supervisor process of Storm to the total memory of the system</p>
<p id="p3227151918108"><a name="p3227151918108"></a><a name="p3227151918108"></a>Value range: 0 to 100</p>
</td>
</tr>
<tr id="row7783194871512"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p794819218319"><a name="p794819218319"></a><a name="p794819218319"></a>StormSupervisorCPUAverageUsagePercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1494842533"><a name="p1494842533"></a><a name="p1494842533"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p1948121837"><a name="p1948121837"></a><a name="p1948121837"></a>Average percentage of the used CPUs of the Supervisor process of Storm to the total CPUs</p>
<p id="p1690164451113"><a name="p1690164451113"></a><a name="p1690164451113"></a>Value range: 0 to 6000</p>
</td>
</tr>
<tr id="ra430378d169b44c29d0139187c0f4a11"><td class="cellrowborder" rowspan="14" valign="top" width="15.598440155984402%" headers="mcps1.2.5.1.1 "><p id="af2c3361bef3e4acda820a0b5349dab94"><a name="af2c3361bef3e4acda820a0b5349dab94"></a><a name="af2c3361bef3e4acda820a0b5349dab94"></a>Analysis cluster</p>
</td>
<td class="cellrowborder" valign="top" width="24.437556244375564%" headers="mcps1.2.5.1.2 "><p id="a2ebc162d44404c4b9171628d2937cac6"><a name="a2ebc162d44404c4b9171628d2937cac6"></a><a name="a2ebc162d44404c4b9171628d2937cac6"></a>YARNAppPending</p>
</td>
<td class="cellrowborder" valign="top" width="15.22847715228477%" headers="mcps1.2.5.1.3 "><p id="a49aea79e2e884b39906752aeb50f6a38"><a name="a49aea79e2e884b39906752aeb50f6a38"></a><a name="a49aea79e2e884b39906752aeb50f6a38"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" width="44.73552644735527%" headers="mcps1.2.5.1.4 "><p id="ad5b596886c494b288346f643daa764e9"><a name="ad5b596886c494b288346f643daa764e9"></a><a name="ad5b596886c494b288346f643daa764e9"></a>Number of pending tasks on YARN</p>
<p id="a35def1222c304e88a59b86583ce0130d"><a name="a35def1222c304e88a59b86583ce0130d"></a><a name="a35def1222c304e88a59b86583ce0130d"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="r1c774463d2a14083a7fdfd96cbaefcef"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a26a74b6270f741a09b3bc5dec2b8a129"><a name="a26a74b6270f741a09b3bc5dec2b8a129"></a><a name="a26a74b6270f741a09b3bc5dec2b8a129"></a>YARNAppPendingRatio</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a8867793be2584544838efdc864b1b199"><a name="a8867793be2584544838efdc864b1b199"></a><a name="a8867793be2584544838efdc864b1b199"></a>Ratio</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a16e41ae39c3542cea4823cc61c96a5d3"><a name="a16e41ae39c3542cea4823cc61c96a5d3"></a><a name="a16e41ae39c3542cea4823cc61c96a5d3"></a>Ratio of pending tasks on YARN, that is, the ratio of pending tasks to running tasks on YARN</p>
<p id="a2d50ce28b3f445d49825f72dd917624d"><a name="a2d50ce28b3f445d49825f72dd917624d"></a><a name="a2d50ce28b3f445d49825f72dd917624d"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="ra094fb90825148839fb3e3c750b09969"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="aa9ba37f3d402455d8e6f9d17b3b83329"><a name="aa9ba37f3d402455d8e6f9d17b3b83329"></a><a name="aa9ba37f3d402455d8e6f9d17b3b83329"></a>YARNAppRunning</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a985a37b47e8541daa74672ec40190b2d"><a name="a985a37b47e8541daa74672ec40190b2d"></a><a name="a985a37b47e8541daa74672ec40190b2d"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="ab56444e8f8054590a8eb9776184ee285"><a name="ab56444e8f8054590a8eb9776184ee285"></a><a name="ab56444e8f8054590a8eb9776184ee285"></a>Number of running tasks on YARN</p>
<p id="a6bb7fc15c9cc497b9befea371482ee14"><a name="a6bb7fc15c9cc497b9befea371482ee14"></a><a name="a6bb7fc15c9cc497b9befea371482ee14"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="r877ab3607fb24199a4f8f5e6027e2d83"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a5e1a1fcebf9c4f5f96457b335d8d3524"><a name="a5e1a1fcebf9c4f5f96457b335d8d3524"></a><a name="a5e1a1fcebf9c4f5f96457b335d8d3524"></a>YARNContainerAllocated</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a4582c276628b40d69800e7c2f0f3e496"><a name="a4582c276628b40d69800e7c2f0f3e496"></a><a name="a4582c276628b40d69800e7c2f0f3e496"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a8dd055b550404e3586a2d008b49cb4aa"><a name="a8dd055b550404e3586a2d008b49cb4aa"></a><a name="a8dd055b550404e3586a2d008b49cb4aa"></a>Number of containers allocated to YARN </p>
<p id="a0af753d126374689b243d324b8b62643"><a name="a0af753d126374689b243d324b8b62643"></a><a name="a0af753d126374689b243d324b8b62643"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="rf899d1058342458c8922fce992d570cc"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a3c879e53204943baa6f00e332603b436"><a name="a3c879e53204943baa6f00e332603b436"></a><a name="a3c879e53204943baa6f00e332603b436"></a>YARNContainerPending</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a9a4b0bf584494168ad484b62945df5ab"><a name="a9a4b0bf584494168ad484b62945df5ab"></a><a name="a9a4b0bf584494168ad484b62945df5ab"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="abd01e06bb70544e38882c07fdf1e5fbe"><a name="abd01e06bb70544e38882c07fdf1e5fbe"></a><a name="abd01e06bb70544e38882c07fdf1e5fbe"></a>Number of pending containers on YARN</p>
<p id="a93d072fada4a4322bb38029de44e1ea2"><a name="a93d072fada4a4322bb38029de44e1ea2"></a><a name="a93d072fada4a4322bb38029de44e1ea2"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="r6eea766caaa8483ba2889235d08f1fb1"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a554108d1a4ac4d548d0d7c913d2c0e96"><a name="a554108d1a4ac4d548d0d7c913d2c0e96"></a><a name="a554108d1a4ac4d548d0d7c913d2c0e96"></a>YARNContainerPendingRatio</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a2f421b01c38b4dacab515d5013a94ec6"><a name="a2f421b01c38b4dacab515d5013a94ec6"></a><a name="a2f421b01c38b4dacab515d5013a94ec6"></a>Ratio</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a3ff2b486a44e4a079f2893a62ebe1057"><a name="a3ff2b486a44e4a079f2893a62ebe1057"></a><a name="a3ff2b486a44e4a079f2893a62ebe1057"></a>Ratio of pending containers on YARN, that is, the ratio of pending containers to running containers on YARN.</p>
<p id="afbecb57893244882aa592c19c2c6d4ca"><a name="afbecb57893244882aa592c19c2c6d4ca"></a><a name="afbecb57893244882aa592c19c2c6d4ca"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="rada32b2ffd544cdb9aceb4f9499866c0"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="aa85783e97d85436eaf8172c7a9377839"><a name="aa85783e97d85436eaf8172c7a9377839"></a><a name="aa85783e97d85436eaf8172c7a9377839"></a>YARNCPUAllocated</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="ae9db170af0a74db097a4118d3c6acbd5"><a name="ae9db170af0a74db097a4118d3c6acbd5"></a><a name="ae9db170af0a74db097a4118d3c6acbd5"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a83a9e1639ef541398ad1326edfbe5652"><a name="a83a9e1639ef541398ad1326edfbe5652"></a><a name="a83a9e1639ef541398ad1326edfbe5652"></a>Number of virtual CPUs (vCPUs) allocated to YARN</p>
<p id="a647834b124bd4911a4e811ad0d5fab4e"><a name="a647834b124bd4911a4e811ad0d5fab4e"></a><a name="a647834b124bd4911a4e811ad0d5fab4e"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="r24f9d8b6e19347a6af3a2b2602817b67"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a56f523a1e5d3450bbfdda7743eb92854"><a name="a56f523a1e5d3450bbfdda7743eb92854"></a><a name="a56f523a1e5d3450bbfdda7743eb92854"></a>YARNCPUAvailable</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a1879208a01884bc3bd21a4d2c696aad8"><a name="a1879208a01884bc3bd21a4d2c696aad8"></a><a name="a1879208a01884bc3bd21a4d2c696aad8"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a0ae5d086156342deba2460f41206c148"><a name="a0ae5d086156342deba2460f41206c148"></a><a name="a0ae5d086156342deba2460f41206c148"></a>Number of available vCPUs on YARN</p>
<p id="aee8087bc3ad8436fa0f8ef040ba673ab"><a name="aee8087bc3ad8436fa0f8ef040ba673ab"></a><a name="aee8087bc3ad8436fa0f8ef040ba673ab"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="rb1a623bacb3446a7ad80947e61db5e14"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a14553be3cec14ae38983fbfb99f29d83"><a name="a14553be3cec14ae38983fbfb99f29d83"></a><a name="a14553be3cec14ae38983fbfb99f29d83"></a>YARNCPUAvailablePercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a4ba6a334b5624002aea5c16ec2bef623"><a name="a4ba6a334b5624002aea5c16ec2bef623"></a><a name="a4ba6a334b5624002aea5c16ec2bef623"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a7f11c0314e0d4bcba94eaf62b670b6f1"><a name="a7f11c0314e0d4bcba94eaf62b670b6f1"></a><a name="a7f11c0314e0d4bcba94eaf62b670b6f1"></a>Percentage of available vCPUs on YARN, that is, the proportion of available vCPUs to total vCPUs</p>
<p id="a50104756cbae4a11afe22dfe9b28fd26"><a name="a50104756cbae4a11afe22dfe9b28fd26"></a><a name="a50104756cbae4a11afe22dfe9b28fd26"></a>Value range: 0 to 100</p>
</td>
</tr>
<tr id="r0d968a43dce44f34bc59e65763a42dff"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="aaf82b0df6bd1489b9e4835f72e66848b"><a name="aaf82b0df6bd1489b9e4835f72e66848b"></a><a name="aaf82b0df6bd1489b9e4835f72e66848b"></a>YARNCPUPending</p>
<p id="adb1ad1fe51bc4d9097f76ed15949faee"><a name="adb1ad1fe51bc4d9097f76ed15949faee"></a><a name="adb1ad1fe51bc4d9097f76ed15949faee"></a></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a182e236f3a6547c1b0c9ddeedc1cb812"><a name="a182e236f3a6547c1b0c9ddeedc1cb812"></a><a name="a182e236f3a6547c1b0c9ddeedc1cb812"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a091982b0354948558a83a2972fc10d78"><a name="a091982b0354948558a83a2972fc10d78"></a><a name="a091982b0354948558a83a2972fc10d78"></a>Number of pending vCPUs on YARN</p>
<p id="a28c518ff6e6f4720a9f248b1785b1a2b"><a name="a28c518ff6e6f4720a9f248b1785b1a2b"></a><a name="a28c518ff6e6f4720a9f248b1785b1a2b"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="r07797e16294f41f2bd22c3d3e0f4fd86"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="af491e04ac4c749678edb5ccd96ecad9c"><a name="af491e04ac4c749678edb5ccd96ecad9c"></a><a name="af491e04ac4c749678edb5ccd96ecad9c"></a>YARNMemoryAllocated</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="ab2771fecf43a4a048713d458958feac6"><a name="ab2771fecf43a4a048713d458958feac6"></a><a name="ab2771fecf43a4a048713d458958feac6"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="ab22cfcbebf544c61b8dc9284e58cf92a"><a name="ab22cfcbebf544c61b8dc9284e58cf92a"></a><a name="ab22cfcbebf544c61b8dc9284e58cf92a"></a>Memory allocated to YARN. The unit is MB.</p>
<p id="a482cb09ec7f146e997111e48c2165fad"><a name="a482cb09ec7f146e997111e48c2165fad"></a><a name="a482cb09ec7f146e997111e48c2165fad"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="re4224e170a464ddcb72136c05158e75b"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="a2e28017342644f3eb52611d00003d7b7"><a name="a2e28017342644f3eb52611d00003d7b7"></a><a name="a2e28017342644f3eb52611d00003d7b7"></a>YARNMemoryAvailable</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="ab709decebd9e4b69a20482fd11472034"><a name="ab709decebd9e4b69a20482fd11472034"></a><a name="ab709decebd9e4b69a20482fd11472034"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a561342c4dfc44654a5ea5ebfcb97c989"><a name="a561342c4dfc44654a5ea5ebfcb97c989"></a><a name="a561342c4dfc44654a5ea5ebfcb97c989"></a>Available memory on YARN. The unit is MB.</p>
<p id="abfa4f9cfe2094a23b33bdd2f66070f57"><a name="abfa4f9cfe2094a23b33bdd2f66070f57"></a><a name="abfa4f9cfe2094a23b33bdd2f66070f57"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
<tr id="refec09246ff047d7a9e3bf7d06a42cfd"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="aaa3390f6e15d4e5ea1140e5d599e6035"><a name="aaa3390f6e15d4e5ea1140e5d599e6035"></a><a name="aaa3390f6e15d4e5ea1140e5d599e6035"></a>YARNMemoryAvailablePercentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a67ac734ecc7b4b018a960953697740ed"><a name="a67ac734ecc7b4b018a960953697740ed"></a><a name="a67ac734ecc7b4b018a960953697740ed"></a>Percentage</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="ac111dffe2233485382eab7979f3b65b3"><a name="ac111dffe2233485382eab7979f3b65b3"></a><a name="ac111dffe2233485382eab7979f3b65b3"></a>Percentage of available memory on YARN, that is, the proportion of available memory to total memory on YARN</p>
<p id="ae0f790dfccb9435484818f104234f1ea"><a name="ae0f790dfccb9435484818f104234f1ea"></a><a name="ae0f790dfccb9435484818f104234f1ea"></a>Value range: 0 to 100</p>
</td>
</tr>
<tr id="r0c96fd2f38dc41c6abb55f6997c2f4ad"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="af44c9409613840b281cd58f04122b5f8"><a name="af44c9409613840b281cd58f04122b5f8"></a><a name="af44c9409613840b281cd58f04122b5f8"></a>YARNMemoryPending</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="a462b3630c14b4fdcb4fbeabe4d5767cb"><a name="a462b3630c14b4fdcb4fbeabe4d5767cb"></a><a name="a462b3630c14b4fdcb4fbeabe4d5767cb"></a>Integer</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="a4a7656ef0e7d41e994bb809330d24e1f"><a name="a4a7656ef0e7d41e994bb809330d24e1f"></a><a name="a4a7656ef0e7d41e994bb809330d24e1f"></a>Pending memory on YARN</p>
<p id="a5a450cbc34414ab599f331078b5f7d88"><a name="a5a450cbc34414ab599f331078b5f7d88"></a><a name="a5a450cbc34414ab599f331078b5f7d88"></a>Value range: 0 to 2147483646</p>
</td>
</tr>
</tbody>
</table>

>![](public_sys-resources/icon-note.gif) **NOTE:**   
>When the value type is percentage or ratio in  [Table 12](#t27de3279a99a48968dacb015c498d9cb), the valid value can be accurate to percentile. The percentage metric value is a decimal value with a percent sign \(%\) removed. For example, 16.80 represents 16.80%.  

**Table  13** **bootstrap\_scripts**  parameter description

<a name="table1258382865010"></a>
<table><thead align="left"><tr id="row16585132875017"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="p2058552815010"><a name="p2058552815010"></a><a name="p2058552815010"></a><strong id="b144217612013"><a name="b144217612013"></a><a name="b144217612013"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.2"><p id="p4585152815505"><a name="p4585152815505"></a><a name="p4585152815505"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.5.1.3"><p id="p145856289503"><a name="p145856289503"></a><a name="p145856289503"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="45%" id="mcps1.2.5.1.4"><p id="p35851281504"><a name="p35851281504"></a><a name="p35851281504"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="row19585182815014"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p0223193618537"><a name="p0223193618537"></a><a name="p0223193618537"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p1322353616531"><a name="p1322353616531"></a><a name="p1322353616531"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p1422373615314"><a name="p1422373615314"></a><a name="p1422373615314"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p27361059145112"><a name="p27361059145112"></a><a name="p27361059145112"></a>Name of a bootstrap action script. It must be unique in a cluster.</p>
<p id="p1768234115215"><a name="p1768234115215"></a><a name="p1768234115215"></a>The value can contain only digits, letters, spaces, hyphens (-), and underscores (_) and cannot start with a space.</p>
<p id="p35651138195212"><a name="p35651138195212"></a><a name="p35651138195212"></a>The value can contain 1 to 64 characters.</p>
</td>
</tr>
<tr id="row55851328175016"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p132232362536"><a name="p132232362536"></a><a name="p132232362536"></a>uri</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p12223123614537"><a name="p12223123614537"></a><a name="p12223123614537"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p16223183655320"><a name="p16223183655320"></a><a name="p16223183655320"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p13373112592717"><a name="p13373112592717"></a><a name="p13373112592717"></a>Path of a bootstrap action script. Set this parameter to an OBS bucket path or a local VM path.</p>
<a name="ul129121753017"></a><a name="ul129121753017"></a><ul id="ul129121753017"><li>OBS bucket path: Enter a script path manually. For example, enter the path of the public sample script provided by MRS. Example: <strong id="b156521362034"><a name="b156521362034"></a><a name="b156521362034"></a>s3a://bootstrap/presto/presto-install.sh</strong>. If <strong id="b3177141715214"><a name="b3177141715214"></a><a name="b3177141715214"></a>dualroles</strong> is installed, the parameter of the <strong id="b141789175220"><a name="b141789175220"></a><a name="b141789175220"></a>presto-install.sh</strong> script is <strong id="b1417961714218"><a name="b1417961714218"></a><a name="b1417961714218"></a>dualroles</strong>. If <strong id="b71811017122"><a name="b71811017122"></a><a name="b71811017122"></a>worker</strong> is installed, the parameter of the <strong id="b3182417523"><a name="b3182417523"></a><a name="b3182417523"></a>presto-install.sh</strong> script is <strong id="b71841717829"><a name="b71841717829"></a><a name="b71841717829"></a>worker</strong>. Based on the Presto usage habit, you are advised to install <strong id="b842352706171336"><a name="b842352706171336"></a><a name="b842352706171336"></a>dualroles</strong> on the active Master nodes and <strong id="b842352706171346"><a name="b842352706171346"></a><a name="b842352706171346"></a>worker</strong> on the Core nodes.</li><li>Local VM path: Enter a script path. The script path must start with a slash (/) and end with <strong id="b1283338432"><a name="b1283338432"></a><a name="b1283338432"></a>.sh</strong>.</li></ul>
</td>
</tr>
<tr id="row11585122835019"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p32231936175317"><a name="p32231936175317"></a><a name="p32231936175317"></a>parameters</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p2223193615533"><a name="p2223193615533"></a><a name="p2223193615533"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p322373685317"><a name="p322373685317"></a><a name="p322373685317"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p28581637172215"><a name="p28581637172215"></a><a name="p28581637172215"></a>Bootstrap action script parameters</p>
</td>
</tr>
<tr id="row2058516287502"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p7694821145413"><a name="p7694821145413"></a><a name="p7694821145413"></a>nodes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p42231036165313"><a name="p42231036165313"></a><a name="p42231036165313"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p1822313612539"><a name="p1822313612539"></a><a name="p1822313612539"></a>Array String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p12585928145012"><a name="p12585928145012"></a><a name="p12585928145012"></a>Type of a node where the bootstrap action script is executed. The value can be Master, Core, or Task.</p>
</td>
</tr>
<tr id="row4757171219539"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p19223203615313"><a name="p19223203615313"></a><a name="p19223203615313"></a>active_master</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p92233362534"><a name="p92233362534"></a><a name="p92233362534"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p152231536145317"><a name="p152231536145317"></a><a name="p152231536145317"></a>Boolean</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p207581812185316"><a name="p207581812185316"></a><a name="p207581812185316"></a>Whether the bootstrap action script runs only on active Master nodes.</p>
<p id="p1919931141119"><a name="p1919931141119"></a><a name="p1919931141119"></a>The default value is <strong id="b1599618249918"><a name="b1599618249918"></a><a name="b1599618249918"></a>false</strong>, indicating that the bootstrap action script can run on all Master nodes.</p>
</td>
</tr>
<tr id="row12296121585317"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p965715541023"><a name="p965715541023"></a><a name="p965715541023"></a>before_component_start</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p7224153625312"><a name="p7224153625312"></a><a name="p7224153625312"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p12224173635317"><a name="p12224173635317"></a><a name="p12224173635317"></a>Boolean</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p11296615135311"><a name="p11296615135311"></a><a name="p11296615135311"></a>Time when the bootstrap action script is executed. Currently, the following two options are available: <strong id="b842352706114015"><a name="b842352706114015"></a><a name="b842352706114015"></a>Before component start</strong> and <strong id="b842352706114018"><a name="b842352706114018"></a><a name="b842352706114018"></a>After component start</strong></p>
<p id="p172869585132"><a name="p172869585132"></a><a name="p172869585132"></a>The default value is <strong id="b811175019910"><a name="b811175019910"></a><a name="b811175019910"></a>false</strong>, indicating that the bootstrap action script is executed after the component is started.</p>
</td>
</tr>
<tr id="row1193251913537"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p132241936165315"><a name="p132241936165315"></a><a name="p132241936165315"></a>fail_action</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.2 "><p id="p022443635318"><a name="p022443635318"></a><a name="p022443635318"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.5.1.3 "><p id="p3224113655314"><a name="p3224113655314"></a><a name="p3224113655314"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="45%" headers="mcps1.2.5.1.4 "><p id="p4700154617299"><a name="p4700154617299"></a><a name="p4700154617299"></a>Whether to continue executing subsequent scripts and creating a cluster after the bootstrap action script fails to be executed.</p>
<a name="ul18391113413191"></a><a name="ul18391113413191"></a><ul id="ul18391113413191"><li>continue: Continue to execute subsequent scripts.</li><li>errorout: Stop the action.</li></ul>
<div class="p" id="p1818026201614"><a name="p1818026201614"></a><a name="p1818026201614"></a>The default value is <strong id="b8898494106"><a name="b8898494106"></a><a name="b8898494106"></a>errorout</strong>, indicating that the action is stopped.<div class="note" id="note796819345579"><a name="note796819345579"></a><a name="note796819345579"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="p6994625143710"><a name="p6994625143710"></a><a name="p6994625143710"></a>You are advised to set this parameter to <strong id="b65806426"><a name="b65806426"></a><a name="b65806426"></a>continue</strong> in the commissioning phase so that the cluster can continue to be installed and started no matter whether the bootstrap action is successful.</p>
</div></div>
</div>
</td>
</tr>
</tbody>
</table>

## Response<a name="s1fc899f588a54d38b6cd3a9ac7aef5e2"></a>

**Table  14**  Response parameter description

<a name="t2e2c04af37c5480ea9025d026610b9bb"></a>
<table><thead align="left"><tr id="r2e166255b6f94f9d8c077a8042e0595f"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.4.1.1"><p id="en-us_topic_0110581924_p42893210328"><a name="en-us_topic_0110581924_p42893210328"></a><a name="en-us_topic_0110581924_p42893210328"></a><strong id="b13192135117102"><a name="b13192135117102"></a><a name="b13192135117102"></a>Parameter</strong></p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.4.1.2"><p id="abce61d58ffb84dcebac614d57bc68c71"><a name="abce61d58ffb84dcebac614d57bc68c71"></a><a name="abce61d58ffb84dcebac614d57bc68c71"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.4.1.3"><p id="a9e61b6c89c234b31ab5421e0205f85b2"><a name="a9e61b6c89c234b31ab5421e0205f85b2"></a><a name="a9e61b6c89c234b31ab5421e0205f85b2"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r8ae12bdde7d4444d92599009f4297e6e"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.1 "><p id="a0f0db59ba5074b109734aaabee70e269"><a name="a0f0db59ba5074b109734aaabee70e269"></a><a name="a0f0db59ba5074b109734aaabee70e269"></a>cluster_id</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0110581924_p744840610328"><a name="en-us_topic_0110581924_p744840610328"></a><a name="en-us_topic_0110581924_p744840610328"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.4.1.3 "><p id="afce6114c78d44a70995e2699bdc177f8"><a name="afce6114c78d44a70995e2699bdc177f8"></a><a name="afce6114c78d44a70995e2699bdc177f8"></a>Cluster ID, which is returned by the system after the cluster is created.</p>
</td>
</tr>
<tr id="rf4387f34c6fc4e7ba9e1f59b4ba61a3c"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.1 "><p id="a0832285830b948a0837e2ed4e63fe2af"><a name="a0832285830b948a0837e2ed4e63fe2af"></a><a name="a0832285830b948a0837e2ed4e63fe2af"></a>result</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.2 "><p id="a17b7c484f84b461aafbb3194cbaf8f5e"><a name="a17b7c484f84b461aafbb3194cbaf8f5e"></a><a name="a17b7c484f84b461aafbb3194cbaf8f5e"></a>Bool</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0110581924_p579568910328"><a name="en-us_topic_0110581924_p579568910328"></a><a name="en-us_topic_0110581924_p579568910328"></a>Operation result</p>
<a name="uc323531d101446e59160932bb68f00ba"></a><a name="uc323531d101446e59160932bb68f00ba"></a><ul id="uc323531d101446e59160932bb68f00ba"><li>true: The operation is successful.</li><li>false: The operation failed.</li></ul>
</td>
</tr>
<tr id="r345025ef16ec499b9bc7da57e699fe4c"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.1 "><p id="a8d7eb9310db443a3b0aa4ae0b305a092"><a name="a8d7eb9310db443a3b0aa4ae0b305a092"></a><a name="a8d7eb9310db443a3b0aa4ae0b305a092"></a>msg</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.4.1.2 "><p id="a7b51865fb8e14eadaba6fb1bf0131ba1"><a name="a7b51865fb8e14eadaba6fb1bf0131ba1"></a><a name="a7b51865fb8e14eadaba6fb1bf0131ba1"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.4.1.3 "><p id="a640daaea3378476186914f6e991f93f1"><a name="a640daaea3378476186914f6e991f93f1"></a><a name="a640daaea3378476186914f6e991f93f1"></a>System message, which can be empty.</p>
</td>
</tr>
</tbody>
</table>

## Example<a name="section141101025191619"></a>

-   Example request

    Creating a cluster with  **Cluster HA**  enabled

    ```
    {
        "billing_type": 12, 
        "data_center": "eu-de", 
        "master_node_num": 2, 
        "master_node_size": "s1.8xlarge.linux.mrs", 
        "core_node_num": 3, 
        "core_node_size": "c2.2xlarge.linux.mrs", 
        "available_zone_id": "bf84aba586ce4e948da0b97d9a7d62fb", 
        "cluster_name": "newcluster", 
        "vpc": "vpc1", 
        "vpc_id": "5b7db34d-3534-4a6e-ac94-023cd36aaf74", 
        "subnet_id": "815bece0-fd22-4b65-8a6e-15788c99ee43", 
        "subnet_name": "subnet",
        "security_groups_id": "",
        "tags": [
           {
              "key": "key1",
              "value": "value1"
           },
           {
              "key": "key2",
              "value": "value2"
           }
        ],
        "cluster_version": "MRS 2.1.0",
        "cluster_type": 0,
        "master_data_volume_type": "SATA",
        "master_data_volume_size": 100,
        "master_data_volume_count": 1,
        "core_data_volume_type": "SATA",
        "core_data_volume_size": 100,
        "core_data_volume_count": 2,
        
        "node_public_cert_name": "SSHkey-bba1", 
        "safe_mode": 0,
        "cluster_admin_secret":"******", 
        "log_collection": 1,
        "task_node_groups": [
           {
             
             "node_num": 2,
             "node_size": "s1.xlarge.linux.mrs",
             "data_volume_type": "SATA",
             "data_volume_count": 1,
             "data_volume_size": 700,
             "auto_scaling_policy": 
              {
                 "auto_scaling_enable": true,
                 "min_capacity": "1",
                 "max_capacity": "3",
                 "resources_plans": [{
                   "period_type": "daily",
                   "start_time": "9:50",
                   "end_time": "10:20",
                   "min_capacity": "2",
                   "max_capacity": "3"
                 },{
                   "period_type": "daily",
                   "start_time": "10:20",
                   "end_time": "12:30",
                   "min_capacity": "0",
                   "max_capacity": "2"
                 }],
                 "exec_scripts": [{
                   "name": "before_scale_out",
                   "uri": "s3a://XXX/zeppelin_install.sh",
                   "parameters": "",
                   "nodes": [
                     "master",
                     "core",
                     "task"
                   ],
                   "active_master": "true",
                   "action_stage": "before_scale_out",
                   "fail_action": "continue"
                 },{
                   "name": "after_scale_out",
                   "uri": "s3a://XXX/storm_rebalance.sh",
                   "parameters": "",
                   "nodes": [
                     "master",
                     "core",
                     "task"
                   ],
                   "active_master": "true",
                   "action_stage": "after_scale_out",
                   "fail_action": "continue"
                 }],
                 "rules": [
                  {
                   "name": "default-expand-1",
                   "adjustment_type": "scale_out",
                   "cool_down_minutes": 5,
                   "scaling_adjustment": 1,
                   "trigger": {
                     "metric_name": "YARNMemoryAvailablePercentage",
                     "metric_value": "25",
                     "comparison_operator": "LT",
                     "evaluation_periods": 10
                    }
                   },
                 {
                   "name": "default-shrink-1",
                   "adjustment_type": "scale_in",
                   "cool_down_minutes": 5,
                   "scaling_adjustment": 1,
                   "trigger": {
                     "metric_name": "YARNMemoryAvailablePercentage",
                     "metric_value": "70",
                     "comparison_operator": "GT",
                     "evaluation_periods": 10
                   }
                 }
               ]
             }
           }
         ],
        "component_list": [
            {
                 
                "component_name": "Hadoop" 
                
            }, 
            {
                 
                "component_name": "Spark" 
                
            }, 
            {
     
                "component_name": "HBase" 
                
    
            }, 
            {
     
                "component_name": "Hive" 
                
    
            }, 
            {
     
                "component_name": "Presto" 
                
    
            }, 
            {
     
                "component_name": "Tez" 
                
    
            }, 
            {
     
                "component_name": "Hue" 
                
    
            }, 
            {
     
                "component_name": "Loader" 
                
    
            }, 
            {
     
                "component_name": "Flink" 
                
    
            }
        ], 
        "add_jobs": [
            {
                "job_type": 1, 
                "job_name": "tenji111", 
                "jar_path": "s3a://bigdata/program/hadoop-mapreduce-examples-XXX.jar", 
                "arguments": "wordcount", 
                "input": "s3a://bigdata/input/wd_1k/", 
                "output": "s3a://bigdata/ouput/", 
                "job_log": "s3a://bigdata/log/", 
                "shutdown_cluster": false, 
                "file_action": "", 
                "submit_job_once_cluster_run": true, 
                "hql": "", 
                "hive_script_path": ""
            }
        ],
    "bootstrap_scripts": [
             {
                 "name":"Modify os config",
                 "uri":"s3a://XXX/modify_os_config.sh",
                 "parameters":"param1 param2",
                 "nodes":[
                     "master",
                     "core",
                     "task"
                 ],
                 "active_master":"false",
                 "before_component_start":"true",
                 "fail_action":"continue"
             },
             {
                 "name":"Install zepplin",
                 "uri":"s3a://XXX/zeppelin_install.sh",
                 "parameters":"",
                 "nodes":[
                     "master"
                 ],
                 "active_master":"true",
                 "before_component_start":"false",
                 "fail_action":"continue"
             }
         ]
    }
    ```

    Creating the smallest cluster with  **Cluster HA**  disabled

    ```
    {
        "billing_type": 12, 
        "data_center": "eu-de", 
        "master_node_num": 1 
        "master_node_size": "s1.8xlarge.linux.mrs", 
        "core_node_num": 1, 
        "core_node_size": "c2.2xlarge.linux.mrs", 
        "available_zone_id": "bf84aba586ce4e948da0b97d9a7d62fb", 
        "cluster_name": "newcluster", 
        "vpc": "vpc1", 
        "vpc_id": "5b7db34d-3534-4a6e-ac94-023cd36aaf74", 
        "subnet_id": "815bece0-fd22-4b65-8a6e-15788c99ee43", 
        "subnet_name": "subnet", 
        "security_groups_id": "",
        "tags": [
           {
              "key": "key1",
              "value":"value1"
           },
           {
              "key": "key2",
              "value": "value2"
           }
        ],
        "cluster_version": "MRS 2.1.0",
        "cluster_type": 0,
        "master_data_volume_type": "SATA",
        "master_data_volume_size": 100,
        "master_data_volume_count": 1,
        "core_data_volume_type": "SATA",
        "core_data_volume_size": 100,
        "core_data_volume_count": 1,
        
        "node_public_cert_name": "SSHkey-bba1", 
        "safe_mode": 0,
        "cluster_admin_secret":"******",
        "log_collection": 1,
        "component_list": [
            {
               "component_name": "Hadoop" 
             }, 
            {
               "component_name": "Spark" 
             }, 
            {
               "component_name": "HBase" 
             }, 
            {
                "component_name": "Hive"
             }, 
            {
                 "component_name": "Presto" 
              }, 
            {
                "component_name": "Tez" 
            }, 
            {
                "component_name": "Hue"       
            }, 
            {
                "component_name": "Loader" 
            }, 
            {
                "component_name": "Flink" 
            }
                          ], 
        "add_jobs": [
            {
                "job_type": 1, 
                "job_name": "tenji111", 
                "jar_path": "s3a://bigdata/program/hadoop-mapreduce-examples-XXX.jar", 
                "arguments": "wordcount", 
                "input": "s3a://bigdata/input/wd_1k/", 
                "output": "s3a://bigdata/ouput/", 
                "job_log": "s3a://bigdata/log/", 
                "shutdown_cluster": false, 
                "file_action": "", 
                "submit_job_once_cluster_run": true, 
                "hql": "", 
                "hive_script_path": ""
            }
        ],
    "bootstrap_scripts": [
             {
                 "name":"Install zepplin",
                 "uri":"s3a://XXX/zeppelin_install.sh",
                 "parameters":"",
                 "nodes":[
                 "master"
                 ],
                 "active_master":"false",
                 "before_component_start":"false",
                 "fail_action":"continue"
             }
        ]
    }
    ```


-   Example response

    ```
    {
        "cluster_id": "da1592c2-bb7e-468d-9ac9-83246e95447a", 
        "result": true,
        "msg": ""
    }
    ```


## Status Code<a name="s96840205927b4620855700bce3bdf937"></a>

[Table 15](#t9da59f1e3aaa4a09903f34b2fc2401e4)  describes the status code of this API.

**Table  15**  Status code

<a name="t9da59f1e3aaa4a09903f34b2fc2401e4"></a>
<table><thead align="left"><tr id="r346472e3f2674761bb8ac9d23e55e89f"><th class="cellrowborder" valign="top" width="30%" id="mcps1.2.3.1.1"><p id="a057d6da56f7c4c17a3c691cd4d2ac9b7"><a name="a057d6da56f7c4c17a3c691cd4d2ac9b7"></a><a name="a057d6da56f7c4c17a3c691cd4d2ac9b7"></a>Status Code</p>
</th>
<th class="cellrowborder" valign="top" width="70%" id="mcps1.2.3.1.2"><p id="a3dc3e6e82627425696fd142c5243614d"><a name="a3dc3e6e82627425696fd142c5243614d"></a><a name="a3dc3e6e82627425696fd142c5243614d"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="r7a7171d6cc67408ca1f9309efcf0a59b"><td class="cellrowborder" valign="top" width="30%" headers="mcps1.2.3.1.1 "><p id="a6bf2d4310b35405c858f7bc2453ee4a6"><a name="a6bf2d4310b35405c858f7bc2453ee4a6"></a><a name="a6bf2d4310b35405c858f7bc2453ee4a6"></a>200</p>
</td>
<td class="cellrowborder" valign="top" width="70%" headers="mcps1.2.3.1.2 "><p id="a4f7ab33674ce48acb38caf8517f32d4c"><a name="a4f7ab33674ce48acb38caf8517f32d4c"></a><a name="a4f7ab33674ce48acb38caf8517f32d4c"></a>The cluster has been successfully created.</p>
</td>
</tr>
</tbody>
</table>

For the description about error status codes, see  [Status Codes](status-codes.md).

