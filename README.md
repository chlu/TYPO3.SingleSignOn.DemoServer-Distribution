# Quickstart

## DemoInstance:

* Run `./flow singlesignon:generatekeypair` to create a new OpenSSL key pair
* Add setting "TYPO3.SingleSignOn.Client.ssoServerEndpointUrl" with the URI of the SSO server endpoint (e.g. http://ssodemoserver.dev/sso/authentication)
* Add setting "TYPO3.SingleSignOn.Client.ssoClientKeyPairUuid" with the created UUID
* Add setting "TYPO3.SingleSignOn.Client.ssoClientIdentifier" with an identifier of the SSO client (has to match the client identifier on the SSO server)
* Export the public key of the client "./flow singlesignon:exportpublickey [uuid] > demoinstance.pub"

## DemoServer:

* Import the public key of the client "./flow security:importpublickey < ../DemoInstance/demoinstance.pub"
* Add a client with the given client identifier and uuid: "./flow client:add demoinstance [uuid]"
* Generate key pair for server "./flow singlesignon:generatekeypair"
* Add setting "TYPO3.SingleSignOn.Server.ssoServerKeyPairUuid" with the UUID of the generated key pair
* Export server public key: "./flow singlesignon:exportpublickey e1879766_2a5b_4d5d_b2b9_30918dd18ef9 > demoserver.pub"

## DemoInstance

* Import server public key: "/flow security:importpublickey < ../DemoServer/demoserver.pub"
* Add setting "TYPO3.SingleSignOn.Client.ssoServerPublicKeyUuid" with the imported UUID
