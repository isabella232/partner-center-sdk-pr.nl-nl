---
title: TransferEntity-resources
description: Een partner maakt een overdracht wanneer een klant wil dat het abonnement met de partner wordt overgedragen aan een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 544b9682bb0e1428fad088c818a62492198897b2
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530137"
---
# <a name="transferentity-resources"></a>TransferEntity-resources

Een partner maakt een overdracht wanneer een klant wil dat het abonnement met de partner wordt overgedragen aan een andere partner.

## <a name="transferentity"></a>TransferEntity

Beschrijft een transferEntity.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een transferEntity-id die wordt opgegeven wanneer de transferEntity is gemaakt.                               |
| createdTime           | DateTime         | De datum waarop de transferEntity is gemaakt, in datum/tijd-indeling. Toegepast wanneer de transferEntity is gemaakt.      |
| lastModifiedTime      | DateTime         | De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de transferEntity is gemaakt. |
| lastModifiedUser      | tekenreeks           | De gebruiker die voor het laatst de transferEntity heeft bijgewerkt. Toegepast bij het maken van transferEntity.                          |
| customerName          | tekenreeks           | Optioneel. De naam van de klant van wie de abonnementen worden overgedragen.                                              |
| customerTenantId      | tekenreeks           | Een met GUID opgemaakte klant-id die de klant identificeert. Toegepast wanneer de transferEntity is gemaakt.         |
| partnertenantid       | tekenreeks           | Een partner-id met GUID-indeling die de partner identificeert.                                                                   |
| sourcePartnerName     | tekenreeks           | Optioneel. De naam van de organisatie van de partner die de overdracht start.                                           |
| sourcePartnerTenantId | tekenreeks           | Een partner-id met GUID-indeling die de partner identificeert die de overdracht start.                                           |
| targetPartnerName     | tekenreeks           | Optioneel. De naam van de organisatie van de partner waarop de overdracht is gericht.                                         |
| targetPartnerTenantId | tekenreeks           | Een partner-id met GUID-indeling die de partner identificeert waarop de overdracht is gericht.                                  |
| lineItems             | Matrix met objecten | Een matrix van [TransferLineItem-resources.](#transferlineitem)                                                   |
| status                | tekenreeks           | De status van de transferEntity. Mogelijke waarden zijn 'Actief' (kan worden verwijderd/verzonden) en 'Voltooid' (is al voltooid). Toegepast wanneer de transferEntity is gemaakt.|

## <a name="transferlineitem"></a>TransferLineItem

Vertegenwoordigt één item in een transferEntity.

| Eigenschap             | Type                             | Beschrijving                                                                                             |
|----------------------|----------------------------------|---------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een overdrachtsregelitem. Toegepast wanneer de transferEntity is gemaakt.   |
| subscriptionId       | tekenreeks                           | De abonnements-id.                                                                            |
| quantity             | int                              | Het aantal licenties of exemplaren.                                                                    |
| billingCycle         | Object                           | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                   |
| Friendlyname         | tekenreeks                           | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                   |
| partnerIdOnRecord    | tekenreeks                           | PartnerId on Record (MPNID) voor de aankoop die wordt gedaan wanneer de overdracht wordt geaccepteerd.                 |
| offerId              | tekenreeks                           | De aanbiedings-id.    |
| addonItems           | Lijst met **TransferLineItem-objecten** | Een verzameling transferEntity-regelitems voor addons die samen met het basisabonnement dat wordt overgedragen, worden overgedragen. Toegepast wanneer de transferEntity is gemaakt.|
| transferError        | tekenreeks                           | Toegepast nadat transferEntity is geaccepteerd in het geval van een fout.                |
| status               | tekenreeks           | De status van het regelitem in de transferEntity.|

## <a name="transfersubmitresult"></a>TransferSubmitResult

Vertegenwoordigt het resultaat van een overdracht accepteren.

| Eigenschap          | Type                                                  | Beschrijving                        |
|-------------------|-------------------------------------------------------|------------------------------------|
| orders            | Lijst met [orderobjecten.](order-resources.md#order)    | De verzameling orders.          |
| transferErrors    | Lijst met [TransferError-objecten.](#transfererror)      | De verzameling overdrachtsfouten. |

## <a name="transfererror"></a>TransferError

Vertegenwoordigt een fout die optreedt wanneer een overdracht wordt geaccepteerd.

| Eigenschap          | Type   | Beschrijving                                     |
|-------------------|--------|-------------------------------------------------|
| transferGroupId   | tekenreeks | De ordergroep-id van de bestelling met de fout. |
| code              | int    | De foutcode.                                 |
| beschrijving       | tekenreeks | De beschrijving van de fout.                   |
| lineItems         | Lijst met **TransferLineItem-objecten** | Een verzameling regelitems voor transferEntity die deel uitmaken van de overdrachtsfout.|

## <a name="transfererrorcode"></a>TransferErrorCode

Een [Enum/dotnet/api/system.enum) met waarden die een type volgordefout aangeven.

| Waarde | Positie | Beschrijving |
| --- | --- | --- |
| PartnerTokenMissing | 800001 | Partner-token ontbreekt in aanvraagcontext. |
| InvalidInput | 800002 | Ongeldige aanvraaginvoer. |
| ServiceException | 800003 | Onverwachte servicefout. |
| InvalidOfferId | 800004 | Ongeldige aanbiedings-id. |
| CreateOrderError | 800005 | Het maken van een order is niet gelukt. |
| MpnIdNotFound | 800015 | DE MPN-id is niet gevonden. |
| NotValidIndirectResellerMpnId | 800016 | MPN-id is geen geldige indirecte reseller. |
| TransferIdNotFound | 900100   | Overdrachtsaanvraag niet gevonden.   |
| TransferNotAllowedIfStatusIsInProgress | 900101 | De overdrachtsaanvraag wordt al uitgevoerd.|
| TransferNotAllowedIfStatusIsCompleted | 900102 | De overdrachtsaanvraag is al voltooid.|
| TransferCreateOrderError | 900103 | De overdrachtsorder is niet gelukt.|
| TransferProcessedByAnotherRequest | 900104 | De overdracht wordt verwerkt door een andere aanvraag.|