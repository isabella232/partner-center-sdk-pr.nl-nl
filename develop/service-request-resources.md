---
title: Resources voor serviceaanvraag
description: Partners kunnen serviceaanvragen indienen namens hun partners om onderbrekingsservices te melden die worden geleverd door Microsoft of om andere technische ondersteuning aan te vragen die ze niet kunnen bieden.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f919b3c34ff179a7a6cd0541f34c53737ec4148e44791419d2252fae64b0658d
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993228"
---
# <a name="service-request-resources"></a>Resources voor serviceaanvraag

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Partners kunnen serviceaanvragen indienen namens hun partners om onderbrekingsservices te melden die worden geleverd door Microsoft of om andere technische ondersteuning aan te vragen die ze niet kunnen bieden.

## <a name="servicerequest"></a>ServiceRequest

Beschrijft een serviceaanvraag die is ingediend door een partner, inclusief de voortgang van die aanvraag.

| Eigenschap         | Type                                                          | Description                                                                          |
|------------------|---------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Titel            | tekenreeks                                                        | De titel van de serviceaanvraag.                                                           |
| Description      | tekenreeks                                                        | De beschrijving.                                                                     |
| Ernst         | tekenreeks                                                        | De ernst: 'onbekend', 'kritiek', 'gemiddeld' of 'minimaal'.                       |
| SupportTopicId   | tekenreeks                                                        | De id van het ondersteuningsonderwerp.                                                         |
| SupportTopicName | tekenreeks                                                        | De naam van het ondersteuningsonderwerp.                                                       |
| Id               | tekenreeks                                                        | De id van de serviceaanvraag.                                                       |
| Status           | tekenreeks                                                        | De status van de serviceaanvraag: 'none', 'open', 'closed' of 'attention \_ needed'. |
| Organisatie     | [ServiceRequestOrganization](#servicerequestorganization)     | Organisatie waarvoor de serviceaanvraag is gemaakt.                               |
| PrimaryContact   | [ServiceRequestContact](#servicerequestcontact)               | Primaire contactpersoon voor de serviceaanvraag.                                              |
| LastUpdatedBy    | [ServiceRequestContact](#servicerequestcontact)               | Contactpersoon laatst bijgewerkt door voor wijzigingen in de serviceaanvraag.                        |
| ProductName      | tekenreeks                                                        | De naam van het product dat overeenkomt met de serviceaanvraag.                     |
| ProductId        | tekenreeks                                                        | De id van het product.                                                               |
| CreatedDate      | date                                                          | De datum waarop de serviceaanvraag is gemaakt.                                          |
| LastModifiedDate | date                                                          | De datum waarop de serviceaanvraag voor het laatst is gewijzigd.                                 |
| LastClosedDate   | date                                                          | De datum waarop de serviceaanvraag voor het laatst is gesloten.                                   |
| FileLinks        | matrix van [FileInfo-resources](utility-resources.md#fileinfo) | De verzameling bestandskoppelingen die betrekking hebben op de serviceaanvraag.                    |
| NewNote          | [ServiceRequestNote](#servicerequestnote)                     | Een opmerking kan worden toegevoegd aan een bestaande serviceaanvraag.                                  |
| Notities            | matrix van [ServiceRequestNotes](#servicerequestnote)           | Een verzameling notities toegevoegd aan de serviceaanvraag.                                  |
| CountryCode      | tekenreeks                                                        | Het land dat overeenkomt met de serviceaanvraag.                                    |
| Kenmerken       | ResourceAttributes                                            | De metagegevenskenmerken die overeenkomen met de serviceaanvraag.                        |

## <a name="servicerequestcontact"></a>ServiceRequestContact

Beschrijft een contactpersoon die een serviceaanvraag maakt of wijzigt.

| Eigenschap     | Type                                                      | Description                                            |
|--------------|-----------------------------------------------------------|--------------------------------------------------------|
| Organisatie | [ServiceRequestOrganization](#servicerequestorganization) | Organisatie waarvoor de serviceaanvraag is gemaakt. |
| ContactId    | tekenreeks                                                    | De unieke id van de contactpersoon.                               |
| LastName     | tekenreeks                                                    | De achternaam van de contactpersoon.                          |
| FirstName    | tekenreeks                                                    | De voornaam van de contactpersoon.                         |
| E-mail        | tekenreeks                                                    | Het e-mailadres van de contactpersoon.                              |
| PhoneNumber  | tekenreeks                                                    | Het telefoonnummer van de contactpersoon.                       |

## <a name="servicerequestnote"></a>ServiceRequestNote

Beschrijft een opmerking die is gekoppeld aan een serviceaanvraag.

| Eigenschap      | Type   | Description                                  |
|---------------|--------|----------------------------------------------|
| CreatedByName | tekenreeks | De naam van de maker van de opmerking.         |
| CreatedDate   | date   | De datum en tijd waarop de notitie is gemaakt. |
| Tekst          | tekenreeks | De tekst van de opmerking.                        |

## <a name="servicerequestorganization"></a>ServiceRequestOrganization

Beschrijft de organisatie waarvoor de serviceaanvraag is gemaakt.

| Eigenschap    | Type   | Description                           |
|-------------|--------|---------------------------------------|
| Id          | tekenreeks | De unieke id van de organisatie.    |
| Name        | tekenreeks | De naam van de organisatie.         |
| PhoneNumber | tekenreeks | Het telefoonnummer van de organisatie. |

## <a name="supporttopic"></a>SupportTopic

Beschrijft een ondersteuningsonderwerp. Serviceaanvragen geven een ondersteuningsonderwerp op om ervoor te zorgen dat ze snel en effectief worden verwerkt.

| Eigenschap    | Type               | Beschrijving                                                   |
|-------------|--------------------|---------------------------------------------------------------|
| Name        | tekenreeks             | De naam van het ondersteuningsonderwerp.                                |
| Description | tekenreeks             | De beschrijving van het ondersteuningsonderwerp.                         |
| Id          | tekenreeks             | De unieke id van het ondersteuningsonderwerp.                           |
| Kenmerken  | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de serviceaanvraag. |

