# AppyPay Payment Gateway - Documentação consolidada

Documentação consolidada a partir dos arquivos HTML extraídos do site da AppyPay. A ordem inicial segue a organização exibida em `Barra lateral.html`; páginas adicionais de API foram agrupadas por seção e ordenadas alfabeticamente.

## Sumário

1. [Intro](#intro)
2. [SDD Payments Error Handling](#sdd-payments-error-handling)
3. [Accounts](#accounts)
4. [Authentication and Authorization](#authentication-and-authorization)
5. [Change-logs](#change-logs)
6. [Charges](#charges)
7. [Errors](#errors)
8. [Fiscal Documents](#fiscal-documents)
9. [Funds-Transfers](#funds-transfers)
10. [Migration Guide v1.2 to v2.0](#migration-guide-v1-2-to-v2-0)
11. [References](#references)
12. [Supported Payment Methods](#supported-payment-methods)
13. [Web App How-to](#web-app-how-to)
14. [Merchant Webhooks](#merchant-webhooks)
15. [Widget](#widget)
16. [AppyPay-Web-API](#appypay-web-api)
17. [AppyPay-API](#appypay-api)
18. [AppyPay-Authentication](#appypay-authentication)
19. [Get a token](#get-a-token)
20. [CancelMandateRequest.](#cancelmandaterequest)
21. [CancelMandateResponse](#cancelmandateresponse)
22. [Create a merchant GPO PST configurations](#create-a-merchant-gpo-pst-configurations)
23. [Create a refperiod](#create-a-refperiod)
24. [Get a merchant all GPO PST Configurations](#get-a-merchant-all-gpo-pst-configurations)
25. [Get a payout](#get-a-payout)
26. [Get all bank participants](#get-all-bank-participants)
27. [Get all business-categories](#get-all-business-categories)
28. [Get all business-types](#get-all-business-types)
29. [Get all payouts](#get-all-payouts)
30. [Post an application bank account](#post-an-application-bank-account)
31. [Subscribe or unsubscribe to push notifications](#subscribe-or-unsubscribe-to-push-notifications)
32. [Update a merchant GPO PST configurations](#update-a-merchant-gpo-pst-configurations)
33. [Cancel Mandate](#cancel-mandate)
34. [CancelMandateRequest](#cancelmandaterequest)
35. [CancelMandateResponse](#cancelmandateresponse)
36. [Get Taxpayer by NIF](#get-taxpayer-by-nif)
37. [Get a Mandate](#get-a-mandate)
38. [Get a charge](#get-a-charge)
39. [Get a creditor account for the specific application (beta)](#get-a-creditor-account-for-the-specific-application-beta)
40. [Get a fiscal document](#get-a-fiscal-document)
41. [Get a reference](#get-a-reference)
42. [Get all Mandates](#get-all-mandates)
43. [Get all analytics or charges](#get-all-analytics-or-charges)
44. [Get all analytics or references](#get-all-analytics-or-references)
45. [Get all applications](#get-all-applications)
46. [Get all charges](#get-all-charges)
47. [Get all fiscal documents](#get-all-fiscal-documents)
48. [Get all fiscal series](#get-all-fiscal-series)
49. [Get all funds-transfers](#get-all-funds-transfers)
50. [Get all references](#get-all-references)
51. [Get an account status](#get-an-account-status)
52. [Get an application point-of-sales](#get-an-application-point-of-sales)
53. [Post a Charge](#post-a-charge)
54. [Post a GPO QR Code](#post-a-gpo-qr-code)
55. [Post a Mandate](#post-a-mandate)
56. [Post a charge refund](#post-a-charge-refund)
57. [Post a charge reverse](#post-a-charge-reverse)
58. [Post a fiscal document](#post-a-fiscal-document)
59. [Post a fiscal series](#post-a-fiscal-series)
60. [Post a funds-transfers](#post-a-funds-transfers)
61. [Post an authorisation funds-transfers](#post-an-authorisation-funds-transfers)
62. [Post reference processing](#post-reference-processing)
63. [Post references](#post-references)
64. [TaxPayerResponse](#taxpayerresponse)
65. [TaxpayerStatus](#taxpayerstatus)
66. [TaxpayerType](#taxpayertype)
67. [Validate Fiscal Document](#validate-fiscal-document)
68. [ValidateDocumentRequest](#validatedocumentrequest)

---

## Intro

**Arquivo de origem:** `appypay/intro.html`

### Intro



AppyPay is Payment gateway facilitator for all Businesses in Angola.



Our APIs are designed around REST, with resource oriented naming convection and responses are JSON-Encoded.



###### Versioning


-  v1.1 - Legacy

-  v1.2 - Legacy

-  v2.0 - Default


###### 💡Where to start?



Get familiar with AppyPay API by reading following topics:


- Supported payment methods

- How charges work

- Authentication and authorization

- Error handling

- How funds-transfers work


Get familiar with AppyPay Portal by reading following topics:


- AppyPay Portal How-to


Get familiar with our low-code option with payment widget.



###### 🔝Upgrading from v1.2 to v2.0?



Find the important notes and major changes here.





Check our company here

---

## SDD Payments Error Handling

**Arquivo de origem:** `appypay/SDD Payments Error Handling.html`

### SDD Payments Error Handling



[Work in progress]



#### Intent Generation - Error Codes



Errors returned by AppyPay Intent generation service



##### Success Codes


 | Code | Reason Description | Descrição
 | Success_100 | Intent Processed Successfully | Instrução Processada com sucesso



##### Input validation errors


 | Code | Reason Description | Descrição
 | Error_01 | General Input validation error | Erro na validação de dados de entrada
 | Error_01_00 | Invalid Policy Number | Número da apólice inválido
 | Error_01_01 | Invalid Payment method | Metodo de pagamento inválida
 | Error_01_02 | Invalid Date Format | Formato de data inválido
 | Error_01_03 | Invalid Description | Descrição inválida
 | Error_01_04 | Invalid Amount | Valor inválido
 | Error_01_05 | Invalid Status | Estado inválido



##### Intent Submission Errors


 | Code | Reason Description | Descrição
 | Error_02 | General Intent Submission Error | Erro no envio da instrução de débito
 | Error_02_00 | Active Mandate with policy number not found | Mandato activo com número de apólice não encontrado
 | Error_02_01 | Intent Amount exceeds mandate max amount | O valor da intenção excede o valor máximo do mandato
 | Error_02_02 | Mandate currently has an ongoing payment instruction | Mandato actualmente com instrução de pagamento em curso
 | Error_02_03 | Intent debit date must be later than existing intent | Já existe uma instrução de débito com a data de débito à posterior a solicitada. A data de débito desta instrução deve ser posterior à ultima instrução existente
 | Error_02_04 | Intent debit date is before start date or after mandate expiration | A data de débito pretendida é anterior à data de início ou posterior a expiração do mandato
 | Error_02_05 | Mandate not active | A data de débito desta instrução de débito é após a expiração do mandato
 | Error_02_06 | Mandate not received | Mandato não recebido
 | Error_02_07 | Mandate not found | Mandato não encontrado
 | Error_02_08 | Payment intent is not allowed. Max number of payment instructions reached for mandate frequency type. | Instrução de pagamento não permitida. Número máximo de instruções de pagamento atingido para a frequência permitida no mandato.
 | Error_02_09 | Policy is set as Declined | Apólice recusada
 | Error_02_10 | Invalid debit date. Debit date must be at least 10 days from request date. | Data de débito inválida. A data de débito deve ser de, pelo menos, 10 dias a partir da data da solicitação.
 | Error_02_11 | `merchantReferenceNumber` is already in use in a ongoing transaction | O `merchantReferenceNumber` já está em utilização numa transação em curso.



##### EMIS Response errors


 | Code | Ref. | Reason Description | Descrição
 | Error_03 |  | EMIS Response errors |
 | Error_03_00 | XM04 | Insufficient Funds - Will be presented again | Fundos Insuficientes - Será apresentados novamente
 | Error_03_01 | AG01 | Transaction not authorized | Transação não autorizada
 | Error_03_02 | AG02 | Invalid Bank operation code | Código de operação do banco inválido
 | Error_03_03 | AGNT | Wrong participant identification | Identificação incorreta do participante
 | Error_03_04 | AM01 | Invalid value (0) | Valor inválido (0)
 | Error_03_05 | AM02 | Invalid amount | Valor inválido
 | Error_03_06 | AM03 | Invalid currency | Moeda inválida
 | Error_03_07 | AM05 | Duplicated | Duplicado
 | Error_03_08 | AM09 | Invalid value | Valor inválido
 | Error_03_09 | AM14 | Value is higher than maximum amount | O valor é superior ao valor máximo
 | Error_03_10 | DT01 | Invalid date | Data inválida
 | Error_03_11 | DS02 | Cancelled ADC | ADC Cancelado
 | Error_03_12 | ED05 | Settlement error | Erro de liquidação
 | Error_03_13 | RX01 | Rejected. ISO and own codes are set | Rejeitado. ISO e códigos próprios definidos
 | Error_03_14 | RX02 | There is at least one not supported field in the transaction | Há pelo menos um campo não suportado na transação
 | Error_03_15 | RX03 | Invalid Country code (Invalid ISO 3166) | RX03 Código de país inválido (ISO 3166 inválido)
 | Error_03_16 | RX04 | Invalid IBAN (ISO 13616) | IBAN inválido (ISO 13616)
 | Error_03_17 | RX05 | BIC non exists | BIC não existe
 | Error_03_18 | RX06 | Mandatory field not provided | Campo obrigatório não fornecido
 | Error_03_19 | RX07 | Not used | Não usado
 | Error_03_20 | RX08 | At least one of the XML elements have wrong format | Pelo menos um dos elementos XML tem formato errado
 | Error_03_21 | RX09 | Invalid “Transfer Reason ISO” | “ISO de Motivo de Transferência” inválido
 | Error_03_22 | RX10 | Invalid “Service Level Code” | “Código de nível de serviço” inválido
 | Error_03_23 | RX11 | Invalid “Local Instrument Code” | “Código de instrumento local” inválido
 | Error_03_24 | RX12 | Invalid “Category Purpose ISO Code” | “Código ISO de Finalidade da Categoria” inválido
 | Error_03_25 | RX13 | Invalid code | Código inválido
 | Error_03_26 | RX14 | ID different from original or missing | Diferente do original ou ausente
 | Error_03_27 | RX15 | Invalid number of decimals (2 digits) | Número inválido de decimais (2 dígitos)
 | Error_03_28 | RX16 | Invalid settlement method | Método de liquidação inválido
 | Error_03_29 | RX17 | OrgnlMsgId not recognized | OrgnlMsgId não reconhecido
 | Error_03_30 | RX18 | Invalid Original message status | Status da mensagem original inválido
 | Error_03_31 | RX19 | Invalid format | Formato inválido
 | Error_03_32 | RX20 | BIC different from original | BIC diferente do original
 | Error_03_33 | RX21 | Revoke non exists | Revcação não existe
 | Error_03_34 | RX22 | Invalid NBA check | Verificação de NBA inválida
 | Error_03_35 | RX23 | Invalid Purpose Code | Código de finalidade inválido
 | Error_03_36 | RX24 | Invalid revoke reason | Motivo de revogação inválido
 | Error_03_37 | RX25 | Invalid reversal reason | Motivo de reversão inválido
 | Error_03_38 | RX29 | Province code non exists | Código de província RX29 não existe
 | Error_03_39 | RX34 | Poor quality image | Imagem de má qualidade
 | Error_03_40 | RX39 | Image – resolution DPI | Imagem - resolução DPI
 | Error_03_41 | RX40 | Image – wrong format <> JPEG | Imagem - formato errado <> JPEG
 | Error_03_42 | RX41 | Image – Compression | Imagem - Compressão
 | Error_03_43 | RX42 | Image – grey scale | Imagem - Escala de cinza
 | Error_03_44 | RX43 | Image – Size | Imagem – Tamanho
 | Error_03_45 | MD16 | Client request ED | Solicitação de cliente ED
 | Error_03_46 | MD07 | Client Diseased | Cliente falecido
 | Error_03_47 | MS03 | IDD refused by Clients Bank with no explanation provided | IDD recusado pelo Banco de Clientes sem explicação fornecida
 | Error_03_48 | RR05 | Clients Name different then the one provided | Clientes Nome diferente do fornecido
 | Error_03_49 | DUPL | IDD liquidated more than once | IDD liquidado mais de uma vez
 | Error_03_50 | FR01 | Refused/Revoked due to fraud | IDD liquidado mais de uma vez
 | Error_03_51 | ANCF | Signature not compliant | Assinatura não compatível
 | Error_03_52 | ADEA | Valor debitado após finalização de serviço | Valor debitado após finalização de serviço
 | Error_03_53 | AC06 | Blocked Account | Conta bloqueada
 | Error_03_54 | AC04 | Account Closed | Conta encerrada

---

## Accounts

**Arquivo de origem:** `Payments Gateway - General Usage/Accounts.html`

### Accounts



💡 Some payment methods support user accounts, meaning an account is created in the provider system and can be verified based on an identifier.



Go to REST endpoints



##### Supported Payment Methods


-  UMM - Unitel Mobile Money

---

## Authentication and Authorization

**Arquivo de origem:** `Payments Gateway - General Usage/Authentication and Authorization.html`

### Authentication and Authorization


-

 The security and authentication for communication service to service will be setup using Azure AD B2CB.



-

 The OAuth2 flow used for authentication is the client credentials grant flow.




##### Authenticate with client id and client secret



All the endpoints provided on Payment Gateway require Merchant authentication and authorization, so this process must be implemented for every call mentioned on this document.



To get an access token, the merchant has to call the API: Get Token with provided merchant credentials.







Token will expire every 1 hour







🔑 Make sure to keep the merchant credentials secure!





Check here how to manage credentials.



##### Best practices for token management


- Secure Storage: Store tokens securely.

- Local caching: Locally cache tokens to improve authentication resilience.

- Token expiration: Consider reusing tokens by adjusting to the token's expiration time.


##### Best practices for secret management


-

Secure Storage: Store secrets securely.



-

Secret expiration: Implement short expiration dates for your secrets (6 months - 1 year) to reduce the window of vulnerability.



-

Version control: Consider using different secrets for different versions and during migration processes.



-

Renewal Policies: Implement policies that allow secrets to be renewed before they expire, ensuring a continuous user experience



-

Revocation: Monitor the use of secrets and have a mechanism to revoke compromised ones.

---

## Change-logs

**Arquivo de origem:** `Payments Gateway - General Usage/Change-logs.html`

### Change-logs



💡API change logs. In the following article all the applied changes of the API can be found.





Note: These are minor versions, that do not affect the versioning used by the merchant on the endpoint calls.



   v2.0.16 - Appypay API

##### v2.0.16 - Appypay API



Date: 05/07/2024



Payment Methods affected: All



New features: None



Fixes: General improvements and bug fixes:


- Handling properly custom options


How this may affect you: Fix issue with missing custom options.

   v2.0.15 - Appypay API

##### v2.0.15 - Appypay API



Date: 28/06/2024



Payment Methods affected: GPO



New features: None



Fixes: General improvements and bug fixes:


- Handling properly GPO response for no status transactions


How this may affect you: Improvements on the base service.

   v2.0.14 - Appypay API

##### v2.0.14 - Appypay API



Date: 27/06/2024



Payment Methods affected: GPO



New features: None



Fixes: General improvements and bug fixes:


- Maintenance transactions not handling properly GPO response


How this may affect you: Improvements on the base service.

   v2.0.13 - Appypay API

##### v2.0.13 - Appypay API



Date: 27/06/2024



Payment Methods affected: GPO, REF, UMM



New features: Introducing status property on response body and webhooks



Fixes: General improvements and bug fixes:


- Webhooks parameters and flow to call merchant bug fixes

- General GPO base service improvements


How this may affect you:


- Improvements on the base services and logs

- Introducing status property on charger response body and webhooks




   v2.0.12 - Appypay API

##### v2.0.12 - Appypay API



Date: 20/05/2024



Payment Methods affected: GPO, REF, UMM



New features: None



Fixes: General improvements and bug fixes:


- GPO clearing periods

- UMM logs implementations

- Bug fixes on refunds


How this may affect you: Improvements on the base services and logs.

   v2.0.11 - Appypay API

##### v2.0.11 - Appypay API



Date: 15/04/2024



Payment Methods affected: GPO



New features: None



Fixes: GPO authentication quick fix



How this may affect you: New responses and errors; New webhook body - Added sourceDetails object in responseStatus.

   v2.0.6 - Appypay API

##### v2.0.6 - Appypay API



Date: 05/01/2024



Payment Methods affected: GPO, REF, UMM



New features: Upgrade GPO authentication from v1.2 to v2.0



Fixes: General Improvements



How this may affect you: New responses and errors; New webhook body - Added sourceDetails object in responseStatus.



   v2.0.4 - Appypay API

##### v2.0.4 - Appypay API



Date: 09/10/2023



Payment Methods affected: GPO, UMM



New features: None



Fixes: POST Refunds general improvements



How this may affect you: Improvements on refunds.

   v2.0.3 - Appypay API

##### v2.0.3 - Appypay API



Date: 16/08/2023



Payment Methods affected: REF



New features: None



Fixes: POST REF Charges general hot fixes and improvements



How this may affect you: Improvements in the error handling.

   v2.0.2 - Appypay API

##### v2.0.2 - Appypay API



Date: 14/08/2023



Payment Methods affected: GPO, UMM, REF



New features: None



Fixes: POST and GET Charges general hot fixes and improvements.



How this may affect you: Improvements in the error handling.

   v2.0.1 - Appypay API

##### v2.0.1 - Appypay API



Date: 14/08/2023



Payment Methods affected: GPO, UMM, REF



New features: Support GPO payment method



Fixes: New response body for POST charges and POST refunds



How this may affect you: Upgraded version (from v1.2 to v2.0) of GPO payment method;



If using the originalSourceDetail object from response of POST charges and POST refunds, stop using. The same information will be available on sourceDetail object.



   v2.0.0 - Appypay API

##### v2.0.0 - Appypay API



Date: 03/04/2023



Payment Methods affected: UMM, REF



New features: Support REF payment methods; Accounts



Fixes: None



How this may affect you: A new payment method to charge customers; A new way to validate the user account on UMM.

---

## Charges

**Arquivo de origem:** `Payments Gateway - General Usage/Charges.html`

### Charges



💡 Process of paying online from a merchant digital platform using AppyPay Payment Gateway



Go to REST endpoints



##### Request Types



Charges endpoint supports both synchronous and asynchronous clients. By default the request will be synchronous.



###### Synchronous



In this case the client sends a request, and waits for a response with transaction result with a HTTP 200 code.





Depending on the payment method the responses can take up to 90 seconds.





###### Asynchronous



In this case the client sends a request, if accepted, is notified with a HTTP 202 code. The endpoint will continue running the task on background, sending the result of the transaction by triggering a request POST with the result.





The POST will be sent to the configured merchant Webhook (check here), and will have the same body as described as sample payload.







Use Accept header to choose the request type.


- Synchronous: application/json

- Asynchronous: application/vnd.appypay.asyncapi+json




#### Charge Operations

 Refunds

Reverse

Cancel


-  Process of refund online a payment from a merchant digital platform using AppyPay Payment Gateway




Note: It's possible to perform a partial or total refund.



This operation is only supported by GPO and UMM payment methods.



Go to REST endpoints



#### Custom options



A merchant can register two (2) custom options to be added to a charge request.



If want to use this service, please go to the AppyPay portal to configure (check how-to here) or provide the following information to your commercial manager:


-  Number of custom options

-  Name of each custom option

-  Data type

---

## Errors

**Arquivo de origem:** `Payments Gateway - General Usage/Errors.html`

### Errors



AppyPay uses conventional HTTP status codes to indicate the result of a client's request.



##### HTTP Status Codes


 | Code | Description
 | 200 - OK | It indicates that the REST API successfully carried out whatever action the client requested
 | 202 - Accepted | It indicates that the request has been accepted for processing
 | 400 - Bad Request | It indicates a generic client-side error status
 | 401 - Unauthorized | It indicates that the client tried to operate on a protected resource without providing the proper authorization
 | 403 - Forbidden | It indicates the user does not have the necessary permissions for the resource
 | 404 - Not found | It indicates that the REST API can’t map the client’s URI to a resource
 | 405 - Method Not Allowed | It indicates that the client tried to use an HTTP method that the resource does not allow
 | 415 - Unsupported Media Type | It indicates that the API is not able to process the client’s supplied media type
 | 500 - Server error | It indicates a generic API server error



##### Response structures



The HTTP `2xx`, `4xx`, `5xx` codes usually are followed by a response body with following structure:

 Charges

Funds-Transfers

References

Common Response Body for Charges

id

string<uuid>

responseStatus

object

successful

boolean

required

Indicates if successful or unsuccessful operation

status

string

Transaction status.

Allowed values:RequestedPendingSuccessFailed

code

integer

required

Unique response code.

message

string

required

Short description of the response.

source

string

Response source

Allowed values:APPYREFUMMFTBAI

sourceDetails

object


-

Please note that depending of the resource and the operation more properties can be added to the response body.



-

API support message translations in Portuguese and English. Message language depends on the Accept-Language on header or query parameter culture of the request.






#### Internal Responses



Bellow there is a list of AppyPay API responses code. They can reflect internal (gateway) and external events (Interbank Processor and payment providers).





###### Status


- Success - Operation was successful

- Pending - Operation was accepted, but not processed yet

- Cancelled - Operation was cancelled

- Failed - Operation was failed

- Expired - Operation was expired `Not available for all payments methods`


  HTTP 2xx Responses

##### HTTP 2xx Responses


 | Code | EN Message | PT Message | Description | Applies To | Supported Payment Methods
 | 100 | Thank you! The payment has been successfully registered | Obrigado! O seu pagamento foi registado com Sucesso. | Success `[Success]` | Charges, Refunds, Reverses, Funds-Transfer | FTBAI, GPO, REF, UMM
 | 101 | The request has been accepted for processing. | A solicitação foi aceita para processamento. | Successful requested `[Pending]` | Charges | GPO, REF, UMM, FTBAI
 | 102 | Payment order accepted for processing. | Ordem de pagamento aceite para processamento. | Successful requested `[Pending]` | Funds-Transfer | FTBAI
 | 103 | QR code successfully created. | QR code criado com sucesso. | Successful created `[Success]` | QR Codes | GPO
 | 200 | The payment was refused by Multicaixa Express system. If the problem persist, please contact Multicaixa Express support team. | O seu pagamento foi recusado pelo sistema Multicaixa Express. Se o problema persistir, contacte a equipa de suporte do Multicaixa Express. | The transaction was refused by the processor `[Cancelled]` | Charges | GPO
 | 201 | The payment was refused. Please try again later. | O seu pagamento foi recusado. Por favor tente novamente mais tarde. | The transaction was refused by issuer (invalid card) `[Cancelled]` | Charges | GPO
 | 206 | Failed to reach Multicaixa Express system. Please try again later. | A comunicação com o Multicaixa Express falhou. Por favor tente novamente mais tarde. | The transaction was refused by processor (establishment configuration) `[Cancelled]` | Charges | GPO
 | 208 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The transaction was refused by processor (terminal configuration) `[Cancelled]` | Charges | GPO
 | 209 | Your balance is insufficient to proceed with the transaction. Please try with another Multicaixa card | O seu saldo é insuficiente para prosseguir com a operação. Por favor tente novamente com outro cartão Multicaixa. | Insufficient funds in client's account to complete the transaction `[Cancelled]` | Charges | GPO
 | 210 | The payment term has expired. You must authorize your payment within a maximum of 90 seconds. Please try again | O prazo de pagamento expirou. Deverá autorizar o seu pagamento num prazo máximo de 90 segundos. Por favor, tente novamente. | Processor timeout `[Cancelled]` | Charges | GPO
 | 211 | The payment term has expired. You must authorize your payment within a maximum of 90 seconds. Please try again | O prazo de pagamento expirou. Deverá autorizar o seu pagamento num prazo máximo de 90 segundos. Por favor, tente novamente. | Transaction timeout `[Cancelled]` | Charges | GPO
 | 212 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank `[Cancelled]` | Charges | GPO
 | 213 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (payment limit exceed) `[Cancelled]` | Charges | GPO
 | 214 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (card blocked) `[Cancelled]` | Charges | GPO
 | 215 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (card limit) `[Cancelled]` | Charges | GPO
 | 216 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (card daily limit) `[Cancelled]` | Charges | GPO
 | 217 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The transaction was refused by processor (terminal error) `[Cancelled]` | Charges | GPO
 | 220 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer (invalid card date) `[Cancelled]` | Charges | GPO
 | 221 | The payment was refused by Multicaixa Express system. If the problem persist, please contact Multicaixa Express support team | O seu pagamento foi recusado pelo sistema Multicaixa Express. Se o problema persistir, contacte a equipa de suporte do Multicaixa Express. | The transaction was refused by the issuer `[Cancelled]` | Charges | GPO
 | 222 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (invalid card) `[Cancelled]` | Charges | GPO
 | 223 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction not authorized by issuer bank `[Cancelled]` | Charges | GPO
 | 224 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (network limit) `[Cancelled]` | Charges | GPO
 | 225 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (funds) `[Cancelled]` | Charges | GPO
 | 227 | The payment was refused by Multicaixa Express system. If the problem persist, please contact Multicaixa Express support team | O seu pagamento foi recusado pelo sistema Multicaixa Express. Se o problema persistir, contacte a equipa de suporte do Multicaixa Express. | The transaction was aborted by the processor `[Cancelled]` | Charges | GPO
 | 228 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (card captured) `[Cancelled]` | Charges | GPO
 | 229 | There was an error in the selected account. Please try with another Multicaixa card | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outro cartão Multicaixa. | The transaction was refused by issuer bank (card inoperable) `[Cancelled]` | Charges | GPO
 | 230 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The transaction was refused by processor (setup error) `[Cancelled]` | Charges | GPO
 | 231 | Payment not authorized by the customer | Pagamento não autorizado pelo cliente. | The customer declined the transaction `[Cancelled]` | Charges | GPO, UMM
 | 233 | There was an error in the account verification | Ocorreu um erro ao verificar a conta | Not possible to validate the MSISDN `[Cancelled]` | Accounts, Charges | UMM
 | 238 | The payment was refused by Unitel Money system. If the problem persist, please contact Unitel Money support team | O prazo de pagamento expirou. Deverá autorizar o seu pagamento num prazo máximo de 30 segundos. Por favor, tente novamente. | The transaction was refused by the processor `[Cancelled]` | Charges | UMM
 | 239 | The payment was refused by Unitel Money system. If the problem persist, please contact Unitel Money support team | Pagamento não autorizado pelo cliente. | The transaction was refused by the processor `[Cancelled]` | Charges | UMM
 | 240 | There was an error in the selected account. Please try with another Unitel Money account | Ocorreu um erro na conta seleccionada. Por favor tente novamente com outra conta Unitel Money. | The transaction was refused by the processor `[Cancelled]` | Charges | UMM
 | 242 | Inactive or unkown customer | Cliente inactivo ou inexistente | Inactive or unkwon account `[Cancelled]` | Accounts,Charges | UMM
 | 243 | Invalid or incorrect PIN | PIN inválido ou incorrecto | Failed on the PIN validation `[Cancelled]` | Charges | UMM
 | 244 | The payment was refused by Unitel Money system. If the problem persist, please contact Unitel Money support team | O seu pagamento foi recusado pelo sistema Unitel Money. Se o problema persistir, contacte a equipa de suporte do Unitel Money. | Internal processor Error `[Cancelled]` | Charges | UMM
 | 245 | The payment has expired. | Data de pagamento expirada | Invalid state of the reference `[Expired]` | Charges | REF
 | 246 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider server rejected the request `[Failed]` | Charges | UMM
 | 247 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider server returned an invalid parameter `[Failed]` | Charges | UMM
 | 248 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider server returned system timeout `[Failed]` | Charges | UMM
 | 249 | There is no information for this transfer. | Não há informação para este transferência. | The provider couldn't not find the transaction details `[Cancelled]` | Funds-Transfer | FTBAI
 | 301 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Provider internal system error `[Failed]` | Charges | GPO
 | 302 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Provider internal system runtime error `[Failed]` | Charges | GPO
 | 306 | Failed to reach Multicaixa Express system. Please try again later. | A comunicação com o Multicaixa Express falhou. Por favor tente novamente mais tarde. | Comunnication error `[Failed]` | Charges | GPO
 | 308 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Provider general internal error `[Failed]` | Charges | GPO
 | 309 | Failed to reach Unitel money system. Please try again later. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Communication error `[Failed]` | Charges | UMM
 | 310 | Failed to reach Unitel money system. Please try again later. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Request not accepted by party `[Failed]` | Charges | UMM
 | 311 | Failed to reach Unitel money system. Please try again later. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Internal processor Error `[Failed]` | Charges | UMM
 | 312 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider server returned an invalid or incomplete response `[Failed]` | Charges | UMM
 | 313 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider configuration is invalid or incomplete response `[Failed]` | Charges | UMM
 | 314 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Communication error `[Failed]` | Charges | UMM
 | 315 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | System error `[Failed]` | Charges | UMM
 | 316 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Internal System error `[Failed]` | Charges | UMM
 | 317 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Multiple entries for the same converstationID `[Failed]` | Charges | UMM
 | 318 | There was a funds transfer error. Some built-in features unavailable, please try again later. | Houve um erro na transferência de fundos. Alguns recursos internos indisponíveis, por favor tente novamente mais tarde. | Features unavailable `[Failed]` | Charges | FTBAI
 | 319 | Payment status is pending. We are waiting for the service provider to confirm the payment. | O pagamento está com estado pendente. Estamos a aguardar pela confirmação do prestador de serviços. | The provider unknown error `[Pending]` | Charges | GPO, UMM
 | 402 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider generic business error `[Failed]` | Charges | GPO
 | 403 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | The provider unknown business error `[Failed]` | Charges | GPO
 | 404 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Unknown Point of Sale `[Failed]` | Charges, Refunds | GPO
 | 405 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Internal Critical Error. Pending reversals `[Failed]` | Charges | GPO
 | 406 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Unable to communicate with dependent module `[Failed]` | Charges | GPO
 | 407 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Communication error due to bad request `[Failed]` | Charges | GPO
 | 408 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Requested resource doesn't exist `[Failed]` | Charges | GPO
 | 410 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Internal Error `[Failed]` | Charges | GPO
 | 411 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | System is unavailable `[Failed]` | Charges | GPO
 | 412 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Establishment inactive `[Failed]` | Charges | GPO
 | 413 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Failed to generate verification code `[Failed]` | Charges | UMM
 | 414 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Sign-out state `[Failed]` | Charges | UMM
 | 415 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Service failure `[Failed]` | Charges | UMM
 | 416 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Abnormal identity status `[Failed]` | Charges | UMM
 | 417 | The payment was refused by UNITEL Money system. If the problem persist, please contact UNITEL Money support team. | O seu pagamento foi recusado pelo sistema UNITEL Money. Se o problema persistir, contacte a equipa de suporte do UNITEL Money. | Identity failure `[Failed]` | Charges | UMM
 | 418 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Invalid identity `[Failed]` | Charges | UMM
 | 440 | There was a payment error. Please try again later. | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Inactive POS `[Failed]` | Charges | GPO
 | 900 | There was a payment error. Please try again later | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Unknow transaction error `[Failed]` | Charges, Refunds | GPO, UMM
 | 901 | There was a payment error. Please try again later | Houve um erro no pagamento. Por favor tente novamente mais tarde. | Unknow provider error `[Failed]` | Charges, Refunds | GPO, UMM
 | 1100 | Active account | Conta activa | Active Account `[Success]` | Accounts | UMM
 | 1101 | Suspended account | Conta suspensa | Inactive Account `[Failed]` | Accounts | UMM
 | 1102 | Frozen account | Conta congelada | Inactive Account `[Failed]` | Accounts | UMM
 | 1103 | Closed account | Conta encerrada | Inactive Account `[Failed]` | Accounts | UMM
 | 1104 | Capped account | Conta limitada | Inactive Account `[Failed]` | Accounts | UMM
 | 1105 | Dormant | Conta inactiva | Inactive Account `[Failed]` | Accounts | UMM
 | -1 | Unknown | Desconhecido | General unknown error `[Failed]` | All | FTBAI, GPO,REF, UMM

   HTTP 4xx Responses

##### HTTP 4xx Responses


 | Code | EN Message | PT Message | Description | Applies To | Supported Payment Methods
 | 717 | Phone number missing. Please try again. | Não forneceu a número de telefone. Por favor tente novamente. | Phone number not provided `[Failed]` | Charges | GPO, UMM
 | 718 | Amount has to be greater than zero (0). Please try again | O valor do pagamento tem que ser superior a zero (0). Por favor tente novamente. | The transaction amount is invalid `[Failed]` | Charges, Refunds, Funds-Transfer | FTBAI, GPO, REF, UMM
 | 719 | Field(s) `[XXXX]` not provided | Campo `[XXXX]` não providenciado | The required field `[XXXX]` was not provided `[Failed]` | All | FTBAI, GPO, REF, UMM
 | 720 | Transaction `[XXXX]` was not found | A transação `[XXXX]` não encontrada | Unkown or inexisting transaction ID `[Failed]` | Charges, Refunds, Cancelations | GPO, REF, UMM
 | 726 | The requested reference number `[XXXX]` already exists | A referência do comerciante `[XXXX]` solicitado já existe. | Duplicated resource `[Failed]` | Charges | GPO, REF, UMM
 | 759 | Amount has to be greater than forty nine (49). Please try again. | O valor do pagamento tem que ser superior a quarenta e nove (49). Por favor tente novamente. | Minimum amount restriction `[Failed]` | Charges | UMM
 | 760 | Refund amount request can not be more than amount paid. | Solicitação de valor de reembolso não pode ser superior ao valor pago. | Invalid refund amount `[Failed]` | Refunds | GPO, UMM
 | 761 | Reverse amount request can not be more than amount paid. | Solicitação de valor de reversão não pode ser superior ao valor pago. | Invalid reverse amount `[Failed]` | Reverses | UMM
 | 762 | Due Date can not be less than current dateTime | A data de vencimento não pode ser menor que a data/hora atual | Invalid reference due date `[Failed]` | Charges | REF
 | 763 | Reference number `[XXXX]` already exists | Número de referência `[XXXX]` já existe | Duplicated resource `[Failed]` | Charges | REF
 | 800 | Request is null or with wrong format. | O pedido é nulo ou com formato incorrecto. | Request is null or with wrong format `[Failed]` | Charges, Funds-Transfer | FTBAI, GPO, REF, UMM
 | 803 | Invalid custom options | Opções do comerciante inválidas | Invalid custom options were provided `[Failed]` | Charges | GPO, REF, UMM
 | Generic-error | `[XXXX]` | `[XXXX]` | Generic message `[Failed]` | All | FTBAI, GPO, REF, UMM
 | -1 | Unknown | Desconhecido | General unknown error `[Failed]` | All | FTBAI, GPO, REF, UMM





Note: HTTP 401 errors can have a specific body, please check examples in each endpoint.



   HTTP 5xx Responses

##### HTTP 5xx Responses


 | Code | Message | Description | Applies To | Supported Payment Methods
 | Generic-error | `[XXXX]` | Generic message `[Failed]` | All | FTBAI, REF, UMM
 | -1 | Unknown | General unknown error `[Failed]` | All | FTBAI, GPO,REF, UMM



#### Error Handling Actions



To handle errors, some actions can be used:


-  For HTTP `2XX` codes responses - show the message to final user and update payment status to the one stated in the description.

-  For HTTP `4XX` and `5XX` codes responses - verify if variables and constraints are correctly implemented. Try again. If persists, contact AppyPay support.
    Deprecated Responses

#### Deprecated Responses


 | Code | Message | Description | Applies To | Supported Payment Methods
 | 202 | There was an error in the selected account. Please try with another Multicaixa card | The transaction was refused by issuer bank (transaction limit) `[Cancelled]` | Charges | GPO
 | 203 | Your balance is insufficient to proceed with the transaction. Please try with another Multicaixa card. | Invalid balance `[Cancelled]` | Charges | GPO
 | 204 | Your balance is insufficient to proceed with the transaction. Please try with another Multicaixa card. | Invalid balance `[Cancelled]` | Charges | GPO
 | 205 | Failed to reach the Multicaixa Express system. Please try again later `[Cancelled]` | Internal system communication | Charges | GPO
 | 207 | There was a payment error. Please try again later | Invalid client origin `[Cancelled]` | Charges | GPO
 | 218 | There was a payment error. Please try again later | Internal error `[Cancelled]` | Charges | GPO
 | 219 | Payment not authorized by the customer | The customer declined the transaction `[Cancelled]` | Charges | GPO
 | 226 | The payment was refused by Multicaixa Express system. If the problem persist, please contact Multicaixa Express support team. | Transaction aborted `[Cancelled]` | Charges | GPO
 | 500 | There was a payment error. Please try again later. | Bad reference `[Failed]` | Charges | GPO
 | 501 | There was a payment error. Please try again later. | Unable to process an authorization `[Failed]` | Charges | GPO
 | 502 | There was a payment error. Please try again later. | Unable to process an authorization. Invalid state `[Failed]` | Charges | GPO
 | 503 | This transaction was already debited (captured). | Unable to process an authorization. Invalid amount `[Failed]` | Charges Capture | GPO
 | 504 | This transaction was already debited (captured). | Unable to process payment. Invalid state `[Failed]` | Charges Capture | GPO
 | 505 | This transaction was already debited (captured). | Unable to process payment. Invalid amount `[Failed]` | Charges Capture | GPO
 | 507 | This transaction was already cancelled. | Unable to process cancellation `[Failed]` | Charges Cancellations | GPO
 | 508 | This transaction was already cancelled. | Unable to process cancellation. Invalid state `[Failed]` | Charges Cancellations | GPO
 | 801 | Application `[XXXX]` not found | Invalid application `[Failed]` | All | All
 | 802 | Invalid payment method | Invalid payment method `[Failed]` | All | All

---

## Fiscal Documents

**Arquivo de origem:** `Payments Gateway - General Usage/Fiscal Documents.html`

### Fiscal Documents



💡 Service for creating electronic fiscal documents compliant with SAF-T(AO) and Angolan Administração Geral Tributária (AGT) requirements.



Go to REST endpoints



#### Supported Document Types



Refers to the following list to see the available fiscal documents and the ones supported by our services.


 | Type | Name | Description | Notes | Supported
 | FA | Factura de Adiantamento | Advance Invoice |  | -
 | FT | Factura | Invoice | Default | ✅
 | FR | Factura/Recibo | Invoice/Receipt |  | ✅
 | FG | Factura Global | Global Invoice |  | -
 | GF | Factura Genérica | Generic Invoice |  | -
 | AC | Aviso de Cobrança | Collection Notice |  | -
 | AR | Aviso de Cobrança/Recibo | Collection Notice/Receipt |  | -
 | TV | Talão de Venda | Sales Slip |  | -
 | RC | Recibo Emitido | Receipt Issued |  | -
 | RG | Recibo | Receipt |  | -
 | RE | Estorno ou Recibo de Estorno | Reversal or Reversal Receipt |  | -
 | ND | Nota de Débito | Debit Note |  | -
 | NC | Nota de Crédito | Credit Note |  | -
 | AF | Factura/Recibo de Autofacturação | Self-Billing Invoice/Receipt |  | -
 | RP | Prémio ou Recibo de Prémio | Premium or Premium Receipt |  | -
 | RA | Resseguro Aceite | Reinsurance Accepted |  | -
 | CS | Imputação a Co-seguradoras | Allocation to Co-insurers |  | -
 | LD | Imputação a Co-seguradora Líder | Allocation to Lead Co-insurer |  | -



#### Complementary Options



Refers to the following list to see the available options for fiscal documents.



##### Operation Types


 | Type | Name | Description | Notes
 | SE | Prestação de serviços de educação | Provision of education services |
 | SS | Prestação de serviços de saúde | Provision of health services |
 | STP | Prestação de serviços de transporte de passageiros | Provision of passenger transport services |
 | SR | Prestação de serviços sujeitos a royalties | Provision of services subject to royalties |
 | SIF | Prestação de serviços de intermediação financeira ou seguradora | Provision of financial intermediation or insurance services |
 | SHS | Prestação de serviços de hotelaria e similares | Provision of hotel and similar services |
 | ST | Prestação de serviços de telecomunicações | Provision of telecommunications services |
 | SG | Prestação de serviço (geral - outros) | Provision of services (general - others) | Default
 | TB | Transmissão de bens | Transfer of goods |
 | AS | Arrendamento e subarrendamento | Leasing and subleasing |
 | QT | Quotas | Quotas |
 | RD | Repasse de despesas | Transfer of expenses |



##### Tax Types


 | Type | Name | Description | Notes
 | IVA | Imposto s/ o Valor Acrescentado | Value Added Tax | Default
 | IS | Imposto de Selo | Stamp Duty |
 | IEC | Imposto Especial de Consumo | Special Consumption Tax |
 | CEOC | Contribuição Especial de Consumo | Special Consumption Contribution |
 | NS | Não sujeito a IVA, IS, IEC ou CEOC | Not subject to VAT, IS, IEC, or |



##### Tax Codes


 | Type | Name | Description | Notes
 | NOR | Taxa normal | Standard rate |
 | INT | Taxa intermédia | Intermediate rate |
 | RED | Taxa reduzida | Reduced rate |
 | ISE | Isento | Exempt |
 | OUT | Outra | Other |



##### Withholding Tax Types


 | Type | Name | Description | Notes
 | IVA | Imposto s/ o Valor Acrescentado | Value Added Tax |
 | IRT | Imposto Sobre os Rendimentos do Trabalho | Income Tax |
 | II | Imposto Industrial | Industrial Tax |
 | IS | Imposto de Selo | Stamp Duty |
 | IP | Imposto Predial | Property Tax |
 | IAC | Imposto sobre Aplicação de Capitais | Capital Gains Tax |
 | OU | Outros | Others |
 | IRPC | Imposto s/ rendimento de pessoas colectivas (impostos futuros) | Tax on the income of legal persons (future taxes) |
 | IRPS | Imposto s/ rendimento de pessoas singulares (impostos futuros) | Tax on the income of natural persons (future taxes) |



#### Fiscal Documents Integration Guide



This integration allows you to automatically create fiscal documents through our system.


-

Get a Token
 Your system connects to our platform and securely authenticates. Check this article to see how you can authenticate.



-

Create a Fiscal Document
 You send the document details (such as invoice or invoice/receipt) to our API. Go to REST endpoints



-

Document Processing
 We process the request and submit the document to the tax authority for validation.



-

Notification
 Once the document is ready, we notify your system using a webhook. Check this article to know about webhooks.



-

Retrive the Document
 The webhook includes a secure URL that you can use to retrieve the official fiscal document.




For error handling please check this article.

---

## Funds-Transfers

**Arquivo de origem:** `Payments Gateway - General Usage/Funds-Transfers.html`

### Funds-Transfers



💡 Process of tranfer funds from one bank account to another using AppyPay Payment Gateway.





###### Funds-transfers types:


-

Intrabank: The transfer happen within bank accounts of the same bank



-

Interbank: The transfer happen within bank accounts of different banks.






Go to REST endpoints



#### Supported Banks



##### Debitor Banks


-  Banco Angolano de Investimentos (BAI)


##### Creditor Banks


-  Banco Angolano de Investimentos (BAI)


##### ISO Codes



Codes that can be used to identify the funds transfer.



###### Category Codes


 | Code | PT Description | EN Description
 | CASH | Pagamentos | Payments
 | GOVT | Reembolsos do Estado | State refunds
 | OTRF | Outros | Others
 | PENS | Pensões/Abonos | Pensions
 | SALA | Salários | Salary
 | SSBE | Segurança Social | Social Security
 | SUPP | Fornecedores | Suppliers
 | TAXS | Taxas ou Impostos - Entidade do Estado | Taxes - State entities
 | TRAD | Mercadoria | Trade



###### Reason Codes


 | Code | PT Description | EN Description | Category Code
 | CASH | Pagamentos | Payments | CASH
 | RINP | Pagamento de retorno da prestação | Installment payments | CASH
 | GOVT | Reembolsos do Estado | State refunds | GOVT
 | AIRB | Pagamento de transporte aéreo | Air transport payments | OTRF
 | FERB | Pagamento de transporte marítimo | Sea transport payments | OTRF
 | HSPC | Cuidados hospitalares | Hospital care | OTRF
 | MDCS | Serviços médicos | Medical services | OTRF
 | OTRH | Outros meios de transporte | Other transportation | OTRF
 | UTIL | Uitilidades | Uitilities | OTRF
 | ALMY | Pagamento de pensão alimentar | Alimony payments | PENS
 | BECH | Abono de família | Family allowance | PENS
 | PENS | Pensões/Abonos | Pensions | PENS
 | SALA | Salários | Salary | SALA
 | BENE | Desemprego | Unemployment | SSBE
 | SSBE | Segurança Social | Social Security | SSBE
 | MSVC | Serviços diversos | Multiple Services | SUPP
 | NWCH | Pagamento de comunicações | Communication payments | SUPP
 | OTLC | Pagamento de comunicações (outras) | Communication payments (others) | SUPP
 | RCPT | Pagamento de recibo | Receipt payments | SUPP
 | CMDT | Pagamento de mercadorias | Goods payments | TRAD
 | ENRG | Pagamento de energia | Energy payments | TRAD
 | GDDS | Pagamento de bens | Goods payments | TRAD
 | SCVE | Compra/venda de serviços | Purchase/sale of services | TRAD
 | SUPP | Fornecedores | Suppliers | TRAD
 | TRAD | Mercadoria | Trade | TRAD



###### Fee Payer Codes


 | Code | PT Description | EN Description
 | BEN | Despesa do credor/beneficiário | Creditor/beneficiary expense
 | OUR | Despesa do devedor/ordenante | Debtor/payer expense
 | SHA | Despesa compartilhada | Shared expense

---

## Migration Guide v1.2 to v2.0

**Arquivo de origem:** `Payments Gateway - General Usage/Migration Guide v1.2 to v2.0.html`

### Migration Guide v1.2 to v2.0



💡In the following article one will find important notes and the major changes that need to be taken in considation when migrating from the legacy version (v1.2) to the major version (v2.0).

   Get Token

Changes on Request: The Get Token URL has changed to this https://login.microsoftonline.com/auth.appypay.co.ao/oauth2/token







The old URL will be descontinued by end of November 2024. So by that date the DNS will only point to the new URL.







🔑 Make sure to create or request new merchant credentials.





Payment Methods affected: ALL



New features: None


- Go to Get Token to get the detailed documentation.
     POST Charges

Changes on Request: The URL has changed to this https://gwy-api.appypay.co.ao/v2.0/charges







REMOVED: orderOrigin and the capture properties.







ADDED: currency proprerty and notify as a new feature.





Changes on Response:







REMOVED: originalSourceDetails property.







ADDED: status and reference proprerty as a new payment method.





Payment Methods affected: GPO, UMM, REF



New features: Notify and Reference (REF)


- Go to Post a Charge to get the detailed documentation.
     POST Refunds

Changes on Request: The URL has changed to this https://gwy-api.appypay.co.ao/v2.0/refunds/{id}







REMOVED: N/A







ADDED: description property





Changes on Response:







REMOVED: originalSourceDetails property







ADDED: status property.





Payment Methods affected: GPO, UMM



New features: None


- Go to Post a charge refund to get the detailed documentation.

---

## References

**Arquivo de origem:** `Payments Gateway - General Usage/References.html`

### References



💡 Payment references can be registed previous in the Gateway.



Go to REST endpoints



##### References Types



References can have:


- Fixed amount - when creating a reference pass the desired amounts in the amounts variable

- Free amount - when creating a reference pass minAmount and maxAmount

---

## Supported Payment Methods

**Arquivo de origem:** `Payments Gateway - General Usage/Supported Payment Methods.html`

### Supported Payment Methods


-  UMM - Unitel Mobile Money

-  REF - Payments by sector (References)

-  FTBAI - Interbank funds-transfers (BAI) [BETA]

-  GPO - Gateway de Pagamentos Online

-  eTPA - eTerminal de Pagamentos Automatico [BETA]

-  SDD - Sistema de Débito Directo [ALPHA]




Payment method identifiers (GPO, UMM, REF, FTBAI, eTPA, SDD) are used in post charges requests with api key.





#### Payment Methods Summary



##### Financial operations


 | Operations | UMM | REF | FTBAI | GPO | eTPA | SDD
 | Charges | ✅ | ✅ | - | ✅ | ✅ | ✅
 | Refunds | ✅ | - | - | ✅ | ✅ | ✅
 | Reverses | ✅ | - | - | - | - | -
 | Funds Transfers | - | - | ✅ | - | - | -
 | References | - | ✅ | - | - | - | -
 | Cancellation | - | - | - | - | - | ✅



##### Validations and Limitations


 | Rule | UMM | REF | FTBAI | GPO | eTPA | SDD
 | Mininum charge amount | 50 AOA | - | - | 1 AOA | 1 AOA | -
 | Approval time | 30s | - | 300s | 90s | 90s | 10 days
 | Payment expiration | - | ✅ | - | - | - | -
 | Default expires in | - | 72h | - | - | - | -
 | Reference number length | - | 9 - 15 digits | - | - | - | -
 | Accounts | ✅ | - | - | - | - | -
 | Daily limit | - | - | 500.000.000.000,00 AOA | - | - | -
 | Webhook | Required for async request | Always required | - | Required for async request | Required for async request | -





For payment methods that allow payment expiration, if the user do not pass due date, the default expires in hours will be summed to the transaction creation date as payment due date.





#### Payment Methods Details

 GPO

UMM

REF

FTBAI

eTPA

SDD

Phone-based online payment. For this payment method, the customer must authorize the payment on MCX App.



To authorize GPO payments, the customer must have the MCX App installed and configured with his phone number.



Whant to know about MCX App? Check here.

Detailed paymentInfo

What should be passed inside paymentInfo object for GPO payment method

paymentInfo

object

phoneNumber

string

required

Phone number to be charged. It supports with or without country code.

>= 9 characters<= 15 characters

Example:922111123 or 244922111123



Get in touch to know more about our supported payment methods and how to subsribe the service.

---

## Web App How-to

**Arquivo de origem:** `Payments Gateway - General Usage/Web App How-to.html`

### Web App How-to



💡 In the following article we explain how one can use the AppyPay web app to manage the services, like adding multiple payment methods, credentials, users and other features.



Go to AppyPay Web APP





This article is still under construction. An amazing content is coming!





How to login



How to edit merchant detail



How to add custom option



How to manage applications (Payment Methods)



How to manage API Keys



How to manage Webhook configurations



How to manage API credentials (Client ID and Secret)



How to manage Widget secrets



How to manage users



How to make a online payment (via web or mobile app)



How to generate charges link



How to make a refund (GPO and UMM only)

---

## Merchant Webhooks

**Arquivo de origem:** `Payments Gateway - General Usage/Merchant Webhooks.html`

### Merchant Webhooks





##### Webhook requirements for Merchants:


- Provide a HTTP or HTTPS public accessible endpoint

- Payload – JSON encoded

- To acknowledge receipt, the endpoint should return a 200 HTTP status code as response. All other response codes will indicate that the payment was not received

- For authorization we support Basic Auth (username and password) and API Key




#### Charges Webhook (Transactional Webhook)



💡 A transactional webhook is a callback function that allows event-driven communication between 2 APIs.


-  AppyPay can POST data to merchant application when payments occur with payment status.

-  The AppyPay Webhook will be mandatory if payment Widget is used and for REF payments.


##### Charges Sample Payload



```
Sample Webhook

1

POST {URL}

2

Content-Type: application/json

3

{

4

    "id": "56985af8-7256-408c-8e71-99d63dd2074b",

5

    "merchantTransactionId":"030000000301201",

6

    "amount":100,

7

    "options": {

8

        "SmartcardNumber": "Smart_card_Number",

9

        "MerchantOrigin": "Merchant_Origin"

10

    },

11

    "directDebit":{

12

      "MerchantReferenceNumber":"AB123456",

13

      "ProcessedDate":"2025-10-03",

14

      "TransactionDescription":"Automoveis",

15

      "ProviderInstructionId":"000000000001234"

16

    },

17

    "reference": {

18

        "referenceNumber": "123456789",

19

        "dueDate": "2022-01-01T15:00:00",

20

        "entity":"00123"

21

    },

22

    "eletronicReceipt": {

23

      "customerReceipt": "TUlOSVNURVJJTyBEQVMgICAgICANCkZJTkFOQ0FTICAgICAgICAgICAgDQpSZXBhcnRpY2FvIG91ICAgICAgIA0KRGVwYXJ0YW1lbnRvICAgICAgICANCk5JRjogNTAwMDM5MzUzMyAgICAgDQpJZGVudC4gVFBBOiAwMDAwMTkzMg0KIDI1LTA3LTAzICAxNjowODozMQ0KUGVyOjAxMiBUcjowMDYgTWc0NTkNCkJhbmNvIEFuZ29sYW5vIGRlIEluDQogICoqKioqKioqKioqKjM4MTggIA0KVEM6IDQxMzI5OTEzQ0MwODBFMjENCkEwMDAwMDA2OTAwMjAwICAgICAgDQogIE11bHRpQ2FpeGEgICAgICANCiAgICAgICBDT01QUkENCiAgICAgICAgICBLWiAyNTAwLDAwDQoNCiAgICBD01BJQSBDTElFTlRFDQpQQUdVRSBDT00gQ9NESUdPIFFSIA0KDQoNCg==",

24

      "merchantReceipt": "TUlOSVNURVJJTyBEQVMgICAgICANCkZJTkFOQ0FTICAgICAgICAgICAgDQpSZXBhcnRpY2FvIG91ICAgICAgIA0KTklGOiA1MDAwMzkzNTMzICAgICANCklkZW50LiBUUEE6IDAwMDAxOTMyDQogMjUtMDctMDMgIDE2OjA4OjMxDQpQZXI6MDEyIFRyOjAwNiBNZzQ1OQ0KQmFuY28gQW5nb2xhbm8gZGUgSW4NCiAgKioqKioqKioqKioqMzgxOCAgDQpUQzogNDEzMjk5MTNDQzA4MEUyMQ0KQTAwMDAwMDY5MDAyMDAgICAgICANCiAgTXVsdGlDYWl4YSAgICAgIA0KICAgICAgIENPTVBSQQ0KICAgICAgICAgIEtaIDI1MDAsMDANCiAgQ9NQSUEgQ09NRVJDSUFOVEUNCg0KDQo="

25

    },

26

    "responseStatus": {

27

        "successful": true,

28

        "status": "Success",

29

        "code": 100,

30

        "message": "Obrigado! O seu pagamento foi registado com Sucesso.",

31

        "source": "GPO",

32

        "sourceDetails": {

33

          "attempt": 1,

34

          "type": "NONE",

35

          "code": "NONE",

36

          "message": "OK"

37

        }

38

    }

39

}

```

  Parameters

id

string<uuid>

required

Identifier of the transaction

merchantTransactionId

string

required

A unique identifier of the transaction

>= 1 characters<= 15 characters

Match pattern:^[a-zA-Z0-9]+$

amount

number<double>

required

Amount charged. Decimal separator (.)

>= 1

Example:225.7

options

object

Custom options for the merchant

directDebit

object

Direct Debit object

MerchantReferenceNumber

string

Merchant Contract Reference Number. Only available for SDD payments

ProcessedDate

string<date-time>

Payment date. Only available for SDD payments

TransactionDescription

string

Payment Description. Only available for SDD payments

reference

object

Reference object

referenceNumber

string

Payment reference. Only available for REF payments

>= 9 characters<= 15 characters

dueDate

string<date-time>

Payment reference due date. Only available for REF payments

entity

string

Payment entity. Only available for REF payments

eletronicReceipt

object

Receipt object

customerReceipt

string

Customer Receipt. Only available for eTPA payments

merchantReceipt

string

Merchant Receipt. Only available for eTPA payments

responseStatus

object

required

Detailed response status

successful

boolean

Indicates if successful or unsuccessful operation

status

string

Transaction status.

Allowed values:RequestedPendingSuccessFailed

code

integer

Unique response code.

message

string

Short description of the response.

source

string

Response source

Allowed values:APPYREFUMMFTBAISDD

sourceDetails

object

Details of the source



###### Supported Methods



-`POST`





Important: The webwook can be triggered more than 1 time for the same transaction in the following cases:


- The transaction is pending due to communication issues with providers

- For REF payments that reflects the number of communications with the provider (for a single payment and the compensation file as summary).


Important: As a security measure, double check the transaction by calling the GET /charges endpoint passing the transaction Id received.





#### Non-Transactional Webhooks



💡 The non-transactional webhook is a callback function that allows event-driven communication between 2 APIs for events that are not directly related to payments.



The following services support non-transactional webhooks:


- SDD

- Fiscal documents




For Direct Debit (SDD): This webhook is used to communicate Direct Debit Mandate statuses updates. When configured this is called on every mandate status update.







For Fiscal documents: This webhook is used to communicate fiscal documents status updates. When configured this is called when document is processed by the tax authority.




-  AppyPay can POST data to merchant application when a particular event unrelated to payments occur within the gateway.


##### Non-transactional Sample Payload

 Direct Debit (SDD)

Fiscal documents

```
Sample Non-transactional Webhook Call from AppyPay Gateway For SDD

1

POST {URL}

2

Content-Type: application/json

3

{

4

  "directDebit":{

5

    "id": 32,

6

    "mandateStatus": "Requested",

7

    "merchantReferenceNumber": "AB123456",

8

    "debitStartDate": "2025-09-24T00:00",

9

    "debitEndDate": "2026-09-24T00:00",

10

    "maxAmount": 100.00,

11

    "providerMandateId": "0000000012345"

12

  },

13

  "responseStatus": {

14

        "successful": true,

15

        "status": "Success",

16

        "code": 100,

17

        "message": "Obrigado! O seu mandato foi registado com Sucesso.",

18

        "source": "SDD",

19

        "sourceDetails": {

20

          "attempt": 1,

21

          "type": "NONE",

22

          "code": "NONE",

23

          "message": "OK"

24

        }

25

    }

26

}

27

}

```

Parameters

DirectDebit

object

Direct Debit object

Id

number

Mandate Id. Only available for SDD payments

MandateStatus

string

Mandate Status as seen in GET /mandate-status. Only available for SDD payments

Allowed values:RequestedPendingActiveFailedExpired

MerchantReferenceNumber

string

Merchant Contract Reference Number. Only available for SDD payments

DebitStartDate

string<date-time>

Allowed debit start date for mandate. Only available for SDD payments

DebitEndDate

string<date-time>

Allowed debit end date from mandate. Only available for SDD payments

MaxAmount

number<double>

Example:100.00

ProviderMandateId

string

Id of the mandate in payment provider. Only available for SDD payments

responseStatus

object

required

Detailed response status

successful

boolean

Indicates if successful or unsuccessful operation

status

string

Transaction status.

Allowed values:RequestedPendingSuccessFailedExpired

code

integer

Unique response code.

message

string

Short description of the response.

source

string

Response source

Allowed values:APPYREFUMMFTBAISDD

sourceDetails

object

Details of the source



###### Supported Methods


- `POST`

---

## Widget

**Arquivo de origem:** `Payments Gateway - General Usage/Widget.html`

### Widget



💡 A Widget is a component of an interface, that enables a user to perform a function or access a service.





The AppyPay Charges Widget v2 enhances your website by providing a versatile payment solution that is secure, easy to integrate, and supports a variety of payment methods. With the inclusion of Unitel Mobile Money, the ability to generate a payment reference, this widget meets a wide range of payment needs.





#### Features


- Multiple Payment Methods: Enables transactions through GPO, UMM, and generating payment references.

- Security and Compliance: Advanced security protocols to protect transactions.

- Easy Integration: A few lines of code is all it takes to add to your website.

- Responsive Design: Fully adaptable to any device, ensuring a seamless user experience.


#### Installation



##### Step 1: Obtain API Credentials





Secure your `data-api-key` and `data-client-id` from your AppyPay account.





##### Step 2: Embed the Script



Place the following script in the HTML of your webpage, ideally on the head section:



```
<script src="<https://widget.appypay.co.ao/main.js>"

    id="appyPay-charges-widget-v2"

    data-merchant-name="your-legal-name"

    data-api-key="your-api-key"

    data-client-id="your-client-id"

    async>

</script>

```





Replace `your-api-key`, `your-legal-name` and `your-client-id` with the credentials provided to you by AppyPay.





Find more examples bellow.



##### Step 3: Test



After embedding the script, load your website to ensure the widget is displayed and functioning properly. Conduct test transactions to validate the setup.



#### Widget Views



Here is what the AppyPay Charges Widget v2 looks like on different devices:


- Mobile View:



- Desktop View:




These images show the widget in various states, offering a preview of how it integrates visually with a website.



#### Configuration Options



##### Data Attributes



Here is the mandatory and optional data attributes you can use to set up the widget:

 Attributes

data-api-key

string<uuid>

required

Your API key for AppyPay services.

data-client-id

string<uuid>

required

The client ID for your account.

data-request-type

string

`async` - Charges request returns you a webhook as call-back containing charges state and details for the pending request.
 `sync` - Charges are handled by the Widget, depending on payment method the Portal shows a progress or result page.

Allowed values:asyncsync

Default:sync

data-redirect-uri

string<uri>

Self hosted endpoint that serves as a callback URI to handle charges. Redirects are conditioned to the request type `async`.

data-merchant-name

string

required

Your legal designation that will be displayed for end users.

data-payment-amount

number<double>

Inform a static amount that will be charged.

Example:225.7

data-payment-description

string

Inform the payment description that will be shown on the charge details.

data-phone-number

number

The payee phone number associated with one or more payment methods.

Example:923111111

data-merchant-tx-id

string

A custom merchant transaction identifier.

Match pattern:^[a-zA-Z0-9]+$

data-merchant-logo-url

string

data-options

object

Custom options defined on the AppyPay Portal

customKey

string

Your custom option name.

Example:AB202320202202

data-lang

string

Language of the widget UI.

Allowed values:pt-PTen

Default:pt-PT



##### Examples



Here are some practical examples demonstrating how to customize the AppyPay Widget by using various configuration options tailored to different business needs:

 Example 1 - Basic setup with mandatory attributes

Example 2 - Fixed payment amount and description

Example 3 - Asynchronous transactions with callback URI

Example 4 - Enhanced user experience with merchant branding

Example 5 - Multi-language and advanced custom Options

This example is a simple setup including all mandatory attributes for a straightforward integration.

```
<script src="<https://widget.appypay.co.ao/main.js>"

    id="appyPay-charges-widget-v2"

    data-merchant-name="Your Legal Name"

    data-api-key="your-api-key"

    data-client-id="your-client-id"

    async>



</script>

```



These examples provide a foundation for implementing the AppyPay Widget tailored to different e-commerce scenarios, from basic setups to more complex, feature-rich implementations.



#### Best Practices


- Security: Always ensure your website uses HTTPS.

- Testing: Thoroughly test the widget after integration and before going live.

- Updates: Keep the widget updated to utilize the latest features and security enhancements.


#### Troubleshooting



Issues with the widget can often be resolved by checking:


- Correctness and validity of the API key and client ID.

- Script tag placement and no conflicts with other scripts.

- Browser console for errors that can provide insights into issues.




For further support, contact the AppyPay technical support team.

---

## AppyPay-Web-API

**Arquivo de origem:** `APIS/AppyPay-Web-API/AppyPay-Web-API.html`

### AppyPay-Web-API

Export

v2.0

API Base URL

DEV:https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}

Mock Server:https://stoplight.io/mocks/appypay/appypay-payment-gateway/191078470

Additional Information

Contact Daniel Cohen

Backbone for AppyPay Web Portals.





All the endpoints have a mandatory usercontext. It means, that the content presented or created is linked to the authenticated user.





💡 It uses the OData URL conventions: http://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part2-url-conventions.html



Versioning:


- v2.0

---

## AppyPay-API

**Arquivo de origem:** `APIS/AppyPay-API/AppyPay-API.html`

### AppyPay-API

Export

v2.0

API Base URL

TEST:https://gwy-api-tst.appypay.co.ao/{version}

PROD:https://gwy-api.appypay.co.ao/{version}

Mock Server:https://stoplight.io/mocks/appypay/appypay-payment-gateway/44997391

Additional Information

Contact Daniel Cohen

The backbone of the AppyPay payments gateway.





Current API version: v2.0

---

## AppyPay-Authentication

**Arquivo de origem:** `APIS/AppyPay-Authentication/AppyPay-Authentication.html`

### AppyPay-Authentication

Export

v1.0

API Base URL

Token - TEST :https://login.microsoftonline.com/appypaydev.onmicrosoft.com/oauth2

Token - PROD:https://login.microsoftonline.com/auth.appypay.co.ao/oauth2

Mock Server:https://stoplight.io/mocks/appypay/appypay-payment-gateway/63461033

Additional Information

Contact Daniel Cohen

---

## Get a token

**Arquivo de origem:** `APIS/AppyPay-Authentication/Get a token.html`

### Get a token

get

https://login.microsoftonline.com/appypaydev.onmicrosoft.com/oauth2/token

The merchant digital platform needs to login to Payment Gateway service before calling any endpoint for payments.





If Authentication and Authorization is accepted, merchant digital Platform gets the Bearer Token as response



If Authentication and Authorization fails, merchant digital Platform is unable to access Payment Gateway







Token will expire every 1 hour







Merchant credentials can be generated in AppyPay Portal or request your commercial manager.



#### Request

Security: OAuth 2.0

##### Headers

Content-Type

string

required

Describes the format the body of your request is being sent as

Example:application/x-www-form-urlencoded

##### Body

application/x-www-form-urlencoded

application/x-www-form-urlencoded

```
Sample cURL

1

curl --location --request GET '{{server}}/token' \

2

--header 'Content-Type: application/x-www-form-urlencoded' \

3

--data-urlencode 'grant_type={{grant_type}}' \

4

--data-urlencode 'client_id={{client_id}}' \

5

--data-urlencode 'client_secret=I{{client_secret}}' \

6

--data-urlencode 'resource={{resource}}'

```



The example data for client_id and client_secret are for information purposes only. Generate your credentials in the AppyPay portal or request your commercial manager.

grant_type

string

required

Supported grants: client_credentials

client_id

string

required

Merchant Client_ID

client_secret

string

required

Merchant Client_Secret

resource

string<uuid>

required

Merchant_Resource

Default:2aed7612-de64-46b5-9e59-1f48f8902d14

Example:2aed7612-de64-46b5-9e59-1f48f8902d14

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

token_type

string

required

expires_in

string

required

ext_expires_in

string

required

expires_on

string

required

not_before

string

required

resource

string

required

access_token

string

required

Auth

Token:

Parameters

Content-Type*:

Body

grant_type*:

client_id*:

client_secret*:

resource*:

Send API Request

Token - TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://login.microsoftonline.com/appypaydev.onmicrosoft.com/oauth2/token \

  --header 'Accept: application/json' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: '

```

Response Example

```
1

{

2

  "token_type": "Bearer",

3

  "expires_in": "3599",

4

  "ext_expires_in": "3599",

5

  "expires_on": "1626173575",

6

  "not_before": "1626169675",

7

  "resource": "2aed7612-de64-46b5-9e59-1f48f8902d14",

8

  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Im5PbzNaRHJPRFhFSzFqS1doWHNsSFJfS1hFZyIsImtpZCI6Im5PbzNaRHJPRFhFSzFqS1doWHNsSFJfS1hFZyJ9.eyJhdWQiOiIyYWVkNzYxMi1kZTY0LTQ2YjUtOWU1OS0xZjQ4Zjg5MDJkMTQiLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC8wYWY3ODU2YS1kMWQzLTRiYjctYmY3MS1jMDE0ZWFmNjVlYjEvIiwiaWF0IjoxNjI2MTY5Njc1LCJuYmYiOjE2MjYxNjk2NzUsImV4cCI6MTYyNjE3MzU3NSwiYWlvIjoiRTJaZ1lHZzFpSzc0RTNLTE9aVHQ2TGRLMjRhSEFBPT0iLCJhcHBpZCI6IjY2ZmM5NGU1LTkzOTAtNDM3Ny1hNDc0LWFhYzEyMGU5NGUzNiIsImFwcGlkYWNyIjoiMSIsImlkcCI6Imh0dHBzOi8vc3RzLndpbmRvd3MubmV0LzBhZjc4NTZhLWQxZDMtNGJiNy1iZjcxLWMwMTRlYWY2NWViMS8iLCJvaWQiOiJlZGYxZjVjNy1iOGZkLTRhMDQtODM3MC01MGJiZjI5MWVmYzEiLCJyaCI6IjAuQVVnQWFvWDNDdFBSdDB1X2NjQVU2dlplc2VXVV9HYVFrM2REcEhTcXdTRHBUalpJQUFBLiIsInJvbGVzIjpbIkFwcHlQYXkuQXBpIl0sInN1YiI6ImVkZjFmNWM3LWI4ZmQtNGEwNC04MzcwLTUwYmJmMjkxZWZjMSIsInRpZCI6IjBhZjc4NTZhLWQxZDMtNGJiNy1iZjcxLWMwMTRlYWY2NWViMSIsInV0aSI6IlF1YXAydlJvU1VPV2dUWXNKendWQUEiLCJ2ZXIiOiIxLjAifQ.N-aUzfaeqaWR4LZqdZPyLlwZceDq7KuuIWcyyuCi0RmVtZBVpv_pPH5yaW85q_r38ti0mSxhsqRmQVTPQsPz72vRTZ0GcwlCY4t0lEGtIhH7CVVQQTTFIp3iDolYYh0CVl9FxIS9gELw7pdtqVhxWJ4okKb-CKVyTmb4INFhtgFAGtx3OrUuIGyS3RQf3Tl6yU7a9jZKSAyL1c2R_ZISTt3f-UGa6RSoze7RG30tRF2uZBqbMpOiQtiq6mXTP2Gun7nvTup2AZQodRp4st9n5XX5cjDO4lJIjLUjeSNSZgG_KTKfUIw-xxjSH92gRLOrlJfibZ9oG-ec9gBpoiVuUA"

9

}

```

---

## CancelMandateRequest.

**Arquivo de origem:** `APIS/AppyPay-Web-API/CancelMandateRequest..html`

### CancelMandateRequest

Export

Example

```
1

{

2

  "reason": "string",

3

  "description": "string"

4

}

```

reason

string

The reason why the mandate is being canceled. This is a required field.

description

string

A free text description of the reason for canceling the mandate. This is an optional field that can be used to provide more context about the cancellation.

---

## CancelMandateResponse

**Arquivo de origem:** `APIS/AppyPay-Web-API/CancelMandateResponse.html`

### CancelMandateResponse

Export

Example

```
1

{

2

  "mandateId": 0,

3

  "status": "string",

4

  "cancellationDate": "2019-08-24T14:15:22Z"

5

}

```

mandateId

integer

The ID of the mandate that was canceled.

status

string

The status of the canceled mandate. This will be 'CANCELED'.

cancellationDate

string<date-time>

The date and time the mandate was canceled in the system.

---

## Create a merchant GPO PST configurations

**Arquivo de origem:** `APIS/AppyPay-Web-API/Create a merchant GPO PST configurations.html`

### Create a merchant GPO PST configurations

post

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations

This service allows to create a GPO PST configurations. Only merchant aggregators (`isAggregator = true`) can have GPO PST configurations.

#### Request

Security: Bearer Auth

##### Path Parameters

merchantId

string

required

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

Content-Type

string

Indicates the media type of the resource

Default:application/json

Example:application/json

#### Responses

201

A single `GPO PST configuration` object. If provided a non-existent `merchantId`, this call returns an error.

##### Body

application/json

application/json

responses

/

201

id

integer

required

clientID

string

required

refreshTokenGrantType

string

required

accessTokenGrantType

string

required

accessTokenExpiresIn

string<date-time>

refreshTokenExpiresIn

string<date-time>

email

string<email>

required

clientSecretKeyVaultId

string

required

passwordKeyVaultId

string

required

redirectURI

string or null

numOfMerchants

integer

enabled

boolean

createdBy

string

required

updatedBy

string

required

createdDate

string<date-time>

required

updatedDate

string<date-time>

required

Auth

Token:

Parameters

merchantId*:

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Content-Type:

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json'

```

Response Example

```
1

{

2

  "id": 1,

3

  "clientID": "gpo-api",

4

  "refreshTokenGrantType": "password",

5

  "accessTokenGrantType": "refresh",

6

  "accessTokenExpiresIn": "2024-01-12T16:53:17.7178719",

7

  "refreshTokenExpiresIn": "2024-01-12T21:23:16.9766280",

8

  "email ": "appypay.dev@appy.co.ao",

9

  "clientSecretKeyVaultId": "AppyClientSecret",

10

  "passwordKeyVaultId": "AppyPassword",

11

  "redirectURI": null,

12

  "numOfMerchants": 10,

13

  "enabled": true,

14

  "createdBy": "Glória Gonçalves",

15

  "updatedBy": "Glória Gonçalves",

16

  "createdDate": "2023-11-29T14:43:32.5266667",

17

  "updatedDate": "2023-11-29T14:43:32.5266667"

18

}

```

---

## Create a refperiod

**Arquivo de origem:** `APIS/AppyPay-Web-API/Create a refperiod.html`

post

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/refperiods/{refperiodId}

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/refperiods/{refperiodId} \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json'

```

---

## Get a merchant all GPO PST Configurations

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get a merchant all GPO PST Configurations.html`

### Get a merchant all GPO PST Configurations

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations

This service allows to get a merchant all GPO PST configurations.Only merchant aggregators (`isAggregator = true`) can have GPO PST configurations.

#### Request

Security: Bearer Auth

##### Path Parameters

merchantId

string

required

##### Query Parameters

$filter

string

The query option that allows to filter a collection of resources based on expressions. Check operators here: https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/kdexoswoenpwt-web-api-operators

Example:$filter=field_name eq '12345'

$orderby

string

The query option that allows to request resources in a particular order

Allowed values:ascdesc

Default:asc

Example:$orderby=field_name desc

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

$skip

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Number of records to skip before start collecting the results

>= 0<= 500

Default:0

$top

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Limit of returned records

>= 0<= 500

Default:50

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

#### Responses

200

A object with data array of up to `$top` merchants GPO PST Configurations, starting after `$skip`. Each entry in the array is a separate `merchant GPO PST Configurations` object. If no more merchants GPO PST configurations are available, the result will be an empty array.

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

required

clientID

string

required

refreshTokenGrantType

string

required

accessTokenGrantType

string

required

accessTokenExpiresIn

string

refreshTokenExpiresIn

string

email

string

required

clientSecretKeyVaultId

string

required

passwordKeyVaultId

string

required

redirectURI

null

numOfMerchants

integer

enabled

boolean

createdBy

string

required

updatedBy

string

required

createdDate

string

required

updatedDate

string

required

totalCount

integer

hasMore

boolean

Auth

Token:

Parameters

merchantId*:

$filter:

$orderby:Not Setascdesc

select an option (defaults to: asc)

$select:

$skip:

$top:

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 1,

5

      "clientID": "gpo-api",

6

      "refreshTokenGrantType": "password",

7

      "accessTokenGrantType": "refresh",

8

      "accessTokenExpiresIn": "2024-01-12T16:53:17.7178719",

9

      "refreshTokenExpiresIn": "2024-01-12T21:23:16.9766280",

10

      "email ": "appypay.dev@appy.co.ao",

11

      "clientSecretKeyVaultId": "AppyClientSecret",

12

      "passwordKeyVaultId": "AppyPassword",

13

      "redirectURI": null,

14

      "numOfMerchants": 10,

15

      "enabled": true,

16

      "createdBy": "Glória Gonçalves",

17

      "updatedBy": "Glória Gonçalves",

18

      "createdDate": "2023-11-29T14:43:32.5266667",

19

      "updatedDate": "2023-11-29T14:43:32.5266667"

20

    }

21

  ],

22

  "totalCount": 1,

23

  "hasMore": false

24

}

```

---

## Get a payout

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get a payout.html`

### Get a payout

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/payouts/{transferId}

This service allows to get a specific payou and all the related data: `transactions`

#### Request

Security: Bearer Auth

##### Path Parameters

transferId

integer

required

Transfer identifier

##### Query Parameters

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

id

integer

rId

string<uuid>

merchantTransactionId

string

transactionTypeId

integer

transactionType

string

Allowed value:Funds Transfers

amount

number<double>

feeAmount

number<double>

numberOfTransactions

integer

currency

string

Allowed value:AOA

Default:AOA

statusId

integer

Allowed values:01234

status

string

Allowed values:RequestedPendingSuccessFailedEspired

description

string

applicationId

integer

applicationName

string

paymentMethodId

integer

paymentMethod

string

paymentMethodImgName

string or null

paymentMethodImgUrl

string or null

merchantId

integer

merchantAdAppId

string<uuid>

merchantName

string

createdDate

string<date-time>

updateDate

string<date-time>

transactions

array[object]

id

integer

rId

string<uuid>

merchantTransactionId

string

transactionTypeId

integer

transactionType

string

Allowed value:Charge

amount

number<double>

amountRefunded

number<double>

currency

string

Allowed value:AOA

Default:AOA

statusId

integer

status

string

description

string

operationId

integer

operation

string

refunded

boolean

applicationFeeAmount

integer

disputes

boolean

Default:false

applicationId

integer

applicationName

string

paymentMethodId

integer

paymentMethod

string

paymentMethodImgName

string or null

paymentMethodImgUrl

string or null

merchantId

integer

merchantAdAppId

string<uuid>

merchantName

string

createdDate

string<date-time>

updateDate

string<date-time>

Auth

Token:

Parameters

transferId*:

$select:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/payouts/{transferId} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "id": 1,

3

  "rId": "4DBAA1F4-C318-404A-AF01-000BE4D65E7D",

4

  "merchantTransactionId": "TA202211291457",

5

  "transactionTypeId": 1,

6

  "transactionType": "Funds Transfers",

7

  "amount": 5000,

8

  "feeAmount": 50,

9

  "numberOfTransactions": 5,

10

  "currency": "AOA",

11

  "statusId": 2,

12

  "status": "Success",

13

  "description": "Test DA",

14

  "applicationId": 1,

15

  "applicationName": "UMM App DEV",

16

  "paymentMethodId": 3,

17

  "paymentMethod": "UMM",

18

  "paymentMethodImgName": null,

19

  "paymentMethodImgUrl": null,

20

  "merchantId": 2,

21

  "merchantAdAppId": "B1DF7F4B-ACF7-45EC-B482-05769EA4CCC3",

22

  "merchantName": "MERCHANT ANGOLA LDA",

23

  "createdDate": "2022-11-29T13:57:35.1781046",

24

  "updateDate": "2022-11-29T13:59:16.9303490",

25

  "transactions": [

26

    {

27

      "id": 102,

28

      "rId": "4DBAA1F4-C318-404A-AF01-000BE4D65E7D",

29

      "merchantTransactionId": "TA202211291457",

30

      "transactionTypeId": 1,

31

      "transactionType": "Charge",

32

      "amount": 50,

33

      "amountRefunded": 0,

34

      "currency": "AOA",

35

      "statusId": 3,

36

      "status": "Success",

37

      "description": "Test DA",

38

      "operationId": 1,

39

      "operation": "One-time payment",

40

      "refunded": false,

41

      "applicationFeeAmount": 0,

42

      "disputes": false,

43

      "applicationId": 1,

44

      "applicationName": "GPOApp DEV",

45

      "paymentMethodId": 1,

46

      "paymentMethod": "GPO",

47

      "paymentMethodImgName": null,

48

      "paymentMethodImgUrl": null,

49

      "merchantId": 2,

50

      "merchantAdAppId": "B1DF7F4B-ACF7-45EC-B482-05769EA4CCC3",

51

      "merchantName": "MERCHANT ANGOLA LDA",

52

      "createdDate": "2022-11-29T13:57:35.1781046",

53

      "updateDate": "2022-11-29T13:59:16.9303490"

54

    }

55

  ]

56

}

```

---

## Get all bank participants

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get all bank participants.html`

### Get all bank participants

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/bank-participants

This service allows to get a list of all bank participants.





The list, by default, returns the data ordered (first created).



#### Request

Security: Bearer Auth

##### Query Parameters

$filter

string

The query option that allows to filter a collection of resources based on expressions. Check operators here: https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/kdexoswoenpwt-web-api-operators

Example:$filter=field_name eq '12345'

$orderby

string

The query option that allows to request resources in a particular order

Allowed values:ascdesc

Default:asc

Example:$orderby=field_name desc

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

$skip

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Number of records to skip before start collecting the results

>= 0<= 500

Default:0

$top

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Limit of returned records

>= 0<= 500

Default:50

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

#### Responses

200

A object with data array of up to `$top` bank participants, starting after `$skip`. Each entry in the array is a separate `bank participant` object. If no more bank participants are available, the result will be an empty array.

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

logoUrl

string

interbankCode

string

bicCode

string

bankName

string

abbreviation

string

isSupportBank

boolean

createdBy

string

updatedBy

string

createdDate

string<date-time>

updatedDate

string<date-time>

totalCount

integer

hasMore

boolean

Auth

Token:

Parameters

$filter:

$orderby:Not Setascdesc

select an option (defaults to: asc)

$select:

$skip:

$top:

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/bank-participants \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 1,

5

      "logoUrl": "0001.jpg",

6

      "interbankCode": "0001",

7

      "bicCode": "BNANAOLU",

8

      "bankName": "Banco Nacional de Angola",

9

      "abbreviation": "BNA",

10

      "isSupportBank": false,

11

      "createdBy": "user",

12

      "updatedBy": "user",

13

      "createdDate": "2023-10-25T10:51:25.2100000",

14

      "updatedDate": "2023-10-25T10:51:25.2100000"

15

    }

16

  ],

17

  "totalCount": 1,

18

  "hasMore": true

19

}

```

---

## Get all business-categories

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get all business-categories.html`

### Get all business-categories

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/business-categories

This service allows to get a list of business-categories.





The list, by default, returns the data ordered (first created).



#### Request

##### Query Parameters

$filter

string

The query option that allows to filter a collection of resources based on expressions. Check operators here: https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/kdexoswoenpwt-web-api-operators

Example:$filter=field_name eq '12345'

$orderby

string

The query option that allows to request resources in a particular order

Allowed values:ascdesc

Default:asc

Example:$orderby=field_name desc

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

$skip

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Number of records to skip before start collecting the results

>= 0<= 500

Default:0

$top

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Limit of returned records

>= 0<= 500

Default:50

##### Headers

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

Content-Type

string

Indicates the media type of the resource

Default:application/json

Example:application/json

#### Responses

200

A object with data array of up to `$top` business-categories, starting after `$skip`. Each entry in the array is a separate `business-category` object. If no more business-categories are available, the result will be an empty array.

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

name

string

description

string

isActive

boolean

createdBy

string

updatedBy

string

createdDate

string<date-time>

updatedDate

string<date-time>

totalCount

integer

hasMore

boolean

Parameters

$filter:

$orderby:Not Setascdesc

select an option (defaults to: asc)

$select:

$skip:

$top:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Content-Type:

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/business-categories \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Content-Type: '

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 1,

5

      "name": "Food & drink",

6

      "description": "Restaurants, cafes, bars, food delivery and beverage services",

7

      "isActive": true,

8

      "createdBy": "Osvaldo Marreiros",

9

      "updatedBy": "Osvaldo Marreiros",

10

      "createdDate": "2025-09-14T07:44:29.2266667",

11

      "updatedDate": "2025-09-14T07:44:29.2266667"

12

    },

13

    {

14

      "id": 2,

15

      "name": "Health, beauty and fitness",

16

      "description": "Healthcare services, beauty salons, gyms, wellness centers",

17

      "isActive": true,

18

      "createdBy": "Osvaldo Marreiros",

19

      "updatedBy": "Osvaldo Marreiros",

20

      "createdDate": "2025-09-14T07:44:29.2266667",

21

      "updatedDate": "2025-09-14T07:44:29.2266667"

22

    },

23

    {

24

      "id": 3,

25

      "name": "Home and repair",

26

      "description": "Construction, plumbing, electrical, maintenance and home improvement services",

27

      "isActive": true,

28

      "createdBy": "Osvaldo Marreiros",

29

      "updatedBy": "Osvaldo Marreiros",

30

      "createdDate": "2025-09-14T07:44:29.2266667",

31

      "updatedDate": "2025-09-14T07:44:29.2266667"

32

    },

33

    {

34

      "id": 4,

35

      "name": "Leisure and entertainment",

36

      "description": "Entertainment venues, sports, recreation and leisure activities",

37

      "isActive": true,

38

      "createdBy": "Osvaldo Marreiros",

39

      "updatedBy": "Osvaldo Marreiros",

40

      "createdDate": "2025-09-14T07:44:29.2266667",

41

      "updatedDate": "2025-09-14T07:44:29.2266667"

42

    },

43

    {

44

      "id": 5,

45

      "name": "Non-profit organizations",

46

      "description": "Charitable organizations, foundations and community service groups",

47

      "isActive": true,

48

      "createdBy": "Osvaldo Marreiros",

49

      "updatedBy": "Osvaldo Marreiros",

50

      "createdDate": "2025-09-14T07:44:29.2266667",

51

      "updatedDate": "2025-09-14T07:44:29.2266667"

52

    },

53

    {

54

      "id": 6,

55

      "name": "Retail",

56

      "description": "Stores, shops, e-commerce and retail merchandise businesses",

57

      "isActive": true,

58

      "createdBy": "Osvaldo Marreiros",

59

      "updatedBy": "Osvaldo Marreiros",

60

      "createdDate": "2025-09-14T07:44:29.2266667",

61

      "updatedDate": "2025-09-14T07:44:29.2266667"

62

    },

63

    {

64

      "id": 7,

65

      "name": "Services",

66

      "description": "Professional services, consulting, legal, accounting and business services",

67

      "isActive": true,

68

      "createdBy": "Osvaldo Marreiros",

69

      "updatedBy": "Osvaldo Marreiros",

70

      "createdDate": "2025-09-14T07:44:29.2266667",

71

      "updatedDate": "2025-09-14T07:44:29.2266667"

72

    },

73

    {

74

      "id": 8,

75

      "name": "Transportation",

76

      "description": "Logistics, delivery, taxi, rideshare and transportation services",

77

      "isActive": true,

78

      "createdBy": "Osvaldo Marreiros",

79

      "updatedBy": "Osvaldo Marreiros",

80

      "createdDate": "2025-09-14T07:44:29.2266667",

81

      "updatedDate": "2025-09-14T07:44:29.2266667"

82

    },

83

    {

84

      "id": 9,

85

      "name": "Travel and Accommodation",

86

      "description": "Hotels, travel agencies, vacation rentals and hospitality services",

87

      "isActive": true,

88

      "createdBy": "Osvaldo Marreiros",

89

      "updatedBy": "Osvaldo Marreiros",

90

      "createdDate": "2025-09-14T07:44:29.2266667",

91

      "updatedDate": "2025-09-14T07:44:29.2266667"

92

    },

93

    {

94

      "id": 10,

95

      "name": "Other",

96

      "description": "Business categories not covered by other classifications",

97

      "isActive": true,

98

      "createdBy": "Osvaldo Marreiros",

99

      "updatedBy": "Osvaldo Marreiros",

100

      "createdDate": "2025-09-14T07:44:29.2266667",

101

      "updatedDate": "2025-09-14T07:44:29.2266667"

102

    }

103

  ],

104

  "totalCount": 10,

105

  "hasMore": false

106

}

```

---

## Get all business-types

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get all business-types.html`

### Get all business-types

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/business-types

This service allows to get a list of business-types.





The list, by default, returns the data ordered (first created).



#### Request

##### Query Parameters

$filter

string

The query option that allows to filter a collection of resources based on expressions. Check operators here: https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/kdexoswoenpwt-web-api-operators

Example:$filter=field_name eq '12345'

$orderby

string

The query option that allows to request resources in a particular order

Allowed values:ascdesc

Default:asc

Example:$orderby=field_name desc

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

$skip

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Number of records to skip before start collecting the results

>= 0<= 500

Default:0

$top

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Limit of returned records

>= 0<= 500

Default:50

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

#### Responses

200

A object with data array of up to `$top` business-types, starting after `$skip`. Each entry in the array is a separate `business-type` object. If no more business-types are available, the result will be an empty array.

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

name

string

description

string

isActive

boolean

createdBy

string

updatedBy

string

createdDate

string<date-time>

updatedDate

string<date-time>

totalCount

integer

hasMore

boolean

Parameters

$filter:

$orderby:Not Setascdesc

select an option (defaults to: asc)

$select:

$skip:

$top:

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/business-types \

  --header 'Accept: application/json' \

  --header 'Accept-Language: '

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 0,

5

      "name": "string",

6

      "description": "string",

7

      "isActive": true,

8

      "createdBy": "string",

9

      "updatedBy": "string",

10

      "createdDate": "2019-08-24T14:15:22Z",

11

      "updatedDate": "2019-08-24T14:15:22Z"

12

    }

13

  ],

14

  "totalCount": 0,

15

  "hasMore": true

16

}

```

---

## Get all payouts

**Arquivo de origem:** `APIS/AppyPay-Web-API/Get all payouts.html`

### Get all payouts

get

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/payouts

This service allows to get a list of payouts.





The list, by default, returns the data ordered (first created).



#### Request

Security: Bearer Auth

##### Query Parameters

$filter

string

The query option that allows to filter a collection of resources based on expressions. Check operators here: https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/kdexoswoenpwt-web-api-operators

Example:$filter=field_name eq '12345'

$orderby

string

The query option that allows to request resources in a particular order

Allowed values:ascdesc

Default:asc

Example:$orderby=field_name desc

$select

string

The query option that allows to request a specific set of attributes that are returned

Example:$select=field_name1, field_name2

$skip

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Number of records to skip before start collecting the results

>= 0<= 500

Default:0

$top

integer

The query option that allows to define the number of items in the queried collection to be included in the result. Limit of returned records

>= 0<= 500

Default:50

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

A object with data array of up to `$top` payouts, starting after `$skip`. Each entry in the array is a separate `payout` object. If no more payouts are available, the result will be an empty array.

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

rId

string<uuid>

merchantTransactionId

string

transactionTypeId

integer

transactionType

string

Allowed value:Funds Transfers

amount

number<double>

feeAmount

number<double>

numberOfTransactions

integer

currency

string

Allowed value:AOA

Default:AOA

statusId

integer

Allowed values:01234

status

string

Allowed values:RequestedPendingSuccessFailedEspired

description

string

applicationId

integer

applicationName

string

paymentMethodId

integer

paymentMethod

string

paymentMethodImgName

string or null

paymentMethodImgUrl

string or null

merchantId

integer

merchantAdAppId

string<uuid>

merchantName

string

createdDate

string<date-time>

updateDate

string<date-time>

totalCount

integer

hasMore

boolean

Auth

Token:

Parameters

$filter:

$orderby:Not Setascdesc

select an option (defaults to: asc)

$select:

$skip:

$top:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/payouts \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 1,

5

      "rId": "4DBAA1F4-C318-404A-AF01-000BE4D65E7D",

6

      "merchantTransactionId": "TA202211291457",

7

      "transactionTypeId": 1,

8

      "transactionType": "Funds Transfers",

9

      "amount": 5000,

10

      "feeAmount": 50,

11

      "numberOfTransactions": 5,

12

      "currency": "AOA",

13

      "statusId": 2,

14

      "status": "Success",

15

      "description": "Test DA",

16

      "applicationId": 1,

17

      "applicationName": "UMM App DEV",

18

      "paymentMethodId": 3,

19

      "paymentMethod": "UMM",

20

      "paymentMethodImgName": null,

21

      "paymentMethodImgUrl": null,

22

      "merchantId": 2,

23

      "merchantAdAppId": "B1DF7F4B-ACF7-45EC-B482-05769EA4CCC3",

24

      "merchantName": "MERCHANT ANGOLA LDA",

25

      "createdDate": "2022-11-29T13:57:35.1781046",

26

      "updateDate": "2022-11-29T13:59:16.9303490"

27

    }

28

  ],

29

  "totalCount": 1,

30

  "hasMore": true

31

}

```

---

## Post an application bank account

**Arquivo de origem:** `APIS/AppyPay-Web-API/Post an application bank account.html`

### Post an application bank account

post

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/applications/{applicationId}/bank-accounts

This service allows to associate a merchant bank account to an application or create a new one.

#### Request

Security: Bearer Auth

##### Path Parameters

applicationId

integer

required

The application identifier

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

201

A single `bank account` object if the call is successful. This call returns an error if something goes wrong.

##### Body

application/json

application/json

responses

/

201

bankAccountId

integer

currency

string

Example:AOA

bankCountry

string

iban

string

createdBy

string

updatedBy

string

createdDate

string<date-time>

updatedDate

string<date-time>

Auth

Token:

Parameters

applicationId*:

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/applications/{applicationId}/bank-accounts \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json'

```

Response Example

```
1

{

2

  "bankAccountId": 1,

3

  "currency": "AOA",

4

  "bankCountry": "Angola",

5

  "iban": "AO1400080001001234567890",

6

  "createdBy": "GG",

7

  "updatedBy": "GG",

8

  "createdDate": "2023-06-09T14:58:48.6233333",

9

  "updatedDate": "2023-06-09T14:58:48.6233333"

10

}

```

---

## Subscribe or unsubscribe to push notifications

**Arquivo de origem:** `APIS/AppyPay-Web-API/Subscribe or unsubscribe to push notifications.html`

### Subscribe/unsubscribe to push notifications

patch

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/users/me/push-subscriptions

This service allows to subscribe or unsubscribe push notification information of the user who is currently authenticated.

#### Request

Security: Bearer Auth

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

Content-Type

string

Indicates the media type of the resource

Default:application/json

Example:application/json

#### Responses

200

A single `user subscription` object. This call returns an error if something goes wrong.

##### Body

application/json

application/json

responses

/

200

userId

string<uuid>

required

subscriptionId

string<uuid>

required

onesignalId

string<uuid>

required

device

string

required

appId

string<uuid>

required

isSubscribed

boolean

required

Auth

Token:

Parameters

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Content-Type:

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request PATCH \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/users/me/push-subscriptions \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json'

```

Response Example

```
1

{

2

  "userId": "2c4a230c-5085-4924-a3e1-25fb4fc5965b",

3

  "subscriptionId": "d079718b-ff63-45dd-947b-4950c023750f",

4

  "onesignalId": "8cf23c22-2b8e-4bc6-ae29-fc827e3d56b1",

5

  "device": "Win32 120",

6

  "appId": "28c365d5-df94-4a54-8217-3ce51d068868",

7

  "isSubscribed": true

8

}

```

---

## Update a merchant GPO PST configurations

**Arquivo de origem:** `APIS/AppyPay-Web-API/Update a merchant GPO PST configurations.html`

### Update a merchant GPO PST configurations

patch

https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations/{gpoPstConfigurationId}

This service allows to partial update a GPO PST configurations. Only merchant aggregators (`isAggregator = true`) can have GPO PST configurations.





The fields omitted in the request will not be affected. The fields included and leave empty will have their current values removed.



#### Request

Security: Bearer Auth

##### Path Parameters

gpoPstConfigurationId

string

required

merchantId

string

required

##### Headers

Accept

string

Informs the server about the types of data that can be sent back

Default:application/json

Example:application/json

Accept-Language

string

Informs the server about the human language the server is expected to send back

Allowed values:enpt-BR

Default:pt-BR

Content-Type

string

Indicates the media type of the resource

Default:application/json

Example:application/json

#### Responses

200

A single `GPO PST configuration` object. If provided a non-existent `merchantId`, this call returns an error.

##### Body

application/json

application/json

responses

/

200

id

integer

required

clientID

string

required

refreshTokenGrantType

string

required

accessTokenGrantType

string

required

accessTokenExpiresIn

string<date-time>

refreshTokenExpiresIn

string<date-time>

email

string<email>

required

clientSecretKeyVaultId

string

required

passwordKeyVaultId

string

required

redirectURI

string or null

numOfMerchants

integer

enabled

boolean

createdBy

string

required

updatedBy

string

required

createdDate

string<date-time>

required

updatedDate

string<date-time>

required

Auth

Token:

Parameters

gpoPstConfigurationId*:

merchantId*:

Accept:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Content-Type:

Send API Request

DEV

Request Sample: Shell / cURL

```
curl --request PATCH \

  --url https://app-appypay-webapi-dev-001.azurewebsites.net/api/{version}/merchants/{merchantId}/gpo-pst-configurations/{gpoPstConfigurationId} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json'

```

Response Example

```
1

{

2

  "id": 1,

3

  "clientID": "gpo-api",

4

  "refreshTokenGrantType": "password",

5

  "accessTokenGrantType": "refresh",

6

  "accessTokenExpiresIn": "2024-01-12T16:53:17.7178719",

7

  "refreshTokenExpiresIn": "2024-01-12T21:23:16.9766280",

8

  "email ": "appypay.dev@appy.co.ao",

9

  "clientSecretKeyVaultId": "AppyClientSecret",

10

  "passwordKeyVaultId": "AppyPassword",

11

  "redirectURI": null,

12

  "numOfMerchants": 10,

13

  "enabled": true,

14

  "createdBy": "Glória Gonçalves",

15

  "updatedBy": "Glória Gonçalves",

16

  "createdDate": "2023-11-29T14:43:32.5266667",

17

  "updatedDate": "2023-11-29T14:43:32.5266667"

18

}

```

---

## Cancel Mandate

**Arquivo de origem:** `APIS/AppyPay-API/Cancel Mandate.html`

### Cancel Mandate

post

https://gwy-api-tst.appypay.co.ao/{version}/mandates/{mandateId}/cancel

Cancels an existing mandate.



##### Reason Codes



The request parameter `reason` should contain the reason code in uppercase, using the following values:


 | Code | Reason Description
 | BEDB | Blocked account request by BED (Debitor Bank)
 | CTAM | Contract update or modification
 | CTCA | By debtor contract cancellation
 | CTEX | By expired contract
 | CUST | Debtor request cancellation
 | DS24 | System action – Timeout, for the request acceptance of ADC has expired
 | DS99 | System action – Timeout, Inactivity of ADC expired
 | DUPL | By Settlement in Duplicate
 | MCFC | Last Contract instruction Ever Charged
 | MCOC | Instruction has already been charged (A IDD Única Já Foi Cobrada)
 | MSUC | Exceeded maximum number of instructions charged (Número de Cobranças Devolvidas Superior ao Definido)

#### Request

##### Path Parameters

mandateId

integer

required

The unique identifier of the mandate in the system. This is used to identify the mandate in the context of the direct debit system.

##### Body

application/json

application/json

reason

string

The reason why the mandate is being canceled. This is a required field.

description

string

A free text description of the reason for canceling the mandate. This is an optional field that can be used to provide more context about the cancellation.

#### Responses

200

Mandate canceled successfully.

##### Body

application/json

application/json

responses

/

200

mandateId

integer

The ID of the mandate that was canceled.

status

string

The status of the canceled mandate. This will be 'CANCELED'.

cancellationDate

string<date-time>

The date and time the mandate was canceled in the system.

Parameters

mandateId*:

Body

{ "reason": "string", "description": "string" }

```
1

{

2

  "reason": "string",

3

  "description": "string"

4

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/mandates/{mandateId}/cancel \

  --header 'Accept: application/json' \

  --header 'Content-Type: application/json' \

  --data '{

  "reason": "string",

  "description": "string"

}'

```

Response Example

```
1

{

2

  "mandateId": 0,

3

  "status": "string",

4

  "cancellationDate": "2019-08-24T14:15:22Z"

5

}

```

---

## CancelMandateRequest

**Arquivo de origem:** `APIS/AppyPay-API/CancelMandateRequest.html`

### CancelMandateRequest

Export

Example

reason

string

The reason why the mandate is being canceled. This is a required field.

description

string

A free text description of the reason for canceling the mandate. This is an optional field that can be used to provide more context about the cancellation.

---

## CancelMandateResponse

**Arquivo de origem:** `APIS/AppyPay-API/CancelMandateResponse.html`

### CancelMandateResponse

Export

Example

mandateId

integer

The ID of the mandate that was canceled.

status

string

The status of the canceled mandate. This will be 'CANCELED'.

cancellationDate

string<date-time>

The date and time the mandate was canceled in the system.

---

## Get Taxpayer by NIF

**Arquivo de origem:** `APIS/AppyPay-API/Get Taxpayer by NIF.html`

### Get Taxpayer by NIF

get

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/taxpayer/{nif}

Retrieves taxpayer information for a given NIF (Número de Identificação Fiscal).





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Path Parameters

nif

string

required

Taxpayer Identification Number (NIF)

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

Taxpayer information retrieved successfully

##### Body

application/json

application/json

responses

/

200

nif

string

required

Taxpayer Identification Number (NIF)

name

string

Taxpayer name

vatRegime

string

VAT regime

type

string

Allowed values:SINGULARCOLLECTIVE

status

string

required

Taxpayer status code:


- `A` - Ativo

- `C` - Cessado

- `D` - Falecido

- `E` - Herança

- `F` - Anulado

- `G` - Suspenso


Allowed values:ACDEFG

Auth

Token:

Parameters

nif*:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/taxpayer/{nif} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "nif": "5000000000",

3

  "name": "Empresa Exemplo, Lda.",

4

  "status": "A"

5

}

```

---

## Get a Mandate

**Arquivo de origem:** `APIS/AppyPay-API/Get a Mandate.html`

### Get a Mandate

get

https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates/{mandateId}

This service allows merchant support team to get a specific mandate.

#### Request

Security: Bearer Auth

##### Path Parameters

mandateId

integer

required

Mandate unique identifier

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

id

integer

merchantId

integer

creditorAccId

integer

currencyId

string

debitorBankParticipantId

integer

purposeCode

string

purposeCategoryCode

string

mandateType

string

frequencyType

string

mandateStatusId

integer

merchantReferenceNumber

string

debitStartDate

string<date>

debitEndDate

string<date>

debitDay

integer

serviceDescription

string

maxAmount

number<double>

debitorName

string

debitorNIF

string

debitorIBAN

string

debitorTelephone

string

debitorEmail

string

debitorSignaturePlace

string

debitorSignatureDate

string<date-time>

debitorSignature

string

isAccepted

boolean

isCanceled

boolean

isMerchantRegistered

boolean

message

string

providerMandateId

string

originator

string

createdDate

string<date-time>

updatedDate

string<date-time>

MandateHistory

array[object]

id

integer

mandateId

integer

mandateStatusId

integer

FileContentId

integer

FilePath

string

createdDate

string<date-time>

updatedDate

string<date-time>

providerResponseDescription

string

providerResponseCodeId

integer

providerCancellationReasonCode

string

providerInitiatedById

integer

Auth

Token:

Parameters

mandateId*:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates/{mandateId} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "id": 0,

3

  "merchantId": 0,

4

  "creditorAccId": 0,

5

  "currencyId": "string",

6

  "debitorBankParticipantId": 0,

7

  "purposeCode": "string",

8

  "purposeCategoryCode": "string",

9

  "mandateType": "string",

10

  "frequencyType": "string",

11

  "mandateStatusId": 0,

12

  "merchantReferenceNumber": "string",

13

  "debitStartDate": "2019-08-24",

14

  "debitEndDate": "2019-08-24",

15

  "debitDay": 0,

16

  "serviceDescription": "string",

17

  "maxAmount": -1.7976931348623157e+308,

18

  "debitorName": "string",

19

  "debitorNIF": "string",

20

  "debitorIBAN": "string",

21

  "debitorTelephone": "string",

22

  "debitorEmail": "string",

23

  "debitorSignaturePlace": "string",

24

  "debitorSignatureDate": "2019-08-24T14:15:22Z",

25

  "debitorSignature": "string",

26

  "isAccepted": true,

27

  "isCanceled": true,

28

  "isMerchantRegistered": true,

29

  "message": "string",

30

  "providerMandateId": "string",

31

  "originator": "string",

32

  "createdDate": "2019-08-24T14:15:22Z",

33

  "updatedDate": "2019-08-24T14:15:22Z",

34

  "MandateHistory": [

35

    {

36

      "id": 0,

37

      "mandateId": 0,

38

      "mandateStatusId": 0,

39

      "FileContentId": 0,

40

      "FilePath": "string",

41

      "createdDate": "2019-08-24T14:15:22Z",

42

      "updatedDate": "2019-08-24T14:15:22Z",

43

      "providerResponseDescription": "string",

44

      "providerResponseCodeId": 0,

45

      "providerCancellationReasonCode": "string",

46

      "providerInitiatedById": 0

47

    }

48

  ]

49

}

```

---

## Get a charge

**Arquivo de origem:** `APIS/AppyPay-API/Get a charge.html`

### Get a charge

get

https://gwy-api-tst.appypay.co.ao/{version}/charges/{id}

This service allows merchant support team to get a specific charge.





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or path parameter culture.



#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

Gateway transaction ID. This will be used to identify the transaction

##### Query Parameters

merchantTransactionId

string

Merchant transaction ID. This will be used to identify the transaction

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

payment

object

required

id

string<uuid>

required

Gateway transaction ID. This will be used to identify the transaction

merchantTransactionId

string

required

A unique identifier of the transaction

>= 1 characters<= 15 characters

type

string

required

operation

string

required

amount

number<double>

required

currency

string

required

status

any

required

Transaction status.

Allowed values:RequestedPendingSuccessFailed

description

string

required

Short description or notes

disputes

boolean

required

applicationFeeAmount

number<double>

required

paymentMethod

string

createdDate

string<date-time>

required

updatedDate

string<date-time>

required

transactionEvents

array[object]

required

options

object

The optional parameters names vary according to merchant

reference

object

Only available for some payment methods

Auth

Token:

Parameters

id*:

merchantTransactionId:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/charges/{id} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

UMM - ExampleREF - Example

Response Example: UMM - Example

```
1

{

2

  "payment": {

3

    "id": "57af18f2-64b7-4464-a503-3baf741c9f0d",

4

    "merchantTransactionId": "131fd130701",

5

    "type": "Charge",

6

    "operation": "ONE_TIME_PAYMENT",

7

    "amount": 1.2,

8

    "currency": "AOA",

9

    "status": "Failed",

10

    "description": "POSTMAN_Test",

11

    "disputes": false,

12

    "applicationFeeAmount": 0,

13

    "paymentMethod": "UMM",

14

    "createdDate": "2021-07-13T11:47:13.5216855",

15

    "updatedDate": "2021-07-13T11:47:52.5991607",

16

    "transactionEvents": [

17

      {

18

        "id": 2648,

19

        "transactionId": "57af18f2-64b7-4464-a503-3baf741c9f0d",

20

        "type": "Charge",

21

        "providerTransactionId": "2BWKF0YIMZTDVGL2",

22

        "actionStatus": false,

23

        "createdDate": "2021-07-13T11:47:14.521179",

24

        "responseStatus": {

25

          "successful": false,

26

          "status": "Failed",

27

          "code": 231,

28

          "message": "Payment not authorized by the customer",

29

          "source": "UMM",

30

          "sourceDetails": {

31

            "attempt": 1,

32

            "type": "EPMS_PROCESSOR",

33

            "code": "ISSUER_907",

34

            "message": "Refused by the issuer."

35

          }

36

        }

37

      }

38

    ],

39

    "options": {},

40

    "reference": null

41

  }

42

}

```

---

## Get a creditor account for the specific application (beta)

**Arquivo de origem:** `APIS/AppyPay-API/Get a creditor account for the specific application (beta).html`

### Get a creditor account for the specific application (beta)

get

https://gwy-api-tst.appypay.co.ao/{version}/applications/{applicationId}/sdd-creditor-accounts/{creditorAccId}

This service allows to get a specific creditor account for an application.





The application must be linked to SDD payment method.



#### Request

Security: Bearer Auth

##### Path Parameters

applicationId

integer

required

The application identifier

creditorAccId

integer

required

The Creditor Account identifier

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

A single `SDD creditor account` object if the call is successful. This call returns an error if something goes wrong.

##### Body

application/json

application/json

responses

/

200

id

integer

currencyId

string

applicationId

integer

bankParticipantId

integer

iban

string

isActive

boolean

isDefault

boolean

description

string

createdBy

string

updatedBy

string

createdDate

string<date-time>

updatedDate

string<date-time>

Auth

Token:

Parameters

applicationId*:

creditorAccId*:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/applications/{applicationId}/sdd-creditor-accounts/{creditorAccId} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "id": 1,

3

  "currencyId": "AOA",

4

  "applicationId": 1,

5

  "bankParticipantId": 1,

6

  "iban": "AO1234567890123456789012",

7

  "isActive": true,

8

  "isDefault": true,

9

  "description": "Creditor Account 2",

10

  "createdBy": "Luis Rita",

11

  "updatedBy": "Luis Rita",

12

  "createdDate": "2023-05-23T11:35:06.6600000",

13

  "updatedDate": "2023-05-23T11:35:06.6600000"

14

}

```

---

## Get a fiscal document

**Arquivo de origem:** `APIS/AppyPay-API/Get a fiscal document.html`

### Get a fiscal document

get

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/{id}

This service allows merchant support team to get a fiscal document.

#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

Unique document identifier

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

required

Unique document identifier

documentNo

string

required

Unique document identification generated according to SAF-T(AO)

docData

object

Document file metadata

fileType

string

required

File type

Allowed value:application/pdf

file

string<byte>

required

File content

qrCode

object

QR code metadata

fileType

string

required

File type

Allowed value:image/png

file

string<byte>

required

File content

Auth

Token:

Parameters

id*:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/{id} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",

3

  "documentNo": "FT FT6325S2C/10006",

4

  "docData": {

5

    "fileType": "application/pdf",

6

    "file": "string"

7

  },

8

  "qrCode": {

9

    "fileType": "image/png",

10

    "file": "string"

11

  }

12

}

```

---

## Get a reference

**Arquivo de origem:** `APIS/AppyPay-API/Get a reference.html`

### Get a reference

get

https://gwy-api-tst.appypay.co.ao/{version}/references/{referenceNumber}

This service allows merchant support team to get a specific reference.

#### Request

Security: Bearer Auth

##### Path Parameters

referenceNumber

string

required

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

reference

object

id

integer

required

entity

string

required

referenceNumber

string

required

>= 9 characters<= 15 characters

currency

string

required

amount

number<double>

minAmount

number<double>

maxAmount

number<double>

startDate

string<date-time>

required

expirationDate

string<date-time>

required

isActive

boolean

required

createdBy

string

required

updatedBy

string

required

createdDate

string<date-time>

required

updatedDate

string<date-time>

required

Auth

Token:

Parameters

referenceNumber*:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/references/{referenceNumber} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "reference": {

3

    "id": 1,

4

    "entity": "00348",

5

    "referenceNumber": "123456789",

6

    "currency": "AOA",

7

    "amount": 10,

8

    "minAmount": 1,

9

    "maxAmount": 10000,

10

    "startDate": "2022-01-01T15:00:00",

11

    "expirationDate": "2025-01-01T15:00:00",

12

    "isActive": true,

13

    "createdBy": "API Service",

14

    "updatedBy": "API Service",

15

    "createdDate": "2022-01-01T15:00:00",

16

    "updatedDate": "2022-01-01T15:00:00"

17

  }

18

}

```

---

## Get all Mandates

**Arquivo de origem:** `APIS/AppyPay-API/Get all Mandates.html`

### Get all Mandates

get

https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates

This service gets a list of mandates.

#### Request

Security: Bearer Auth

##### Query Parameters

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

MerchantReferenceNumber

string

Filter by Reference number used by the merchant to identify the customer subscription/contract within their system

<= 100 characters

Example:AI8282734

mandateStatusId

integer

Filter by mandate status

Allowed values:0 - Requested1 - Pending2 - Active3 - Failed4 - Cancelled5 - Expired

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

data

array[object]

id

integer

merchantId

integer

creditorAccId

integer

currencyId

string

debitorBankParticipantId

integer

purposeCode

string

purposeCategoryCode

string

mandateType

string

frequencyType

string

mandateStatusId

integer

merchantReferenceNumber

string

debitStartDate

string

debitEndDate

string

debitDay

integer

serviceDescription

string

maxAmount

integer

debitorName

string

debitorNIF

string

debitorIBAN

string

debitorTelephone

string

debitorEmail

string

debitorSignaturePlace

string

debitorSignatureDate

string

debitorSignature

string

isAccepted

boolean

isCanceled

boolean

isMerchantRegistered

boolean

message

string

providerMandateId

string

originator

string

createdDate

string

updatedDate

string

createdBy

string

totalCount

integer

hasMore

boolean

Auth

Token:

Parameters

MerchantReferenceNumber:

dateFrom:

dateTo:

limit:

mandateStatusId:Not Set0 - Requested1 - Pending2 - Active3 - Failed4 - Cancelled5 - Expired

select an option

skip:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "data": [

3

    {

4

      "id": 0,

5

      "merchantId": 0,

6

      "creditorAccId": 0,

7

      "currencyId": "string",

8

      "debitorBankParticipantId": 0,

9

      "purposeCode": "string",

10

      "purposeCategoryCode": "string",

11

      "mandateType": "string",

12

      "frequencyType": "string",

13

      "mandateStatusId": 0,

14

      "merchantReferenceNumber": "string",

15

      "debitStartDate": "string",

16

      "debitEndDate": "string",

17

      "debitDay": 0,

18

      "serviceDescription": "string",

19

      "maxAmount": 0,

20

      "debitorName": "string",

21

      "debitorNIF": "string",

22

      "debitorIBAN": "string",

23

      "debitorTelephone": "string",

24

      "debitorEmail": "string",

25

      "debitorSignaturePlace": "string",

26

      "debitorSignatureDate": "string",

27

      "debitorSignature": "string",

28

      "isAccepted": true,

29

      "isCanceled": true,

30

      "isMerchantRegistered": true,

31

      "message": "string",

32

      "providerMandateId": "string",

33

      "originator": "string",

34

      "createdDate": "string",

35

      "updatedDate": "string",

36

      "createdBy": "string"

37

    }

38

  ],

39

  "totalCount": 0,

40

  "hasMore": true

41

}

```

---

## Get all analytics or charges

**Arquivo de origem:** `APIS/AppyPay-API/Get all analytics or charges.html`

### Get all analytics/charges

get

https://gwy-api-tst.appypay.co.ao/{version}/analytics/charges

This service allows merchant support team to get a list of charges. if you are a merchantAggregator, list all transactions of aggregates merchants. Also, allows merchant support team to search for specific charges based on filters. This functionality is useful to check a pending payment status or check charges that meet some criteria.



Example-Simple

Example-Parameters

Example-MerchantTransactionID

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/charges' \

2

--header 'Accept-Language: <lang_code>' \

3

--header 'Authorization: Bearer <token>'\

```





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Query Parameters

amountFrom

number<double>

Inital amount range

>= 0

amountTo

number<double>

Final amount range

>= 0

culture

string

User's language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Example:en

currency

string

Transaction currency

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

disputes

string

Disputed transactions

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

type

string

Transactions types

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

payments

array[object]

id

integer

rId

string

merchantTransactionId

string

type

string

typeId

integer

operation

string

amount

integer

currency

string

status

string

description

string

applicationFeeAmount

integer

paymentMethod

string

paymentMethodId

integer

merchantId

integer

merchantName

string

createdDate

string

updatedDate

string

reference

null

totalCount

integer

hasMorePages

boolean

Auth

Token:

Parameters

amountFrom:

amountTo:

culture:Not Setenpt-BR

select an option

currency:

dateFrom:

dateTo:

disputes:

limit:

skip:

type:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/analytics/charges \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

Load examplesLarge examples are not rendered by default.

---

## Get all analytics or references

**Arquivo de origem:** `APIS/AppyPay-API/Get all analytics or references.html`

### Get all analytics/references

get

https://gwy-api-tst.appypay.co.ao/{version}/analytics/references

This service allows merchant support team to get a list of references. if you are a merchantAggregator, list all transactions of aggregates merchants. Also, allows merchant support team to search for specific charges based on filters. This functionality brings only succesfull transactions .



Example-Simple

Example-Parameters

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/references/dateFrom=2026-04-01&dateTo=2026-04-31&skip=0&top=20' \

2

--header 'Accept-Language: <lang_code>' \

3

--header 'Authorization: Bearer <token>'\

```





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Query Parameters

culture

string

User's language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Example:en

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

merchantId

string

FIlter by MerchantId

referenceNumber

string

Filter by referenceNumber

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

payments

array[object]

id

integer

transactionRId

string

merchantTransactionId

string

referenceNumber

string

amount

integer or number

bankFeesAmount

null

currency

null

description

null

entity

string

merchantId

integer

merchantName

string

periodNumber

string

logNumber

string

terminalType

string

terminalTypeDescription

string

providerPaymentDateTime

null or string

createdDate

string

updatedDate

string

totalCount

integer

hasMorePages

boolean

Auth

Token:

Parameters

culture:Not Setenpt-BR

select an option

dateFrom:

dateTo:

limit:

merchantId:

referenceNumber:

skip:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/analytics/references \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

Load examplesLarge examples are not rendered by default.

---

## Get all applications

**Arquivo de origem:** `APIS/AppyPay-API/Get all applications.html`

### Get all applications

get

https://gwy-api-tst.appypay.co.ao/{version}/applications

This service allows to get a list of all applications linked to a merchant.



Example-Simple

Example-Parameters

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/applications' \

2

--header 'Authorization: Bearer <token>'\

```





The list, by default, returns the data ordered (first created).



#### Request

Security: Bearer Auth

##### Query Parameters

isActive

boolean

Identifies if it should return elements that have active set to true/false

isDefault

boolean

Identifies if it should return default elements set to true/false

isEnabled

boolean

Identifies if it should return elements that have enabled set to true/false

limit

integer

Limit of returned records

Default:50

paymentMethod

string

The payment method tag name

Example:GPO, UMM, REF, eTPA

skip

integer

Number of records to skip before start collecting the results

Default:0

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

applications

array[object]

id

string<uuid>

name

string

description

string

paymentMethod

string

isDefault

boolean

isActive

boolean

isEnabled

boolean

CreatedBy

string

UpdatedBy

string

CreatedDate

string<date-time>

UpdatedDate

string<date-time>

applicationKeys

array[object]

totalCount

integer

hasMorePages

boolean

Auth

Token:

Parameters

isActive:Not SetFalseTrue

select an option

isDefault:Not SetFalseTrue

select an option

isEnabled:Not SetFalseTrue

select an option

limit:

paymentMethod:

skip:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/applications \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "applications": [

3

    {

4

      "id": "80528743-dc0e-4f6e-834c-55362c3761d2",

5

      "name": "AppyPay Automatic Test GPO",

6

      "description": "AppyPay Automatic Test GPO",

7

      "paymentMethod": "GPO",

8

      "isDefault": true,

9

      "isActive": true,

10

      "isEnabled": true,

11

      "CreatedBy": "DA",

12

      "UpdatedBy": "DA",

13

      "CreatedDate": "2023-07-07T11:47:42.7866667",

14

      "UpdatedDate": "2024-10-22T15:55:58.9843963",

15

      "applicationKeys": [

16

        {

17

          "apiKey": "f1b3cb1b-a906-497b-a91e-f26919a7d084",

18

          "webHookName": "AppyPay Automatic Test Webhook",

19

          "webHookdescription": "AppyPay Automatic Test Webhook",

20

          "webHookUrl": "https://webhook.site/478494c7-68d4-4288-9f7e-e18a81d5648b",

21

          "isActive": true

22

        }

23

      ]

24

    }

25

  ],

26

  "totalCount": 200,

27

  "hasMorePages": true

28

}

```

---

## Get all charges

**Arquivo de origem:** `APIS/AppyPay-API/Get all charges.html`

### Get all charges

get

https://gwy-api-tst.appypay.co.ao/{version}/charges

This service allows merchant support team to get a list of charges. Also, allows merchant support team to search for specific charges based on filters. This functionality is useful to check a pending payment status or check charges that meet some criteria.



Example-Simple

Example-Parameters

Example-MerchantTransactionID

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/charges' \

2

--header 'Accept-Language: <lang_code>' \

3

--header 'Authorization: Bearer <token>'\

```





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Query Parameters

amountFrom

number<double>

Inital amount range

>= 0

amountTo

number<double>

Final amount range

>= 0

culture

string

User's language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Example:en

currency

string

Transaction currency

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

disputes

string

Disputed transactions

limit

integer

Limit of returned records

Default:50

merchantTransactionId

string

Merchant transaction ID. This will be used to identify the transaction

skip

integer

Number of records to skip before start collecting the results

Default:0

type

string

Transactions types

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

payments

array[object]

id

string<uuid>

Gateway transaction ID. This will be used to identify the transaction

merchantTransactionId

string

A unique identifier of the transaction

<= 15 characters

type

string

operation

string

amount

number<double>

currency

string

status

any

Transaction status.

Allowed values:RequestedPendingSuccessFailed

description

string

Short description or notes

disputes

boolean

applicationFeeAmount

number<double>

paymentMethod

string

createdDate

string<date-time>

updatedDate

string<date-time>

options

object

The optional parameters names vary according to merchant

reference

object

Only available for some payment methods

Auth

Token:

Parameters

amountFrom:

amountTo:

culture:Not Setenpt-BR

select an option

currency:

dateFrom:

dateTo:

disputes:

limit:

merchantTransactionId:

skip:

type:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/charges \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

General-ExampleREF-Example

Response Example: General-Example

```
1

{

2

  "payments": [

3

    {

4

      "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",

5

      "merchantTransactionId": "string",

6

      "type": "string",

7

      "operation": "string",

8

      "amount": 0,

9

      "currency": "string",

10

      "status": "string",

11

      "description": "string",

12

      "disputes": true,

13

      "applicationFeeAmount": 0,

14

      "paymentMethod": "string",

15

      "createdDate": "2019-08-24T14:15:22Z",

16

      "updatedDate": "2019-08-24T14:15:22Z",

17

      "options": null,

18

      "reference": null

19

    }

20

  ]

21

}

```

---

## Get all fiscal documents

**Arquivo de origem:** `APIS/AppyPay-API/Get all fiscal documents.html`

### Get all fiscal documents

get

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents

This service allows merchant support team to get a list of fiscal documents.





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header.



#### Request

Security: Bearer Auth

##### Query Parameters

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

documents

array[object]

id

string<uuid>

required

Unique document identifier

documentNo

string

required

Unique document identification generated according to SAF-T(AO)

documentStatus

string

required

Document status.

Allowed values:PendingSuccessFailed

validationStatus

string

Result of processing the document. V = Valid; I = Invalid.

Allowed values:VI

rejectedDocumentNo

string

Identification of the document number previously submitted and rejected due to non-compliance.

documentType

string

required

Type of electronic billing document. Check full list of document types here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

eACCode

string

Economic activity code related to the document.

documentDate

string

required

Document issue date

customerTaxID

string

required

Customer tax identification number

customerCountry

string

required

Buyer country code (ISO 3166-1 alpha-2)

companyName

string

required

Name or designation of the taxpayer.

providerRequestId

string

Confirmation ID of a successful registration of request on tax authority.

providerResultCode

string

Result of processing the docu registration request.

providerResultDescription

string

Detaild message from provider.

createdDate

string

required

Date of creation.

updatedDate

string

required

Last update date

totalCount

integer

Total documents count

hasMorePages

boolean

Indicates if has more pages

Auth

Token:

Parameters

dateFrom:

dateTo:

limit:

skip:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "documents": [

3

    {

4

      "id": "6f1b5e7a-9a3d-4c8f-9f8a-3c2a1b9e45d2",

5

      "documentNo": "FR2026/000154",

6

      "documentStatus": "Failed",

7

      "validationStatus": "I",

8

      "rejectedDocumentNo": "FR2026/000153",

9

      "documentType": "FR",

10

      "eACCode": "EAC-AGT-001",

11

      "documentDate": "2026-01-15",

12

      "customerTaxID": "1234567890",

13

      "customerCountry": "AO",

14

      "companyName": "Appy Saúde, Lda",

15

      "providerRequestId": "REQ-AGT-20260115-00045",

16

      "providerResultCode": "E08",

17

      "providerResultDescription": "Número de documento duplicado para a série informada",

18

      "createdDate": "2026-01-15T15:12:30.000Z",

19

      "updatedDate": "2026-01-15T15:18:10.000Z"

20

    }

21

  ],

22

  "totalCount": 1,

23

  "hasMorePages": false

24

}

```

---

## Get all fiscal series

**Arquivo de origem:** `APIS/AppyPay-API/Get all fiscal series.html`

### Get all fiscal series

get

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-series

This service allows merchant support team to get a list of fiscal series.





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header.



#### Request

Security: Bearer Auth

##### Query Parameters

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

series

array[object]

Electronic documents numbering series code assigned by tax authority.

id

string<uuid>

Unique series identifier

seriesYear

integer

required

Year of issue associated with the numbering series. From January 1 to December 15, it is possible to create series only for the system year. After that date, it is possible to create series for the system year and for the year immediately following the system year.

seriesCode

string

required

Electronic documents numbering series code assigned by tax authority.

documentType

string

required

Type of electronic billing document. Check full list of document types here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

seriesStatus

string

required

Status of the document number series. A = Open series



U = Series in use



F = Closed series

Allowed values:AUF

seriesCreationDate

string<date>

required

Original creation date of the electronic series

firstDocumentApproved

string

Number of the first document in the range that was approved for issuance

lastDocumentApproved

string

Number of the last document in the range that was approved for issuance in this series

firstDocumentCreated

string

Number of the first document in the range that was approved for issuance

lastDocumentCreated

string

Number of the last document in the range that was approved for issuance in this series

invoicingMethod

string

What is the method for generating document. FEPC = Electronic invoicing issued on the Taxpayer Portal



FESF = Electronic invoicing issued via invoicing software



SF = Non-electronic invoicing issued via invoicing software

Allowed values:FEPCFESFSF

seriesContingencyIndicator

string

Identifies whether the numbering series is intended for issuance in a contingency regime. N = Normal issuance regime series; C = Series created to support issuance in a contingency regime

Allowed values:NC

totalCount

integer

Total documents count

hasMorePages

boolean

Indicates if has more pages

Auth

Token:

Parameters

limit:

skip:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-series \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "series": [

3

    {

4

      "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

5

      "seriesCode": "FT2026",

6

      "seriesYear": 2026,

7

      "documentType": "FT",

8

      "seriesStatus": "U",

9

      "seriesCreationDate": "2026-01-02",

10

      "firstDocumentApproved": "FT2026/000001",

11

      "lastDocumentApproved": "FT2026/999999",

12

      "firstDocumentCreated": "FT2026/000001",

13

      "lastDocumentCreated": "FT2026/000154",

14

      "invoicingMethod": "FESF",

15

      "seriesContingencyIndicator": "N"

16

    }

17

  ],

18

  "totalCount": 1,

19

  "hasMorePages": false

20

}

```

---

## Get all funds-transfers

**Arquivo de origem:** `APIS/AppyPay-API/Get all funds-transfers.html`

### Get all funds-transfers

get

https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers

This service allows merchant support team to get a list of funds-transfers. Also, allows merchant support team to search for specific funds-transfer based on filters. This functionality is useful to check a pending transfers status or check transfers that meet some criteria.



Example-Simple

Example-Parameters

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/funds-transfers' \

2

--header 'Accept-Language: <lang_code>' \

3

--header 'Authorization: Bearer <token>'\

```





API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Query Parameters

amountFrom

number<double>

Inital amount range

>= 0

amountTo

number<double>

Final amount range

>= 0

culture

string

User's language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Example:en

currency

string

Transaction currency

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

limit

integer

Limit of returned records

Default:50

merchantTransactionId

string

Merchant transaction ID. This will be used to identify the transaction

skip

integer

Number of records to skip before start collecting the results

Default:0

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

transfers

array[object]

id

string<uuid>

Geteway transaction ID. This will be used to identify the transaction

merchantTransactionId

string

A unique identifier of the transaction

type

string

currency

string

amount

number<double>

status

string

description

string

Short description or notes

disputes

boolean

paymentMethod

string

createdDate

string<date-time>

updatedDate

string<date-time>

Auth

Token:

Parameters

amountFrom:

amountTo:

culture:Not Setenpt-BR

select an option

currency:

dateFrom:

dateTo:

limit:

merchantTransactionId:

skip:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "transfers": [

3

    {

4

      "id": "6EC003A7-4B8A-47E6-B365-1885D7B716CF",

5

      "merchantTransactionId": "TMR20230217172053",

6

      "type": "Funds Transfers",

7

      "currency": "AOA",

8

      "amount": 100,

9

      "status": "Requested",

10

      "description": "PostmanTest-Prodution",

11

      "disputes": false,

12

      "paymentMethod": "FTBAI",

13

      "createdDate": "2023-02-17T17:20:53.7906375",

14

      "updatedDate": "2023-03-20T16:20:23.7757673"

15

    }

16

  ]

17

}

```

---

## Get all references

**Arquivo de origem:** `APIS/AppyPay-API/Get all references.html`

### Get all references

get

https://gwy-api-tst.appypay.co.ao/{version}/references

This service allows merchant support team to get a list of references.

#### Request

Security: Bearer Auth

##### Query Parameters

amountFrom

number<double>

Inital amount range

>= 0

amountTo

number<double>

Final amount range

>= 0

dateFrom

string<date-time>

Filter by initial date range

dateTo

string<date-time>

Filter by final date range

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

references

array[object]

id

integer

required

entity

string

required

referenceNumber

string

required

>= 9 characters<= 15 characters

currency

string

required

Default:AOA

amount

number<double>

minAmount

number<double>

maxAmount

number<double>

startDate

string<date-time>

required

expirationDate

string<date-time>

required

isActive

boolean

required

Default:true

createdBy

string

required

updatedBy

string

required

createdDate

string<date-time>

required

updatedDate

string<date-time>

required

Auth

Token:

Parameters

amountFrom:

amountTo:

dateFrom:

dateTo:

limit:

skip:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/references \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "references": [

3

    {

4

      "id": 1,

5

      "entity": "00348",

6

      "referenceNumber": "123456789",

7

      "currency": "AOA",

8

      "amount": 10,

9

      "minAmount": 1,

10

      "maxAmount": 10000,

11

      "startDate": "2022-01-01T15:00:00",

12

      "expirationDate": "2025-01-01T15:00:00",

13

      "isActive": true,

14

      "createdBy": "API Service",

15

      "updatedBy": "API Service",

16

      "createdDate": "2022-01-01T15:00:00",

17

      "updatedDate": "2022-01-01T15:00:00"

18

    }

19

  ]

20

}

```

---

## Get an account status

**Arquivo de origem:** `APIS/AppyPay-API/Get an account status.html`

### Get an account status

get

https://gwy-api-tst.appypay.co.ao/{version}/accounts/{identifier}

This service allows merchant support team to enquire the status of an account.





Supported payment methods: `UMM`







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Path Parameters

identifier

string

required

The unique indentifier of the account, usually is the mobile number

##### Query Parameters

culture

string

User's language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Example:en

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

paymentMethod

string

required

The payment method that should identify the merchant resouces

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

identifier

string

responseStatus

object

code

integer

message

string

source

string

Auth

Token:

Parameters

identifier*:

culture:Not Setenpt-BR

select an option

paymentMethod*:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/accounts/{identifier} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'paymentMethod: '

```

Response Example

```
1

{

2

  "identifier": "929443750",

3

  "responseStatus": {

4

    "code": 3,

5

    "message": "Active",

6

    "source": "UMM"

7

  }

8

}

```

---

## Get an application point-of-sales

**Arquivo de origem:** `APIS/AppyPay-API/Get an application point-of-sales.html`

### Get an application point-of-sales

get

https://gwy-api-tst.appypay.co.ao/{version}/applications/{id}

This service allows to get a list of all points of sale linked to a merchant application.



Example-Simple

Example-Parameters

```
Sample cURL - Simple

1

curl --location --request GET '{{server}}/{{api_version}}/applications/{id}' \

2

--header 'Authorization: Bearer <token>'\

```





The list, by default, returns the data ordered (first created).



#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

The application universal unique identifier

##### Query Parameters

isActive

boolean

Identifies if it should return elements that have active set to true/false

isDefault

boolean

Identifies if it should return default elements set to true/false

limit

integer

Limit of returned records

Default:50

skip

integer

Number of records to skip before start collecting the results

Default:0

supportBank

string

The suport bank abbreviation name

Example:BAI, BCI, BIC, BFA, SBA

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

application

object

id

string<uuid>

required

name

string

posItems

array[object]

totalCount

integer

hasMorePages

boolean

Auth

Token:

Parameters

id*:

isActive:Not SetFalseTrue

select an option

isDefault:Not SetFalseTrue

select an option

limit:

skip:

supportBank:

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request GET \

  --url https://gwy-api-tst.appypay.co.ao/{version}/applications/{id} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123'

```

Response Example

```
1

{

2

  "application": {

3

    "id": "80528743-dc0e-4f6e-834c-55362c3761d2",

4

    "name": "AppyPay Automatic Test GPO",

5

    "posItems": [

6

      {

7

        "id": "d7589b29-7e51-4e15-84e7-88121e4ff3b3",

8

        "posCode": "TPA000412",

9

        "name": "TPA412",

10

        "description": "Luanda - Miramar - TPA412",

11

        "ipAdress": "192.168.1.10",

12

        "port": "7777",

13

        "serialNumber": "202717303221017317317214955",

14

        "macAddress": "54:E1:40:E4:06:10",

15

        "supportBank": "BAI",

16

        "isDefault": true,

17

        "isActive": true,

18

        "createdBy": "DA",

19

        "updatedBy": "DA",

20

        "createdDate": "2023-07-07T11:47:42.7866667",

21

        "updatedDate": "2024-10-22T15:55:58.9843963"

22

      }

23

    ],

24

    "totalCount": 200,

25

    "hasMorePages": true

26

  }

27

}

```

---

## Post a Charge

**Arquivo de origem:** `APIS/AppyPay-API/Post a Charge.html`

### Post a Charge

post

https://gwy-api-tst.appypay.co.ao/{version}/charges

This service allows merchant support team to create a charge.





The required payment information (paymentInfo) of a charge can be different based on the payment method. Please check the Body Examples in the right panel or payment method details here.







For SDD payments, an ACTIVE mandate is required to make the payment. The mandateId passed in the paymentInfo must be active and payment details must abide by rules defined in the mandate.







For GPO payments, the phoneNumber field is used to simulate different payment response scenarios. Please refer to the Body Examples on the right panel for more details.







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.





##### Request Types



This endpoint supports both synchronous and asynchronous clients. By default the request will be synchronous.



###### Synchronous



In this case the client sends a request, and waits for a response with transaction result with a HTTP 200 code.





Depending on the payment method the responses can take up to 90 seconds.





###### Asynchronous



In this case the client sends a request, if accepted, is notified with a HTTP 202 code. The endpoint will continue running the task on background, sending the result of the transaction by triggering a request POST with the result.





The POST will be sent to the configured merchant Webhook (check here), and will have the same body as described as sample payload.







Use Accept header to choose the request type.


- Synchronous: `application/json`

- Asynchronous: `application/vnd.appypay.asyncapi+json`


#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

amount

number<double>

required

Amount to be charged. Minimun amount can change based on the payment method

>= 1

Example:100.2

currency

string

required

Currency

>= 1 characters<= 3 characters

Allowed value:AOA

Default:AOA

description

string

Short description or notes. No special characters are allowed.

>= 1 characters

merchantTransactionId

string

required

A unique identifier of the transaction

>= 1 characters<= 15 characters

Match pattern:^[a-zA-Z0-9]+$

paymentMethod

string

required

Unique payment method identifier formed by payment method identifier and a key that needs to be generated in merchant's account.Please check payment methods articles for identifiers: https://appypay.stoplight.io/docs/appypay-payment-gateway/6a14vlzwhui8u-supported-payment-methods

>= 1 characters

Example:GPO_53c70da3-1c88-4391-8b60-ab4757fbb044

paymentInfo

object

The payment info varies according to the payment method. Please check payment methods articles for examples: https://appypay.stoplight.io/docs/appypay-payment-gateway/6a14vlzwhui8u-supported-payment-methods

options

object

The optional parameters names vary according to merchant

notify

object

Notifications are recommended for REF payment method

name

string

Customer name

telephone

string

Telephone that will receive SMS notification

email

string

Email that will receive Email notification

smsNotification

boolean

Notify by SMS

Default:false

emailNotification

boolean

Notify by Email

Default:false

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

required

responseStatus

object

required

successful

boolean

required

status

any

required

Transaction status.

Allowed values:RequestedPendingSuccessFailed

code

integer

required

message

string

required

source

string

required

sourceDetails

object

required

reference

object

Only available for some payment methods

eletronicReceipt

object

Only available for some payment methods

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

Examples

{ "amount": 123, "currency": "AOA", "description": "POSTMAN_Test", "merchantTransactionId": "TR00000180320", "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044", "paymentInfo": { "PaymentInfo1": "string" }, "options": { "Option1": "string", "Option2": "string" }, "notify": { "name": "Customer A", "telephone": "923111111", "email": "customera@mail.com", "smsNotification": true, "emailNotification": true } }

```
1

{

2

  "amount": 123,

3

  "currency": "AOA",

4

  "description": "POSTMAN_Test",

5

  "merchantTransactionId": "TR00000180320",

6

  "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044",

7

  "paymentInfo": {

8

    "PaymentInfo1": "string"

9

  },

10

  "options": {

11

    "Option1": "string",

12

    "Option2": "string"

13

  },

14

  "notify": {

15

    "name": "Customer A",

16

    "telephone": "923111111",

17

    "email": "customera@mail.com",

18

    "smsNotification": true,

19

    "emailNotification": true

20

  }

21

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/charges \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "amount": 123,

  "currency": "AOA",

  "description": "POSTMAN_Test",

  "merchantTransactionId": "TR00000180320",

  "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044",

  "paymentInfo": {

    "PaymentInfo1": "string"

  },

  "options": {

    "Option1": "string",

    "Option2": "string"

  },

  "notify": {

    "name": "Customer A",

    "telephone": "923111111",

    "email": "customera@mail.com",

    "smsNotification": true,

    "emailNotification": true

  }

}'

```

UMM - ExampleREF - ExampleGPO - ExampleSDD - ExampleETPA - ExampleMBWAY - ExampleMBREF - ExampleSIBSCARD - Example

Response Example: UMM - Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "responseStatus": {

4

    "successful": true,

5

    "status": "Success",

6

    "code": 100,

7

    "message": "Thank you! The payment has been successfully registered.",

8

    "source": "UMM",

9

    "sourceDetails": {

10

      "attempt": 1,

11

      "type": "NONE",

12

      "code": "NONE",

13

      "message": "OK"

14

    },

15

    "reference": null

16

  }

17

}

```

---

## Post a GPO QR Code

**Arquivo de origem:** `APIS/AppyPay-API/Post a GPO QR Code.html`

### Post a GPO QR Code

post

https://gwy-api-tst.appypay.co.ao/{version}/qr-codes

This service allows merchant support team to create a GPO QR Code.





The Qr code can be shared with customers to pay using EMIS Multicaixa Mobile App.







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

Body request to create a GPO QR code.

amount

number<double>

required

Amount to be charged.

>= 1

Example:100.2

currency

string

required

Currency

>= 1 characters<= 3 characters

Allowed value:AOA

Example:AOA

merchantTransactionId

string

required

A unique identifier of the transaction

>= 1 characters<= 15 characters

Match pattern:^[a-zA-Z0-9]+$

paymentMethod

string

required

Unique payment method identifie

>= 1 characters

description

string

Short description or notes

>= 1 characters

qrCodeType

any

required

Default value SINGLE and if MULTIPLE the fields minAmount, maxTransaction, startDate and endDate are mandatory.

Allowed values:SINGLEMULTIPLE

minAmount

number<double>

Minimum amount to be charged using this QR Code.

>= 1

Example:100.2

maxTransactions

integer

Maximum number of transactions to be used with this QR Code.

>= 2

Example:4

startDate

string<date>

The start date when this QR Code should be available from.

Example:2024-11-19

endDate

string<date>

The end date related to when this QR Code should be available for use.

Example:2024-11-19

options

object

The optional parameters names vary according to merchant

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

required

qrCodeArr

string

required

responseStatus

object

required

successful

boolean

required

status

string

code

integer

required

message

string

required

source

string

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

{ "amount": 300.23, "currency": "AOA", "merchantTransactionId": "A12345678912345", "paymentMethod": "GPO_53c70da3-1c88-4391-8b60-ab4757fbb044", "description": "Payment X", "qrCodeType": "SINGLE", "minAmount": 1000, "maxTransactions": 5, "startDate": "2024-11-19", "endDate": "2024-11-19", "options": { "Option1": "string", "Option2": "string" } }

```
1

{

2

  "amount": 300.23,

3

  "currency": "AOA",

4

  "merchantTransactionId": "A12345678912345",

5

  "paymentMethod": "GPO_53c70da3-1c88-4391-8b60-ab4757fbb044",

6

  "description": "Payment X",

7

  "qrCodeType": "SINGLE",

8

  "minAmount": 1000,

9

  "maxTransactions": 5,

10

  "startDate": "2024-11-19",

11

  "endDate": "2024-11-19",

12

  "options": {

13

    "Option1": "string",

14

    "Option2": "string"

15

  }

16

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/qr-codes \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "amount": 300.23,

  "currency": "AOA",

  "merchantTransactionId": "A12345678912345",

  "paymentMethod": "GPO_53c70da3-1c88-4391-8b60-ab4757fbb044",

  "description": "Payment X",

  "qrCodeType": "SINGLE",

  "minAmount": 1000,

  "maxTransactions": 5,

  "startDate": "2024-11-19",

  "endDate": "2024-11-19",

  "options": {

    "Option1": "string",

    "Option2": "string"

  }

}'

```

Response Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "qrCodeArr": "iVBORw0KGgoAAAANSUhEUgAAAMgAAADIAQAAAACFI5MzAAADfklEQVR42u3XPbKtKBAAYEhkC5LI1jSRLUDCTwJb0AS2BglsQRJ4PZl3qnxFNDXBNTv1nfI03dDNQePrQb/yK7/y30tC53rSIJsvpOWAyITUvgsZZC6KN3sXXSekLLu8W0Ky2Wyvc+dTIugYfaVdl23bJkX6esmOSJfDlymp/fCX2lZFizou9WM9XwLZeT8/8/YhY+SuL7WoTd4j6B/1+ZK+8KSLEAgXtdJnIxNSeLv7UXBzBySWxjghSWlDC3fs7tpsOLEJybmfPGwnto/0TrY6Ic+yIj2MIiNt6Ag4Tkj1uUHohuZCoqO3nxDIjr1YpzbwzuFDnJDncNg/68JqdcTBbpmQsu7ayIKNkI+Ab8UJaT4Gcl+nEJBVp+OM9BPnXPjFHJI5LLueECjwo4i3tQZci6x+RnbFhkHUJhp22k8yIYXaLq9V0PrgWB82JqSaTZEieH5wSyt57apvSfwe0R0J7az5IG2dkIKWBd/Z17AvOw0Lm5CE6/3ITroeiSX5PiWfUk5mvX102U9Sb7ezCcne8YR4rmnFNchRJ6Q9qwIIpyzqZ9Tf0o/77vuC+DCkFhrrhAyzaN9sQeuqeECIzUhNQm36UQjDwCCvXfUXcadgvvVT7QoiP/WENJ9tOga0PWJWXl9v+xZYJdQuKSRwqxC1nhBoL9bt/IElxphbrRPSLunEKfiljdg37OOEZA8piQlWm0gsG5mRLpghzwltAoKJ2bAJqa2vSind+Q0dA7+68rekHTuS3YILzNo7tzghncN8iYl0hPC/ov6U0eUjrU1wfWD5bnFGoNJdLLwcHY9mFK8TUjYeq1mhRdhnY/lVhW+psD3YQw06soXhRPyEZCdoWvh4tlPbS19sQqot566odwup1YhX1N/Sin5ky9XRIHaSA5uQfEdIDx8X7iTsG/cT0gwvcBnM/iKw+Z+VTQhspEu3gqHqw3eS64T0nZeTFOnvLgTNNU5I8zVRB5m8mx01ED8hfcUwNZJ0uIhlO15V+Bb4SQ9TnTxqwXBKXlF/y3MeQbD7QtupeE6vHf8t/7zPZgMFN/gOJI8JSUgnKDLc2D2cXve61XxL7dKdxDt1+Lt2nviElIXDDBMIrYgZnF7d/6/SjECbztlGKOCYksOI41p1NroG9Z6nnwJRjxwo3ARwHh2xOiEJ2r7beMKwzl22pCfk93/jr/zK/0D+AB5xfsQ9t3k2AAAAAElFTkSuQmCC",

4

  "responseStatus": {

5

    "successful": true,

6

    "status": "Active",

7

    "code": 103,

8

    "message": "QR code successfully created.",

9

    "source": "GPO"

10

  }

11

}

```

---

## Post a Mandate

**Arquivo de origem:** `APIS/AppyPay-API/Post a Mandate.html`

### Post a Mandate

post

https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates

This service allows merchant to create a direct debit payment mandate.



The payment mandate is the contract between the creditor (merchant) and the debitor (end user) that upon submission and activation of the contract, it allows a payment intent to be submitted and the debitor to be charged once approved by the payment provider





The application must be linked to SDD payment method.



#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

multipart/form-data

multipart/form-data

applicationKey

string<uuid>

required

Mandate Application Key. This will allow the configured webhook to be called on mandate status updates

Example:3fa85f64-5717-4562-b3fc-2c963f66afa6

creditorAccId

integer

Validate if creditor account exists and make sure that it is active. See Get Application Creditor Accounts

currencyId

string

required

Must be a registered a currency.

Example:'AOA'

purposeCode

string

Code of the purpose for the payment. Max 4 characters. Should be a valid MandatePurposeCode. See Get Mandate Purpose Codes

Example:'UTIL'

purposeCategoryCode

string

Code for the category of the purpose for the payment. Max 4 characters. Should be a valid MandatePurposeCode. See See Get Mandate Purpose Category Codes

mandateType

any

Max 3 characters. Should be a valid MandateTypeCode. See Get Mandate Types

Allowed values:'CAP''SAP'

frequencyType

any

required

Max 4 characters. Should be a valid MandateFrequencyTypeCode. See Get Mandate Frequency Types

Allowed values:'ADHO''DAIL''MIAN''MNTH''QURT''WEEK''YEAR'

sequenceTypeCode

string

Indicates the allowed recurrency of debits to the mandate ('OFF' - Once-off or 'RCUR' - Recurrent).

merchantReferenceNumber

string

required

Max. 20 characters alphanumeric. Important: Remove special characters.

debitStartDate

string<date>

required

Must be today or in the future. Must be omitted for SAP mandate types

debitEndDate

string<date>

Omit this field for a mandate without expiry date. If passed must be in the future and after the debitStartDate

debitDay

integer

Must be bigger than 0. This is an optional field

serviceDescription

string

required

Max of 50 characters allowed

maxAmount

number<double>

Optional field. Omit if no limit is needed. If present must be bigger than 0

debitorName

string

required

Max of 70 characters. No special characters allowed. Transform any special character into its allowed counterpart. Example: `'João Luís Antônio Lorenço'` -> `'Joao Luis Antonio Lorenco'`. Remove any other unsupported character.



Allowed characters: `a-z`, `A-Z`, `0-9`, `/ - ? : ( ) . , ' + Space`

debitorNIF

string

required

Max of 15 characters (should be stored as uppercase)

debitorIBAN

string

required

Must be exactly 25 characters. Must start with 'AO'

debitorTelephone

string

Optional field. Must be 14 characters. Must be in the following format +CCC-NNNNNNNNN. Where C is the country code and N is the number.

Example:+244-923445566

debitorEmail

string

Optional field. Should be a valid email format.

Example:email@appypay.co.ao

debitorSignaturePlace

string

required

Max of 20 characters. Description of the signature location. Must be omitted for SAP mandate types

Example:Agencia Mutamaba

debitorSignatureDate

string<date-time>

required

Must be a valid datetime (in UTC/GMT), bigger or equal to request date. Must be omitted for SAP mandate types

Example:2025-06-03T10:21:57.855Z

debitorSignature

string<binary>

required

This should be a file upload of the debitor signature. Supported formats: png or jpg. Max file size 20 KB. Must be omitted for SAP mandate types

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

required

responseStatus

object

required

successful

boolean

required

status

any

required

Transaction status.

Allowed values:RequestedPendingSuccessFailed

code

integer

required

message

string

required

source

string

required

sourceDetails

object

required

reference

object

Only available for some payment methods

eletronicReceipt

object

Only available for some payment methods

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

applicationKey*:

creditorAccId:

Omit creditorAccId

currencyId*:

purposeCode:

Omit purposeCode

purposeCategoryCode:

Omit purposeCategoryCode

mandateType:Not Set'CAP''SAP'

select an option

Omit mandateType

frequencyType*:'ADHO''DAIL''MIAN''MNTH''QURT''WEEK''YEAR'

'ADHO'

sequenceTypeCode:

Omit sequenceTypeCode

merchantReferenceNumber*:

debitStartDate*:

debitEndDate:

Omit debitEndDate

debitDay:

Omit debitDay

serviceDescription*:

maxAmount:

Omit maxAmount

debitorName*:

debitorNIF*:

debitorIBAN*:

debitorTelephone:

Omit debitorTelephone

debitorEmail:

Omit debitorEmail

debitorSignaturePlace*:

debitorSignatureDate*:

debitorSignature*:

Upload

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/direct-debit/mandates \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: multipart/form-data' \

  --form applicationKey=3fa85f64-5717-4562-b3fc-2c963f66afa6 \

  --form creditorAccId= \

  --form 'currencyId='\''AOA'\''' \

  --form purposeCode= \

  --form purposeCategoryCode= \

  --form mandateType= \

  --form 'frequencyType='\''ADHO'\''' \

  --form sequenceTypeCode= \

  --form merchantReferenceNumber= \

  --form debitStartDate= \

  --form debitEndDate= \

  --form debitDay= \

  --form serviceDescription= \

  --form maxAmount= \

  --form debitorName= \

  --form debitorNIF= \

  --form debitorIBAN= \

  --form debitorTelephone= \

  --form debitorEmail= \

  --form 'debitorSignaturePlace=Agencia Mutamaba' \

  --form debitorSignatureDate=2025-06-03T10:21:57.855Z \

  --form debitorSignature=

```

UMM - ExampleREF - ExampleGPO - ExampleSDD - ExampleETPA - ExampleMBWAY - ExampleMBREF - ExampleSIBSCARD - Example

Response Example: UMM - Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "responseStatus": {

4

    "successful": true,

5

    "status": "Success",

6

    "code": 100,

7

    "message": "Thank you! The payment has been successfully registered.",

8

    "source": "UMM",

9

    "sourceDetails": {

10

      "attempt": 1,

11

      "type": "NONE",

12

      "code": "NONE",

13

      "message": "OK"

14

    },

15

    "reference": null

16

  }

17

}

```

---

## Post a charge refund

**Arquivo de origem:** `APIS/AppyPay-API/Post a charge refund.html`

### Post a charge refund

post

https://gwy-api-tst.appypay.co.ao/{version}/refunds/{id}

This service allows merchant support team to refund a charge.





It's possible to perform a partial or total refund.







This operation is not supported by all payment methods. Please check payment method details here







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.



#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

Gateway transaction ID. This will be used to identify the transaction

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

##### Body

application/json

application/json

amount

number<double>

required

> 1

description

string

required

Short description or notes. No special characters are allowed.

reasonCode

string

(Required for SDD payment method) Code for reason for refund.



The reason code justifies the motive for the refund of the direct debit payment.


 | Code | Reason
 | ADEA | Amount debited after end of service
 | AM05 | Duplicate operation
 | AM09 | Amount diverges from previously agreed
 | DUPL | Duplicated Intent debit
 | MS02 | Intent refused by debtor - No specified reason
 | MS03 | Intent refused by debtor bank - No specified reason

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

id

string

responseStatus

object

successful

boolean

status

any

Allowed values:RequestedPendingSuccessFailed

code

integer

message

string

source

string

sourceDetails

object

eletronicReceipt

object

Only available for some payment methods

Auth

Token:

Parameters

id*:

Content-Type*:application/json

application/json

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

{ "amount": 250.99, "description": "Refund" }

```
1

{

2

  "amount": 250.99,

3

  "description": "Refund"

4

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/refunds/{id} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "amount": 250.99,

  "description": "Refund"

}'

```

UMM - ExampleGPO - Example ETPA - ExampleMBWAY - ExampleMBREF - ExampleSIBSCARD - Example

Response Example: UMM - Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "responseStatus": {

4

    "successful": true,

5

    "status": "Success",

6

    "code": 100,

7

    "message": "Thank you! The payment has been successfully registered.",

8

    "source": "UMM",

9

    "sourceDetails": {

10

      "attempt": 1,

11

      "type": "NONE",

12

      "code": "NONE",

13

      "message": "OK"

14

    }

15

  }

16

}

```

---

## Post a charge reverse

**Arquivo de origem:** `APIS/AppyPay-API/Post a charge reverse.html`

### Post a charge reverse

post

https://gwy-api-tst.appypay.co.ao/{version}/reverses/{id}

This service allows merchant support team to reverse a charge.





This operation is only supported by UMM payment method.







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or path parameter culture.



#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

Gateway transaction ID. This will be used to identify the transaction

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

##### Body

application/json

application/json

amount

number<double>

> 1

description

string

Short description or notes. No special characters are allowed.

#### Responses

200

OK

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

required

responseStatus

object

required

successful

boolean

required

status

any

required

Transaction status.

Allowed values:RequestedPendingSuccessFailed

code

integer

required

message

string

required

source

string

required

sourceDetails

object

required

reference

object

Only available for some payment methods

eletronicReceipt

object

Only available for some payment methods

Auth

Token:

Parameters

id*:

Content-Type*:application/json

application/json

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

{ "amount": 250.99, "description": "reverse the transaction" }

```
1

{

2

  "amount": 250.99,

3

  "description": "reverse the transaction"

4

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/reverses/{id} \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "amount": 250.99,

  "description": "reverse the transaction"

}'

```

UMM - ExampleREF - ExampleGPO - ExampleSDD - ExampleETPA - ExampleMBWAY - ExampleMBREF - ExampleSIBSCARD - Example

Response Example: UMM - Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "responseStatus": {

4

    "successful": true,

5

    "status": "Success",

6

    "code": 100,

7

    "message": "Thank you! The payment has been successfully registered.",

8

    "source": "UMM",

9

    "sourceDetails": {

10

      "attempt": 1,

11

      "type": "NONE",

12

      "code": "NONE",

13

      "message": "OK"

14

    },

15

    "reference": null

16

  }

17

}

```

---

## Post a fiscal document

**Arquivo de origem:** `APIS/AppyPay-API/Post a fiscal document.html`

### Post a fiscal document

post

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents

This service allows merchant support team to create a single electronic fiscal document.



To create a fiscal document a open fiscal serie is required. Refer to the series endpoints to create a new one.





Different document types can be generated. Please refer to the Body Examples on the right panel for more details. Or to the fiscal documents article to get the full list of supported documents.







Only one document per request is allowed.





This service only supports asynchronous request, if accepted, the client is notified with a HTTP 202 code. The endpoint will continue running the task on background, sending the result of the request by triggering a request POST with the result.





The POST will be sent to the configured merchant Webhook (check here), and will have the same body as described as sample payload for non transactional webhooks.



#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

documentNo

string

Unique document identification generated according to SAF-T(AO). If not provided, it will be generated by the gateway.

documentStatus

string

Current status of the billing document. N = Normal; C = Correction of a previously rejected document.

Allowed values:NC

Default:N

rejectedDocumentNo

string

Document number previously rejected. Mandatory when documentStatus = C.

documentDate

string<date>

required

Document issue date.

documentType

string

Type of electronic billing document. Check full list of document types here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

Allowed values:FTFR

Default:FT

eacCode

string

Economic activity code related to the document.

customerTaxID

string

required

Customer tax identification number. Use the value “999999999” for domestic requests without buyer identification.

customerCountry

string

required

Buyer country code (ISO 3166-1 alpha-2). Use “AO” for domestic buyers.

companyName

string

required

Name or designation of the taxpayer.

lines

array[object]

List of billing document lines. Mandatory for the majority of document types.

lineNumber

integer

required

Line number starting at 1.

operationType

string

Operation type related to the line. Check full list of operation types here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

Allowed values:SGSESSSTPSRSIFSHSSTTBASQTRD

Default:SG

operationDate

string<date>

Operation date.

productCode

string

required

Product or service code.

productDescription

string

required

Description of the product or service

quantity

number<double>

required

Quantity, whole or decimal.

unitOfMeasure

string

required

Unit of measurement.

unitPrice

number<double>

Discounted unit price excluding taxes. Mandatory if any discount applied.

unitPriceBase

number<double>

required

Base unit price without discounts and taxes.

referenceInfo

object

Object detailing the reference for the base document for this billing document.



Mandatory for billing documents of type:



NC, to indicate the base invoice where the return of items took place.

taxes

array[object]

Array of objects that specify the tax(es) calculated for the line. If not provided, IVA with 14% will be applied.

paymentReceipt

object

Object containing receipt data, which must be filled in for the following invoice types (documentType):



AR - Collection Notice/Receipt



RC - Receipt Issued



RG - Other Receipts Issued



This element is not filled in for other types of billing documents.

sourceDocuments

array[object]

Paid billing document data.

withholdingTaxList

array[object]

withholdingTaxType

string

required

Withholding tax or retention code. Check full list of tax codes here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

Allowed values:IRTIIISIVAIPIACOUIRPCIRPS

withholdingTaxDescription

string

The reason for withholding tax. The applicable legal provisions or the applicable tax rate must be indicated.

withholdingTaxAmount

number

required

Withholding tax amount.



When it comes to a billing document of one of the following types:



AR - Collection notice/receipt



RC - Receipt issued



RG - Other receipts issued



This amount is calculated by grouping the withholdingTaxAmount values for the same tax type (withholdingTaxType) from the different source documents settled by the receipt, with NCs being recorded with a negative sign.

#### Responses

202

Request accepted for asynchronous processing

##### Body

application/json

application/json

responses

/

202

id

string<uuid>

required

Unique document identifier

responseStatus

object

required

code

integer

required

Unique response code

message

string

required

Short description of the response

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Body

Examples

{ "documentDate": "2025-11-04", "customerTaxID": "PT987654321", "customerCountry": "PT", "companyName": "Cliente Exemplo Lda", "lines": [ { "lineNumber": 1, "productCode": "PROD001", "productDescription": "Produto Exemplo 1", "quantity": 2, "unitOfMeasure": "UN", "unitPriceBase": 250 } ] }

```
1

{

2

  "documentDate": "2025-11-04",

3

  "customerTaxID": "PT987654321",

4

  "customerCountry": "PT",

5

  "companyName": "Cliente Exemplo Lda",

6

  "lines": [

7

    {

8

      "lineNumber": 1,

9

      "productCode": "PROD001",

10

      "productDescription": "Produto Exemplo 1",

11

      "quantity": 2,

12

      "unitOfMeasure": "UN",

13

      "unitPriceBase": 250

14

    }

15

  ]

16

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "documentDate": "2025-11-04",

  "customerTaxID": "PT987654321",

  "customerCountry": "PT",

  "companyName": "Cliente Exemplo Lda",

  "lines": [

    {

      "lineNumber": 1,

      "productCode": "PROD001",

      "productDescription": "Produto Exemplo 1",

      "quantity": 2,

      "unitOfMeasure": "UN",

      "unitPriceBase": 250

    }

  ]

}'

```

Response Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "responseStatus": {

4

    "code": 101,

5

    "message": "The request has been accepted for processing."

6

  }

7

}

```

---

## Post a fiscal series

**Arquivo de origem:** `APIS/AppyPay-API/Post a fiscal series.html`

### Post a fiscal series

post

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-series

This service allows merchant support team to create a fiscal serie.





A open fiscal serie is required to create fiscal documents.



#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

seriesYear

string

required

Year of issue associated with the numbering series. From January 1 to December 15, it is possible to create series only for the system year. After that date, it is possible to create series for the system year and for the year immediately following the system year.

documentType

string

required

Type of electronic billing document. Check full list of document types here: https://appypay.stoplight.io/docs/appypay-payment-gateway/gxxuvcuyio913-fiscal-documents

Allowed values:FTFRNC

establishmentNumber

string

required

Identifies the establishment requesting the issuance

seriesContingencyIndicator

string

required

Identifies whether the numbering series is intended for issuance in a contingency regime. N = Normal issuance regime series; C = Series created to support issuance in a contingency regime

Allowed values:NC

#### Responses

200

Example response

##### Body

application/json

application/json

responses

/

200

id

string<uuid>

Unique series identifier

series

object

seriesCode

string

Electronic documents numbering series code assigned by tax authority.

authorizedQuantity

string

The number of documents that tax authority has approved for issuance

firstDocumentNo

string

Identifier of the first electronic document that can be issued in the new series or extension of an existing series

lastDocumentNo

string

Identifier of the last electronic document that can be issued in the new series or extension of an existing series

responseStatus

object

code

integer

Unique response code

status

string

Status of the operation

Allowed values:PendingSuccessFailed

message

string

Short description of the response

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Body

{ "seriesYear": "2025", "documentType": "FT", "establishmentNumber": "10", "seriesContingencyIndicator": "N" }

```
1

{

2

  "seriesYear": "2025",

3

  "documentType": "FT",

4

  "establishmentNumber": "10",

5

  "seriesContingencyIndicator": "N"

6

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-series \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "seriesYear": "2025",

  "documentType": "FT",

  "establishmentNumber": "10",

  "seriesContingencyIndicator": "N"

}'

```

Response Example

```
1

{

2

  "id": "50625c7f-894b-410b-9ee8-6ef958a534d9",

3

  "series": {

4

    "seriesCode": "LD6325S2042N",

5

    "authorizedQuantity": "999999999999",

6

    "firstDocumentNo": "1",

7

    "lastDocumentNo": "999999999999"

8

  },

9

  "responseStatus": {

10

    "code": 100,

11

    "status": "Success",

12

    "message": "Series successfully created."

13

  }

14

}

```

---

## Post a funds-transfers

**Arquivo de origem:** `APIS/AppyPay-API/Post a funds-transfers.html`

### Post a funds-transfers

post

https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers

This service allows merchant support team to create a funds transfer request.



The transfer is only processed after authorization. Please check the endpoint here





The required transfer information of a fund-tranfer can be different based on the payment method. Please check the Body Examples in the right panel or payment method details here.







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.





#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

paymentMethod

string

required

Match pattern:/^[A-Z]{5}_[{]?[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}[}]?$/gm

merchantTransactionId

string

required

A unique identifier of the transaction indicated by the merchant

>= 0 characters<= 15 characters

Example:12B5h4456789Z23

Match pattern:^[0-9a-zA-Z]{0,15}$

description

string

A user-defined description for the operation. Special character are NOT allowed.

>= 0 characters<= 35 characters

Match pattern:^[a-zA-Z ]{0,35}$

transferInfo

array[object]

The transfer info varies according to the payment method

categoryCode

string

required

ISO code of the transfer category. See allowed values here:https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/809pcqp2gtyrx-funds-transfers#iso-codes

Example:CASH

reasonCode

string

required

ISO code of the transfer reason. See allowed values here:https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/809pcqp2gtyrx-funds-transfers#iso-codes

Example:CASH

feePayerCode

string

Fee payer code. See allowed values here:https://appypay.stoplight.io/docs/appypay-payment-gateway/branches/main/809pcqp2gtyrx-funds-transfers#iso-codes

Example:OUR

amount

number<double>

required

The monetary amount to be debited.

>= 1<= 9999999999.99

currency

string

The currency to be used to debit the account. If omitted, the default value is AOA.

>= 1 characters<= 3 characters

Default:AOA

Example:AOA

creditorIban

string

required

IBAN number to be credited.

Example:AO06004000001007938230142

Match pattern:(^[0-9]{10}$)|^[Aa][Oo]06\d{21}$)

creditorName

string

required

The name of the recipient of the transaction.

>= 5 characters<= 35 characters

Example:Nzinga Mbandi

Match pattern:^[a-zA-Z ]{5,35}$

description

string

required

A user-defined description for the operation. Special character are NOT allowed.

>= 0 characters<= 35 characters

Match pattern:^[a-zA-Z ]{0,35}$

#### Responses

202

OK

##### Body

application/jsonapplication/xml

application/json

responses

/

202

id

string<uuid>

responseStatus

object

successful

boolean

code

integer

message

string

source

string

authorizationDetails

object

sourceDetails

object

Auth

Token:

Parameters

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

Examples

{ "paymentMethod": "string", "merchantTransactionId": "12B5h4456789Z23", "description": "string", "transferInfo": [ { "categoryCode": "string", "reasonCode": "string", "feePayerCode": "string", "amount": 1, "currency": "AOA", "creditorIban": "AO06004000001007938230142", "creditorName": "Nzinga Mbandi", "description": "string" } ] }

```
1

{

2

  "paymentMethod": "string",

3

  "merchantTransactionId": "12B5h4456789Z23",

4

  "description": "string",

5

  "transferInfo": [

6

    {

7

      "categoryCode": "string",

8

      "reasonCode": "string",

9

      "feePayerCode": "string",

10

      "amount": 1,

11

      "currency": "AOA",

12

      "creditorIban": "AO06004000001007938230142",

13

      "creditorName": "Nzinga Mbandi",

14

      "description": "string"

15

    }

16

  ]

17

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers \

  --header 'Accept: application/json, application/xml' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "paymentMethod": "string",

  "merchantTransactionId": "12B5h4456789Z23",

  "description": "string",

  "transferInfo": [

    {

      "categoryCode": "string",

      "reasonCode": "string",

      "feePayerCode": "string",

      "amount": 1,

      "currency": "AOA",

      "creditorIban": "AO06004000001007938230142",

      "creditorName": "Nzinga Mbandi",

      "description": "string"

    }

  ]

}'

```

Response Example

```
1

{

2

  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",

3

  "responseStatus": {

4

    "successful": true,

5

    "code": 101,

6

    "message": "The request has been accepted for processing.",

7

    "source": "FTBAI",

8

    "authorizationDetails": {

9

      "duration": 300,

10

      "durationUnit": "s",

11

      "authorizationToken": "b2577735-50cb-44b9-b606-b71cccd33ea7"

12

    },

13

    "sourceDetails": {

14

      "type": "NONE",

15

      "code": "NONE",

16

      "message": "Finalizado"

17

    }

18

  }

19

}

```

---

## Post an authorisation funds-transfers

**Arquivo de origem:** `APIS/AppyPay-API/Post an authorisation funds-transfers.html`

### Post an authorisation funds-transfers

post

https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers/authorisation

Authorise a funds transfer instruction by validating the origination token that was delivered by an origination endpoint.



It caters for the origination tokens generated by all of the origination endpoints.





The authorisation of a fund-tranfer is essential performing a payment order acceptance. In order to get the detailed confirmation for each payment transfer one must have a webhook callback configured, please check How to manage Webhook configurations or alternatively envoke the Get a funds-transfers endpoint to get the latest detail.







API support message translations in Portuguese and English.



Pass the desired language code with Accept-Language on header or query parameter culture.





#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

paymentMethod

string

required

Match pattern:/^[A-Z]{5}_[{]?[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}[}]?$/gm

authorizationToken

string<uuid>

required

Delivered by origination endpoint

notify

object

debitorEmail

string<email>

creditorEmail

string<email>

sendDebitorProofOfTransactionEmail

boolean

sendCreditorProofOfTransactionEmail

boolean

#### Responses

202

Example response

##### Body

application/json

application/json

responses

/

202

id

string

responseStatus

object

successful

boolean

code

integer

message

string

source

string

authorizationDetails

object

sourceDetails

object

Auth

Token:

Parameters

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

Examples

{ "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044", "authorizationToken": "b2577735-50cb-44b9-b606-b71cccd33ea7", "notify": { "debitorEmail": "nzinga.mbandi@appy.co.ao", "creditorEmail": "nzinga.mbandi@appy.co.ao", "sendCreditorProofOfTransactionEmail": true, "sendDebitorProofOfTransactionEmail": true } }

```
1

{

2

  "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044",

3

  "authorizationToken": "b2577735-50cb-44b9-b606-b71cccd33ea7",

4

  "notify": {

5

    "debitorEmail": "nzinga.mbandi@appy.co.ao",

6

    "creditorEmail": "nzinga.mbandi@appy.co.ao",

7

    "sendCreditorProofOfTransactionEmail": true,

8

    "sendDebitorProofOfTransactionEmail": true

9

  }

10

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/funds-transfers/authorisation \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "paymentMethod": "paymentMethod_53c70da3-1c88-4391-8b60-ab4757fbb044",

  "authorizationToken": "b2577735-50cb-44b9-b606-b71cccd33ea7",

  "notify": {

    "debitorEmail": "nzinga.mbandi@appy.co.ao",

    "creditorEmail": "nzinga.mbandi@appy.co.ao",

    "sendCreditorProofOfTransactionEmail": true,

    "sendDebitorProofOfTransactionEmail": true

  }

}'

```

Response Example

```
1

{

2

  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",

3

  "responseStatus": {

4

    "successful": true,

5

    "code": 102,

6

    "message": "Payment order accepted for processing.",

7

    "source": "FTBAI",

8

    "sourceDetails": {

9

      "type": "NONE",

10

      "code": "NONE",

11

      "message": "Pendente"

12

    }

13

  }

14

}

```

---

## Post reference processing

**Arquivo de origem:** `APIS/AppyPay-API/Post reference processing.html`

### Post reference processing

post

https://gwy-api-tst.appypay.co.ao/{version}/mocks/referenceProcessing

This service allows to process a reference.

#### Request

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

paymentMethod

string

references

array[object]

referenceNumber

string

currency

string

amounts

array[object]

minAmount

integer

maxAmount

integer

startDate

string

expirationDate

string

nib

string

balance

integer

createdBy

string

#### Responses

202

OK

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

Examples

{ "paymentMethod": "", "references": [ { "referenceNumber": "", "currency": "AOA", "amounts": [ { "amount": 102, "descriptionLine1": "Test2.0 L1", "descriptionLine2": "Test2.0 L2" }, { "amount": 102.01, "descriptionLine1": "Test2.1 L1", "descriptionLine2": "Test2.1 L2" } ], "minAmount": 100, "maxAmount": 200, "startDate": "2024-03-01T22:18:14.651Z", "expirationDate": "2025-06-27T22:18:14.651Z" } ], "createdBy": "POSTMAN_Test" }

```
1

{

2

  "paymentMethod": "",

3

  "references": [

4

    {

5

      "referenceNumber": "",

6

      "currency": "AOA",

7

      "amounts": [

8

        {

9

          "amount": 102,

10

          "descriptionLine1": "Test2.0 L1",

11

          "descriptionLine2": "Test2.0 L2"

12

        },

13

        {

14

          "amount": 102.01,

15

          "descriptionLine1": "Test2.1 L1",

16

          "descriptionLine2": "Test2.1 L2"

17

        }

18

      ],

19

      "minAmount": 100,

20

      "maxAmount": 200,

21

      "startDate": "2024-03-01T22:18:14.651Z",

22

      "expirationDate": "2025-06-27T22:18:14.651Z"

23

    }

24

  ],

25

  "createdBy": "POSTMAN_Test"

26

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/mocks/referenceProcessing \

  --header 'Accept: ' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "paymentMethod": "",

  "references": [

    {

      "referenceNumber": "",

      "currency": "AOA",

      "amounts": [

        {

          "amount": 102,

          "descriptionLine1": "Test2.0 L1",

          "descriptionLine2": "Test2.0 L2"

        },

        {

          "amount": 102.01,

          "descriptionLine1": "Test2.1 L1",

          "descriptionLine2": "Test2.1 L2"

        }

      ],

      "minAmount": 100,

      "maxAmount": 200,

      "startDate": "2024-03-01T22:18:14.651Z",

      "expirationDate": "2025-06-27T22:18:14.651Z"

    }

  ],

  "createdBy": "POSTMAN_Test"

}'

```

---

## Post references

**Arquivo de origem:** `APIS/AppyPay-API/Post references.html`

### Post references

post

https://gwy-api-tst.appypay.co.ao/{version}/references

This service allows merchant support team to create references (one or multiple).





Maximun references for a request is 500. If more than 500 are requested then a HTTP 413 will be raised.





##### References Types



References can have:


- Fixed amount - when creating a reference pass the desired amounts in the amounts variable

- Free amount - when creating a reference pass minAmount and maxAmount


#### Request

Security: Bearer Auth

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Assertion

string

User-grant assertion

Content-Type

string

required

Describes the format the body of your request is being sent as

Allowed value:application/json

Example:application/json

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

paymentMethod

string

references

array[object]

referenceNumber

string

currency

string

amounts

array[object]

minAmount

integer

maxAmount

integer

startDate

string

expirationDate

string

nib

string

balance

integer

createdBy

string

#### Responses

202

Example response

##### Body

application/json

application/json

responses

/

202

references

array[object]

referenceNumber

string

>= 9 characters<= 15 characters

code

integer

message

string

Auth

Token:

Parameters

Content-Type*:application/json

application/json

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Assertion:

Body

Examples

{ "paymentMethod": "", "references": [ { "referenceNumber": "", "currency": "AOA", "amounts": [ { "amount": 102, "descriptionLine1": "Test2.0 L1", "descriptionLine2": "Test2.0 L2" }, { "amount": 102.01, "descriptionLine1": "Test2.1 L1", "descriptionLine2": "Test2.1 L2" } ], "minAmount": 100, "maxAmount": 200, "startDate": "2024-03-01T22:18:14.651Z", "expirationDate": "2025-06-27T22:18:14.651Z" } ], "createdBy": "POSTMAN_Test" }

```
1

{

2

  "paymentMethod": "",

3

  "references": [

4

    {

5

      "referenceNumber": "",

6

      "currency": "AOA",

7

      "amounts": [

8

        {

9

          "amount": 102,

10

          "descriptionLine1": "Test2.0 L1",

11

          "descriptionLine2": "Test2.0 L2"

12

        },

13

        {

14

          "amount": 102.01,

15

          "descriptionLine1": "Test2.1 L1",

16

          "descriptionLine2": "Test2.1 L2"

17

        }

18

      ],

19

      "minAmount": 100,

20

      "maxAmount": 200,

21

      "startDate": "2024-03-01T22:18:14.651Z",

22

      "expirationDate": "2025-06-27T22:18:14.651Z"

23

    }

24

  ],

25

  "createdBy": "POSTMAN_Test"

26

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/references \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Assertion: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "paymentMethod": "",

  "references": [

    {

      "referenceNumber": "",

      "currency": "AOA",

      "amounts": [

        {

          "amount": 102,

          "descriptionLine1": "Test2.0 L1",

          "descriptionLine2": "Test2.0 L2"

        },

        {

          "amount": 102.01,

          "descriptionLine1": "Test2.1 L1",

          "descriptionLine2": "Test2.1 L2"

        }

      ],

      "minAmount": 100,

      "maxAmount": 200,

      "startDate": "2024-03-01T22:18:14.651Z",

      "expirationDate": "2025-06-27T22:18:14.651Z"

    }

  ],

  "createdBy": "POSTMAN_Test"

}'

```

Response Example

```
1

{

2

  "references": [

3

    {

4

      "referenceNumber": "123456789",

5

      "code": 101,

6

      "message": "The request has been accepted for processing."

7

    }

8

  ]

9

}

```

---

## TaxPayerResponse

**Arquivo de origem:** `APIS/AppyPay-API/TaxPayerResponse.html`

### TaxPayerResponse

Export

Example

nif

string

required

Taxpayer Identification Number (NIF)

name

string

Taxpayer name

vatRegime

string

VAT regime

type

string

Allowed values:SINGULARCOLLECTIVE

status

string

required

Taxpayer status code:


- `A` - Ativo

- `C` - Cessado

- `D` - Falecido

- `E` - Herança

- `F` - Anulado

- `G` - Suspenso


Allowed values:ACDEFG

---

## TaxpayerStatus

**Arquivo de origem:** `APIS/AppyPay-API/TaxpayerStatus.html`

### TaxpayerStatus

Export

Example

string

Taxpayer status code:


- `A` - Ativo

- `C` - Cessado

- `D` - Falecido

- `E` - Herança

- `F` - Anulado

- `G` - Suspenso


Allowed values:ACDEFG

---

## TaxpayerType

**Arquivo de origem:** `APIS/AppyPay-API/TaxpayerType.html`

_Sem conteúdo textual extraído._

---

## Validate Fiscal Document

**Arquivo de origem:** `APIS/AppyPay-API/Validate Fiscal Document.html`

### Validate Fiscal Document

post

https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/{id}/validate

Submits an uploaded fiscal/electronic billing document for validation based on a specific verification process flow.

#### Request

Security: Bearer Auth

##### Path Parameters

id

string<uuid>

required

The unique Guid identifier of the fiscal document to be validated.

##### Headers

Accept-Language

string

Language preferences that is passed via HTTP when a document is requested

Allowed values:enpt-BR

Default:pt-BR

Example:pt-BR

Accept

string

Accept header is used by HTTP clients to tell the server which type of content they expect/prefer as response.

Allowed values:application/jsonapplication/vnd.appypay.asyncapi+json

Default:application/json

##### Body

application/json

application/json

merchantId

integer<int32>

required

Unique identifier mapping the core validation target reference context directly back to the executing or parent merchant identity reference structure.

action

string

required

Indica a acção que o adquirente pretende aplicar ao documento de facturação emitido. (C – Confirmação, R – Rejeição)

Allowed values:CR

deductibleVatPercentage

number<double> or null

The specific VAT percentage threshold metric designated as compliant or eligible for fiscal allocation deductions under operational region compliance parameters.

nonDeductibleAmount

number<double> or null

Baseline transaction amount mapping out financial values bound directly against standard tax calculations that are blocked from dynamic deductions.

#### Responses

202

Accepted - The document validation task has been queued and successfully pushed into background processing execution.

##### Body

application/json

application/json

responses

/

202

any

Accepted

Auth

Token:

Parameters

id*:

Accept:Not Setapplication/jsonapplication/vnd.appypay.asyncapi+json

select an option (defaults to: application/json)

Accept-Language:Not Setenpt-BR

select an option (defaults to: pt-BR)

Body

{ "merchantId": -2147483648, "action": "C", "deductibleVatPercentage": -1.7976931348623157e+308, "nonDeductibleAmount": -1.7976931348623157e+308 }

```
1

{

2

  "merchantId": -2147483648,

3

  "action": "C",

4

  "deductibleVatPercentage": -1.7976931348623157e+308,

5

  "nonDeductibleAmount": -1.7976931348623157e+308

6

}

```

Send API Request

TEST

Request Sample: Shell / cURL

```
curl --request POST \

  --url https://gwy-api-tst.appypay.co.ao/{version}/fiscal-documents/{id}/validate \

  --header 'Accept: application/json' \

  --header 'Accept-Language: ' \

  --header 'Authorization: Bearer 123' \

  --header 'Content-Type: application/json' \

  --data '{

  "merchantId": -2147483648,

  "action": "C",

  "deductibleVatPercentage": -1.7976931348623157e+308,

  "nonDeductibleAmount": -1.7976931348623157e+308

}'

```

---

## ValidateDocumentRequest

**Arquivo de origem:** `APIS/AppyPay-API/ValidateDocumentRequest.html`

### ValidateDocumentRequest

Export

Example

merchantId

integer<int32>

required

Unique identifier mapping the core validation target reference context directly back to the executing or parent merchant identity reference structure.

action

string

required

Indica a acção que o adquirente pretende aplicar ao documento de facturação emitido. (C – Confirmação, R – Rejeição)

Allowed values:CR

deductibleVatPercentage

number<double> or null

The specific VAT percentage threshold metric designated as compliant or eligible for fiscal allocation deductions under operational region compliance parameters.

nonDeductibleAmount

number<double> or null

Baseline transaction amount mapping out financial values bound directly against standard tax calculations that are blocked from dynamic deductions.

---
