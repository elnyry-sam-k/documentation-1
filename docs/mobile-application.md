# Resident Mobile Application

## Overview
In the Phase 1, the mobile application can be used by residents to securely store, share and receive digital credentials. The current version of this application supports only Android OS. This will later be extended to support iOS too.

The mobile application's repo is called [Inji](https://github.com/mosip/inji) and the corresponding backend that works as an intermediate between Inji and MOSIP platform is in [Mimoto repo](https://github.com/mosip/mimoto).

## Data model of digital credentials
The digital credentials generated by the mobile application follow the Verifiable Credentials data model. More details can be found [here](https://www.w3.org/TR/vc-data-model/#:~:text=A%20verifiable%20credential%20is%20a,can%20be%20about%20different%20subjects.)

## Installing the application
After installing the application, the user will need to set a app lock code for it. The current version supports a PIN based lock. The first launch will also establish a security check with Google SafetyNet Attestation API (for Android) and the equivalent for iOS.

The process flow for installation and first launch is given below

![](_images/app-install-launch-process.jpg)

## Generating and storing of credentials
A resident can generate a Verifiable Credential(VC) by either using a UIN or a VID. Detailed steps on generating and sharing credentials are given in the user guide [here](https://github.com/mosip/documentation/blob/1.2.0/docs/mobile-id-app-user-guide.md).

The process of generating a credential is shown below
![](_images/app-generating-credential-process.jpg)

## Sharing of credentials
In Phase 1, the credentials are shared in peer-to-peer model with another instance of the application. The data exchange between devices is done using Google Nearby Connections API. This API uses a combination of Bluetooth (BT), Bluetooth Low energy (BLE) and Wifi to achieve seamless, low-latency, high-throughput communications without requiring pairing of devices.


### How peer-to-peer connection is established
A QR code is generated and displayed on the requesting party's mobile application. A sample QR code json content is given below

```
{
  "cid": "1ejpu",
  "pk": "819176777955C098B78BAF949084A4484AEC5A769CED2307D59E46DC85A0F758"
}
```
where ```cid``` is a randomly generated connection ID which is used as a device identifier and ```pk``` is a randomly generated public key.

Once a sharing phone scans the QR code of the requesting/relying party, a connection is established between the two devices. When the requesting party has to connect to another device, a new QR code is generated.

The process flow for QR code scan is given below
![](_images/app-qr-code-scan-process.jpg)
  
The process flow for receiving the credentials is given below
![](_images/app-receiving-credential-process.jpg)

## Download resident mobile application
Resident Mobile Application can be downloaded from [here].(todo)