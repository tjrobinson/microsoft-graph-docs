---
description: "Automatically generated file. DO NOT MODIFY"
---

```python

// THE PYTHON SDK IS IN PREVIEW. NON-PRODUCTION USE ONLY
client =  GraphServiceClient(request_adapter)

request_body = TransferPostRequestBody()
transfer_target = InvitationParticipantInfo()
transfer_target.endpointtype(EndpointType.Default('endpointtype.default'))

transfer_targetidentity = IdentitySet()
additional_data = [
'phone' => transfer_targetidentity = Phone()
		transfer_targetidentity.@odata_type = '#microsoft.graph.identity'

		transfer_targetidentity.id = '+12345678901'


transfer_targetidentity.phone = phone

];
transfer_targetidentity.additional_data(additional_data)



transfer_target.identity = transfer_targetidentity
additional_data = [
'language_id' => 'languageId-value', 
'region' => 'region-value', 
];
transfer_target.additional_data(additional_data)



request_body.transfer_target = transfer_target



await client.communications.calls.by_call_id('call-id').transfer.post(request_body = request_body)


```