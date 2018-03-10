# Models

## AccountsAddDelegatesRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
publicKey* | string | A valid account Public Key.
secondSecret | string | A valid secondary account Passphrase.

## DelegatesAddDelegateRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
publicKey* | string | A valid account Public Key.
secondSecret | string | A valid secondary account Passphrase.
username* | string | A valid SmartHoldem Delegate username.

## MultisignaturesAddMultisignatureRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
publicKey* | string | A valid account Public Key.
secondSecret | string | A valid secondary account Passphrase.
min* | integer | min sugnatures (min 1 - max 16)
lifetime* | integer | min 1 - max 72
keysgroup* | array [string] | length 1 - 10

