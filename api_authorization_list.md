# API Access Authorization

API access authorization is implemeted to ensure secure access to EnOS resources through API. An application can access the resources of an organization only if the application is granted the appropriate authorization policy. For more information about EnOS user authorization, see [Policy, Role, and Access](/docs/iam/en/latest/access_policy).


| API Name	| Service	| Access Authorization |
| ------ | ------ | ------ |
| getAsset	| Asset	| Read |
| deleteAsset	| Asset	| Write |
| createAsset	| Asset	| Full Access|
| updateAsset	| Asset	| Write|
| listAssets	| Asset	| Read|
| insertNode	| Asset	| Full Access|
| getNode	| Asset	| Read|
| listChildNodes	| Asset	| Read|
| searchNodes	| Asset	| Read|
| deleteNode	| Asset	| Full Access|
| deleteAllNodesAndAsset	| Asset	| Full Access|
| bindAssetToNode	| Asset	| Full Access|
| updateNodeName	| Asset	| Full Access|
| searchNodePaths	| Asset	| Read|
| createTree	| Asset	| Full Access|
| listTrees	| Asset	| Read|
| getTree	| Asset	| Read|
| getThingModel	| Thing Model	| Read|
| listThingModels	| Thing Model	| Read|
| setMeasurepointByDeviceKey	| Device	| Control|
| setMeasurepointByAssetId	| Device	| Control|
| invokeServiceByDeviceKey	| Device	| Control|
| invokeServiceByAssetId	| Device	| Control|
| listProductTags	| Product     | Read|
| updateProductTags	| Product	| Full Access|
| deleteProductTags	| Product	| Full Access|
| listProducts	| Product	| Read|
| getProduct	| Product	| Read|
| createProduct	| Product	| Full Access|
| updateProduct	| Product	| Full Access|
| deleteProduct	| Product	| Full Access|
| listTopologyByDeviceKey	| Device	| Read|
| listTopologyByAssetId	| Device      | Read|
| createTopologyByDeviceKey	| Device      | Full Access|
| createTopologyByAssetId	| Device	| Full Access|
| deleteTopologyByDeviceKey	| Device	| Full Access|
| deleteTopologyByAssetId	| Device	| Full Access|
| listDeviceTagsByDeviceKey	| Device	| Read|
| listDeviceTagsByAssetId	| Device	| Read|
| updateDeviceTagsByDeviceKey	| Device	| Full Access|
| updateDeviceTagsByAssetId	| Device	| Full Access|
| deleteDeviceTagsByDeviceKey	| Device	| Full Access|
| deleteDeviceTagsByAssetId	| Device	| Full Access|
| uploadDeviceMeasurepoints	| Device	| Full Access|
| checkDevices	| Device	| Read|
| getMeasurepointsDataByDeviceKey	| Device	| Read|
| getMeasurepointsDataByAssetID	| Device	| Read|
| registerDevices	| Device	| Full Access|
| listDevices	| Device	| Read|
| getDeviceByDeviceKey	| Device	| Read|
| getDeviceByAssetId	| Device	| Read|
| updateDeviceByDeviceKey	| Device	| Full Access|
| updateDeviceByAssetId	| Device	| Full Access|
| deleteDeviceByDeviceKey	| Device	| Full Access|
| deleteDeviceByAssetId	| Device	| Full Access|
| getDeviceStatusByDeviceKeys	| Device	| Read|
| getDeviceStatusByAssetIds	| Device      | Read|
| getDeviceStatistics	| Statistics	| Read|
| disableDeviceByDeviceKey	| Device	| Full Access|
| disableDeviceByAssetId	| Device	| Full Access|
| enableDeviceByDeviceKey	| Device	| Full Access|
| applyCertificateByDeviceKey	| Certificate | Full Access|
| applyCertificateByAssetId	| Certificate | Full Access|
| revokeCertificateByDeviceKey	| Certificate | Full Access|
| revokeCertificateByAssetId	| Certificate | Full Access|
| listCertificatesByDeviceKey	| Certificate | Read|
| listCertificatesByAssetId	| Certificate	| Read|


