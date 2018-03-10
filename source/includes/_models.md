# Models

## AccountsAddDelegatesRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
secondSecret | string | A valid secondary account Passphrase.
publicKey* | string | A valid account Public Key.

## DelegatesAddDelegateRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
secondSecret | string | A valid secondary account Passphrase.
publicKey* | string | A valid account Public Key.
username* | string | A valid SmartHoldem Delegate username.

## MultisignaturesAddMultisignatureRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
secondSecret | string | A valid secondary account Passphrase.
publicKey* | string | A valid account Public Key.
min* | integer | min sugnatures (min 1 - max 16)
lifetime* | integer | min 1 - max 72
keysgroup* | array [string] | A list of public keys. length 1 - 10

## SignaturesAddSignatureRequest

Parameter | Type | Description
--------- | ------- | -----------
secret* | string | A valid account Passphrase.
secondSecret | string | A valid secondary account Passphrase.
publicKey* | string | A valid account Public Key.
multisigAccountPublicKey* | string | A valid multi signature SmartHoldem Public Key.

