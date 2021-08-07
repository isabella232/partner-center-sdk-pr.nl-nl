---
title: Gebruikersbronnen
description: Beschrijft een afzonderlijke Partner Center gebruiker, hun persoonlijke gegevens en accountgegevens en de machtigingen die ze hebben binnen Partner Center.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c91e3509d86c8817da30c8ad0d96a2b1b6eec7697e43b47d3dfb96055cac632
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989216"
---
# <a name="user-resources"></a>Gebruikersbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beschrijft een afzonderlijke Partner Center gebruiker, hun persoonlijke gegevens en accountgegevens en de machtigingen die ze hebben binnen Partner Center.

## <a name="user"></a>Gebruiker

Beschrijft een afzonderlijke gebruiker.

| Eigenschap              | Type                                                           | Beschrijving                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks                                                         | De gebruikers-id.                                                                                                                                                                                                       |
| userPrincipalName     | tekenreeks                                                         | De principal-id van de gebruiker.                                                                                                                                                                                             |
| voornaam             | tekenreeks                                                         | De voornaam van de gebruiker.                                                                                                                                                                                                |
| achternaam              | tekenreeks                                                         | De achternaam van de gebruiker.                                                                                                                                                                                                 |
| displayName           | tekenreeks                                                         | De weergegeven naam van de gebruiker.                                                                                                                                                                                            |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | Het wachtwoordprofiel van de gebruiker.                                                                                                                                                                                               |
| phoneNumber           | tekenreeks                                                         | Het telefoonnummer van de gebruiker.                                                                                                                                                                                                   |
| lastDirectorySyncTime | tekenreeks in UTC-datum/tijd-indeling                                 | De laatste keer dat de gegevens voor deze gebruiker zijn gesynchroniseerd tussen Azure Active Directory en on-premises Active Directory. Een datum/tijd-waarde wordt alleen weergegeven als Azure AD Verbinding maken synchronisatie is ingeschakeld. Anders is de waarde null. |
| userDomainType        | tekenreeks                                                         | Het domeintype van de gebruiker: 'none', 'managed' of 'federated'.                                                                                                                                                                   |
| staat                 | tekenreeks                                                         | De status van de gebruiker: 'actief', 'inactief' (voor een verwijderde gebruiker).                                                                                                                                                          |
| softDeletionTime      | tekenreeks in UTC-datum/tijd-indeling                                 | Vertegenwoordigt het begin van de periode van 30 dagen waarna gegevens die zijn gekoppeld aan een verwijderde gebruiker permanent worden verwijderd en daarom onherkenbaar zijn.                                                                          |
| Verwijzigingen                 | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen.                                                                                                                                                                                                        |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                                                                                                                                                                   |

## <a name="customeruser"></a>CustomerUser

Beschrijft een klantgebruiker.

| Eigenschap              | Type                                                           | Description                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageLocation         | tekenreeks                                                         | De locatie waar de gebruiker de licentie wil gebruiken.                                                                                                                                                                    |
| id                    | tekenreeks                                                         | De gebruikers-id.                                                                                                                                                                                                       |
| userPrincipalName     | tekenreeks                                                         | De principal-id van de gebruiker.                                                                                                                                                                                             |
| voornaam             | tekenreeks                                                         | De voornaam van de gebruiker.                                                                                                                                                                                                |
| achternaam              | tekenreeks                                                         | De achternaam van de gebruiker.                                                                                                                                                                                                 |
| displayName           | tekenreeks                                                         | De weergegeven naam van de gebruiker.                                                                                                                                                                                            |
| onveranderbareid           | tekenreeks                                                         | De onveranderbare id van de gebruiker.                                                                                                                                                                                              |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | Het wachtwoordprofiel van de gebruiker.                                                                                                                                                                                               |
| phoneNumber           | tekenreeks                                                         | Het telefoonnummer van de gebruiker.                                                                                                                                                                                                   |
| lastDirectorySyncTime | tekenreeks in UTC-datum/tijd-indeling                                 | De laatste keer dat de gegevens voor deze gebruiker zijn gesynchroniseerd tussen Azure Active Directory en on-premises Active Directory. Een datum/tijd-waarde wordt alleen weergegeven als Azure AD Verbinding maken synchronisatie is ingeschakeld. Anders is de waarde null. |
| userDomainType        | tekenreeks                                                         | Het domeintype van de gebruiker: 'none', 'managed' of 'federated'.                                                                                                                                                                   |
| staat                 | tekenreeks                                                         | De status van de gebruiker: 'actief', 'inactief' (voor een verwijderde gebruiker).                                                                                                                                                          |
| softDeletionTime      | tekenreeks in UTC-datum/tijd-indeling                                 | Vertegenwoordigt het begin van de periode van 30 dagen waarna gegevens die zijn gekoppeld aan een verwijderde gebruiker permanent worden verwijderd en daarom onherkenbaar zijn.                                                                          |
| Verwijzigingen                 | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen.                                                                                                                                                                                                        |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                                                                                                                                                                   |

## <a name="usercredentials"></a>UserCredentials

Beschrijft de aanmeldingsreferenties van een gebruiker.

| Eigenschap | Type                                               | Description                          |
|----------|----------------------------------------------------|--------------------------------------|
| userName | tekenreeks                                             | De naam van de gebruiker.                |
| wachtwoord | [SecureString](utility-resources.md#securestring) | Het veilig opgeslagen wachtwoord van de gebruiker. |

## <a name="usermember"></a>UserMember

Beschrijft de lidgegevens van een gebruiker.

| Eigenschap          | Type                                                           | Description                        |
|-------------------|----------------------------------------------------------------|------------------------------------|
| displayName       | tekenreeks                                                         | De weergegeven naam voor de gebruiker.   |
| userPrincipalName | tekenreeks                                                         | De naam van de user principal.    |
| roleId            | tekenreeks                                                         | De id van de rol van de gebruiker. |
| id                | tekenreeks                                                         | De id van het lid.      |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.           |

