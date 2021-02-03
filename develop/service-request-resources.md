---
title: Resources van service aanvraag
description: Partners kunnen service aanvragen namens hun partners indienen om verstoringen van de door micro soft geleverde services te melden of om andere technische ondersteuning te vragen die ze niet kunnen leveren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 072f9eddaf9d854f1dcc8cc65f7928b6c95700fa
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767236"
---
# <a name="service-request-resources"></a>Resources van service aanvraag

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Partners kunnen service aanvragen namens hun partners indienen om verstoringen van de door micro soft geleverde services te melden of om andere technische ondersteuning te vragen die ze niet kunnen leveren.

## <a name="servicerequest"></a>ServiceRequest

Beschrijft een service aanvraag die is ingediend door een partner, met inbegrip van de voortgang van de aanvraag.

| Eigenschap         | Type                                                          | Description                                                                          |
|------------------|---------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Titel            | tekenreeks                                                        | De titel van de service aanvraag.                                                           |
| Description      | tekenreeks                                                        | De beschrijving.                                                                     |
| Severity         | tekenreeks                                                        | De ernst: "onbekend", "kritiek", "gemiddeld" of "mini maal".                       |
| SupportTopicId   | tekenreeks                                                        | De id van het ondersteunings onderwerp.                                                         |
| SupportTopicName | tekenreeks                                                        | De naam van het ondersteunings onderwerp.                                                       |
| Id               | tekenreeks                                                        | De id van de service aanvraag.                                                       |
| Status           | tekenreeks                                                        | De status van de service aanvraag: ' geen ', ' openen ', ' gesloten ' of ' aandacht \_ vereist '. |
| Organisatie     | [ServiceRequestOrganization](#servicerequestorganization)     | De organisatie waarvoor de service aanvraag is gemaakt.                               |
| PrimaryContact   | [ServiceRequestContact](#servicerequestcontact)               | Primaire contact persoon op de service aanvraag.                                              |
| LastUpdatedBy    | [ServiceRequestContact](#servicerequestcontact)               | De contact persoon ' laatst bijgewerkt door ' voor wijzigingen in de service aanvraag.                        |
| ProductName      | tekenreeks                                                        | De naam van het product dat overeenkomt met de service aanvraag.                     |
| ProductId        | tekenreeks                                                        | De id van het product.                                                               |
| CreatedDate      | date                                                          | De datum waarop de service aanvraag is gemaakt.                                          |
| LastModifiedDate | date                                                          | De datum waarop de service aanvraag voor het laatst is gewijzigd.                                 |
| LastClosedDate   | date                                                          | De datum waarop de service aanvraag voor het laatst is gesloten.                                   |
| FileLinks        | matrix van [file info](utility-resources.md#fileinfo) -resources | De verzameling bestands koppelingen die betrekking hebben op de service aanvraag.                    |
| NewNote          | [ServiceRequestNote](#servicerequestnote)                     | Een notitie kan worden toegevoegd aan een bestaande service aanvraag.                                  |
| Notities            | matrix van [ServiceRequestNotes](#servicerequestnote)           | Een verzameling notities die worden toegevoegd aan de service aanvraag.                                  |
| CountryCode      | tekenreeks                                                        | Het land dat overeenkomt met de service aanvraag.                                    |
| Kenmerken       | ResourceAttributes                                            | De meta gegevens kenmerken die overeenkomen met de service aanvraag.                        |

## <a name="servicerequestcontact"></a>ServiceRequestContact

Beschrijft een contact persoon die een service aanvraag maakt of wijzigt.

| Eigenschap     | Type                                                      | Description                                            |
|--------------|-----------------------------------------------------------|--------------------------------------------------------|
| Organisatie | [ServiceRequestOrganization](#servicerequestorganization) | De organisatie waarvoor de service aanvraag is gemaakt. |
| ContactId    | tekenreeks                                                    | De unieke id van de contact persoon.                               |
| LastName     | tekenreeks                                                    | De achternaam van de contact persoon.                          |
| FirstName    | tekenreeks                                                    | De voor naam van de contact persoon.                         |
| E-mail        | tekenreeks                                                    | Het e-mail adres van de contact persoon.                              |
| PhoneNumber  | tekenreeks                                                    | Het telefoon nummer van de contact persoon.                       |

## <a name="servicerequestnote"></a>ServiceRequestNote

Hierin wordt een notitie beschreven die is gekoppeld aan een service aanvraag.

| Eigenschap      | Type   | Description                                  |
|---------------|--------|----------------------------------------------|
| CreatedByName | tekenreeks | De naam van de maker van de notitie.         |
| CreatedDate   | date   | De datum en tijd waarop de notitie is gemaakt. |
| Tekst          | tekenreeks | De tekst van de notitie.                        |

## <a name="servicerequestorganization"></a>ServiceRequestOrganization

Hierin wordt de organisatie beschreven waarvoor de service aanvraag is gemaakt.

| Eigenschap    | Type   | Description                           |
|-------------|--------|---------------------------------------|
| Id          | tekenreeks | De unieke id van de organisatie.    |
| Name        | tekenreeks | De naam van de organisatie.         |
| PhoneNumber | tekenreeks | Het telefoon nummer van de organisatie. |

## <a name="supporttopic"></a>SupportTopic

Hierin wordt een ondersteunings onderwerp beschreven. Service aanvragen geven een ondersteunings onderwerp op om ervoor te zorgen dat ze snel en effectief worden verwerkt.

| Eigenschap    | Type               | Beschrijving                                                   |
|-------------|--------------------|---------------------------------------------------------------|
| Name        | tekenreeks             | De naam van het ondersteunings onderwerp.                                |
| Description | tekenreeks             | De beschrijving van het ondersteunings onderwerp.                         |
| Id          | tekenreeks             | De unieke id van het ondersteunings onderwerp.                           |
| Kenmerken  | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de service aanvraag. |

