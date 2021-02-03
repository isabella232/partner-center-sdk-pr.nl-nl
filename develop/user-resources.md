---
title: Gebruikers resources
description: Hierin wordt een afzonderlijke partner Center-gebruiker, hun persoonlijke gegevens en account informatie en de machtigingen die ze hebben in het partner centrum beschreven.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0c88b9b65dfb925712ff85fb42d34251cca6e0b5
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767164"
---
# <a name="user-resources"></a>Gebruikers resources

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hierin wordt een afzonderlijke partner Center-gebruiker, hun persoonlijke gegevens en account informatie en de machtigingen die ze hebben in het partner centrum beschreven.

## <a name="user"></a>Gebruiker

Beschrijft een afzonderlijke gebruiker.

| Eigenschap              | Type                                                           | Beschrijving                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks                                                         | De gebruikers-id.                                                                                                                                                                                                       |
| userPrincipalName     | tekenreeks                                                         | De principal-id van de gebruiker.                                                                                                                                                                                             |
| voornaam             | tekenreeks                                                         | De voor naam van de gebruiker.                                                                                                                                                                                                |
| achternaam              | tekenreeks                                                         | De achternaam van de gebruiker.                                                                                                                                                                                                 |
| displayName           | tekenreeks                                                         | De weer gegeven naam van de gebruiker.                                                                                                                                                                                            |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | Het wachtwoord Profiel van de gebruiker.                                                                                                                                                                                               |
| phoneNumber           | tekenreeks                                                         | Het telefoon nummer van de gebruiker.                                                                                                                                                                                                   |
| lastDirectorySyncTime | teken reeks in UTC-datum tijd notatie                                 | De laatste keer dat de gegevens voor deze gebruiker zijn gesynchroniseerd tussen Azure Active Directory en on-premises Active Directory. Een waarde voor datum en tijd wordt alleen weer gegeven als Azure AD Connect synchronisatie is ingeschakeld. Anders is de waarde Null. |
| userDomainType        | tekenreeks                                                         | Het gebruikers domein type: ' none ', ' managed ' of ' Federated '.                                                                                                                                                                   |
| staat                 | tekenreeks                                                         | De status van de gebruiker: ' Active ', ' inactive ' (voor een verwijderde gebruiker).                                                                                                                                                          |
| softDeletionTime      | teken reeks in UTC-datum tijd notatie                                 | Vertegenwoordigt het begin van de periode van dertig dagen waarna de gegevens die zijn gekoppeld aan een verwijderde gebruiker permanent worden verwijderd en daarom niet kan worden hersteld.                                                                          |
| koppelen                 | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen.                                                                                                                                                                                                        |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                                                                                                                                                                                   |

## <a name="customeruser"></a>CustomerUser

Beschrijft een klant gebruiker.

| Eigenschap              | Type                                                           | Description                                                                                                                                                                                                                |
|-----------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageLocation         | tekenreeks                                                         | De locatie waar de gebruiker de licentie wil gebruiken.                                                                                                                                                                    |
| id                    | tekenreeks                                                         | De gebruikers-id.                                                                                                                                                                                                       |
| userPrincipalName     | tekenreeks                                                         | De principal-id van de gebruiker.                                                                                                                                                                                             |
| voornaam             | tekenreeks                                                         | De voor naam van de gebruiker.                                                                                                                                                                                                |
| achternaam              | tekenreeks                                                         | De achternaam van de gebruiker.                                                                                                                                                                                                 |
| displayName           | tekenreeks                                                         | De weer gegeven naam van de gebruiker.                                                                                                                                                                                            |
| immutableId           | tekenreeks                                                         | De onveranderbare id van de gebruiker.                                                                                                                                                                                              |
| passwordProfile       | [PasswordProfile](utility-resources.md#passwordprofile)       | Het wachtwoord Profiel van de gebruiker.                                                                                                                                                                                               |
| phoneNumber           | tekenreeks                                                         | Het telefoon nummer van de gebruiker.                                                                                                                                                                                                   |
| lastDirectorySyncTime | teken reeks in UTC-datum tijd notatie                                 | De laatste keer dat de gegevens voor deze gebruiker zijn gesynchroniseerd tussen Azure Active Directory en on-premises Active Directory. Een waarde voor datum en tijd wordt alleen weer gegeven als Azure AD Connect synchronisatie is ingeschakeld. Anders is de waarde Null. |
| userDomainType        | tekenreeks                                                         | Het gebruikers domein type: ' none ', ' managed ' of ' Federated '.                                                                                                                                                                   |
| staat                 | tekenreeks                                                         | De status van de gebruiker: ' Active ', ' inactive ' (voor een verwijderde gebruiker).                                                                                                                                                          |
| softDeletionTime      | teken reeks in UTC-datum tijd notatie                                 | Vertegenwoordigt het begin van de periode van dertig dagen waarna de gegevens die zijn gekoppeld aan een verwijderde gebruiker permanent worden verwijderd en daarom niet kan worden hersteld.                                                                          |
| koppelen                 | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen.                                                                                                                                                                                                        |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                                                                                                                                                                                   |

## <a name="usercredentials"></a>UserCredentials

Beschrijft de aanmeldings referenties van een gebruiker.

| Eigenschap | Type                                               | Description                          |
|----------|----------------------------------------------------|--------------------------------------|
| userName | tekenreeks                                             | De naam van de gebruiker.                |
| wachtwoord | [SecureString](utility-resources.md#securestring) | Het veilig opgeslagen wacht woord van de gebruiker. |

## <a name="usermember"></a>UserMember

Beschrijft de gebruikers gegevens van een gebruiker.

| Eigenschap          | Type                                                           | Description                        |
|-------------------|----------------------------------------------------------------|------------------------------------|
| displayName       | tekenreeks                                                         | De weer gegeven naam voor de gebruiker.   |
| userPrincipalName | tekenreeks                                                         | De naam van de gebruikers-principal.    |
| roleId            | tekenreeks                                                         | De id van de rol van de gebruiker. |
| id                | tekenreeks                                                         | De id van het lid.      |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.           |

