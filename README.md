# VivaTerminalRelayServer
Design and concept for the VivaWallet Relay Server

### IM30 PAX Terminal

If a IM30 PAX Terminal is used on another network then the platform or product you use, the IM30 is not usable. However using a Relay Server can solve this issue and can send transaction to 1 or more terminals.

Custom API connector(s) can be created and added to the Relay Server to receive the payment request(s).

The Relay server can be installed on a local computer and can be used on Linux, Apple, Windows etc... IOT devices like OrangePI, Raspberry PI, etc...

A webhook wil be used to receive the payment, if the payment is succesfull.

Concept of the Relay Server

![image](https://user-images.githubusercontent.com/96020208/215439208-b9639f2a-6b37-429e-828b-0ba1ccb6808b.png)

### How it works

The Relay Server will connect to a custom API connector, the API connector will then convert it to the same JSON that is used for Virutal Terminals POS.
We do this to be uniform with the documentation from VivaWallet.
```
https://developer.vivawallet.com/apis-for-point-of-sale/card-terminals-devices/rest-api/eft-pos-api-documentation/#tag/Transactions/paths/~1ecr~1v1~1transactions:sale/post
```

Using a Virtual Terminal you use: "/ecr/v1/transactions:sale" to post:
```
{
  "sessionId": "4bdebe62-c211-4ca0-a994-b2fbea2061c5",
  "terminalId": 16000010,
  "cashRegisterId": "XDE384678UY",
  "amount": 1170,
  "currencyCode": 978,
  "merchantReference": "some-reference",
  "customerTrns": "some-reference",
  "preauth": false,
  "maxInstalments": 0,
  "tipAmount": 0
}
```
The Relay Server will catch the request from the API, once received the source API need to flag the request as handled.

The Relay Server will convert to JSON into a Socket Instruction string



