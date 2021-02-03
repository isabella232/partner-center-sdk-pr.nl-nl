---
title: TransferEntity-resources
description: Een partner maakt een overdracht wanneer een klant zijn abonnement met de partner wil overzetten naar een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 96c43d255fcd31e6dc4de50baa0e19f5d8855685
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767334"
---
# <a name="transferentity-resources"></a>TransferEntity-resources

**Van toepassing op:**

- Partnercentrum

Een partner maakt een overdracht wanneer een klant zijn abonnement met de partner wil overzetten naar een andere partner.

## <a name="transferentity"></a>TransferEntity

Hierin wordt een transferEntity beschreven.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een transferEntity-id die wordt geleverd bij het maken van de transferEntity.                               |
| createdTime           | DateTime         | De datum waarop de transferEntity is gemaakt, in datum-tijd notatie. Wordt toegepast wanneer de transferEntity is gemaakt.      |
| lastModifiedTime      | DateTime         | De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum-tijd notatie. Wordt toegepast wanneer de transferEntity is gemaakt. |
| lastModifiedUser      | tekenreeks           | De gebruiker die de transferEntity voor het laatst heeft bijgewerkt. Toegepast bij het maken van transferEntity.                          |
| customerName          | tekenreeks           | Optioneel. De naam van de klant wiens abonnementen worden overgedragen.                                              |
| customerTenantId      | tekenreeks           | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd. Wordt toegepast wanneer de transferEntity is gemaakt.         |
| partnertenantid       | tekenreeks           | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd.                                                                   |
| sourcePartnerName     | tekenreeks           | Optioneel. De naam van de organisatie van de partner die de overdracht initieert.                                           |
| sourcePartnerTenantId | tekenreeks           | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd die de overdracht initieert.                                           |
| targetPartnerName     | tekenreeks           | Optioneel. De naam van de organisatie van de partner waarop de overdracht is gericht.                                         |
| targetPartnerTenantId | tekenreeks           | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd voor wie de overdracht is gericht.                                  |
| Regel items             | Matrix van objecten | Een matrix met [TransferLineItem](#transferlineitem) -resources.                                                   |
| status                | tekenreeks           | De status van de transferEntity. Mogelijke waarden zijn ' Active ' (kunnen worden verwijderd/verzonden) en ' voltooid ' (is al voltooid). Wordt toegepast wanneer de transferEntity is gemaakt.|

## <a name="transferlineitem"></a>TransferLineItem

Vertegenwoordigt één item in een transferEntity.

| Eigenschap             | Type                             | Beschrijving                                                                                             |
|----------------------|----------------------------------|---------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een regel item voor de overdracht. Wordt toegepast wanneer de transferEntity is gemaakt.   |
| subscriptionId       | tekenreeks                           | De abonnements-id.                                                                            |
| quantity             | int                              | Het aantal licenties of exemplaren.                                                                    |
| billingCycle         | Object                           | Het type facturerings cyclus dat voor de huidige periode is ingesteld.                                                   |
| friendlyName         | tekenreeks                           | Optioneel. De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                   |
| partnerIdOnRecord    | tekenreeks                           | Partner on record (MPNID) voor de aankoop die plaatsvindt wanneer de overdracht wordt geaccepteerd.                 |
| offerId              | tekenreeks                           | De aanbiedings-id.    |
| addonItems           | Lijst met **TransferLineItem** -objecten | Een verzameling transferEntity-regel items voor addons die worden overgedragen samen met het basis abonnement dat wordt overgedragen. Wordt toegepast wanneer de transferEntity is gemaakt.|
| transferError        | tekenreeks                           | Wordt toegepast nadat transferEntity is geaccepteerd in het geval van een fout.                |
| status               | tekenreeks           | De status van de lineitem in de transferEntity.|

## <a name="transfersubmitresult"></a>TransferSubmitResult

Hiermee wordt het resultaat van een overdracht geaccepteerd aangegeven.

| Eigenschap          | Type                                                  | Description                        |
|-------------------|-------------------------------------------------------|------------------------------------|
| orders            | Lijst met [order](order-resources.md#order) objecten.    | De verzameling orders.          |
| transferErrors    | Lijst met [TransferError](#transfererror) -objecten.      | De verzameling van overdrachts fouten. |

## <a name="transfererror"></a>TransferError

Hiermee wordt een fout aangeduid die zich voordoet wanneer een overdracht wordt geaccepteerd.

| Eigenschap          | Type   | Description                                     |
|-------------------|--------|-------------------------------------------------|
| transferGroupId   | tekenreeks | De order groep-ID van de order met de fout. |
| code              | int    | De fout code.                                 |
| beschrijving       | tekenreeks | De beschrijving van de fout.                   |
| Regel items         | Lijst met **TransferLineItem** -objecten | Een verzameling transferEntity-regel items die deel uitmaken van de overdrachts fout.|

## <a name="transfererrorcode"></a>TransferErrorCode

Een [Enum/DotNet/API/System. enum) met waarden die een type bestel fout aangeven.

| Waarde | Positie | Description |
| --- | --- | --- |
| PartnerTokenMissing | 800001 | Het partner token ontbreekt in de context van de aanvraag. |
| InvalidInput | 800002 | Ongeldige invoer van aanvraag. |
| ServiceException | 800003 | Onverwachte service fout. |
| InvalidOfferId | 800004 | Ongeldige aanbiedings-ID. |
| CreateOrderError | 800005 | De order voor het maken is niet voltooid. |
| MpnIdNotFound | 800015 | De MPN-id is niet gevonden. |
| NotValidIndirectResellerMpnId | 800016 | De MPN-id is geen geldige indirecte wederverkoper. |
| TransferIdNotFound | 900100   | De overdrachts aanvraag is niet gevonden.   |
| TransferNotAllowedIfStatusIsInProgress | 900101 | De overdrachts aanvraag wordt al uitgevoerd.|
| TransferNotAllowedIfStatusIsCompleted | 900102 | De overdrachts aanvraag is al voltooid.|
| TransferCreateOrderError | 900103 | De overdrachts order is niet geslaagd.|
| TransferProcessedByAnotherRequest | 900104 | De overdracht wordt verwerkt door een andere aanvraag.|