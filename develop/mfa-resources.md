---
title: Resources voor beveiligingsvereisten van partners
description: Meer informatie over de acceptatie van Meervoudige verificatie (MFA) om te voldoen aan de beveiligingsvereisten van de partner.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: b41a0e46fa6e0643e82a5a2dbfb7141f54a0f824
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445541"
---
# <a name="partner-security-requirements-resources"></a>Resources voor beveiligingsvereisten van partners

Dit artikel helpt u inzicht te krijgen in de ingebruikname van Meervoudige verificatie (MFA) om uw organisatie te helpen voldoen aan de status van de beveiligingsvereiste van de partner. 

## <a name="portal-request-without-mfa"></a>Portalaanvraag zonder MFA

Geef een gebruiker aan die toegang heeft tot Partner Center portal zonder MFA-verificatie.

| Eigenschap                            | Type            | Beschrijving                           |
|-------------------------------------|-----------------|---------------------------------------|
| ObjectId                            | tekenreeks          | Gebruikersobject-id                        |
| TenantId                            | tekenreeks          | Tenant-id van CSP                         |
| Upn                                 | tekenreeks          | User Principal Name                   |
| LastNonMfaCompliantLoginDateTime    | datum/tijd        | Laatste keer dat gebruikers zich aanmelden zonder MFA |


## <a name="api-request-summarized-by-application"></a>API-aanvraag samengevat per toepassing

Een samenvatting van de API-aanvraag die wordt gedaan door APP + gebruikersreferenties, geaggregeerd op aanvraagdatum en toepassings-id.

| Eigenschap                            | Type            | Beschrijving               |
|-------------------------------------|-----------------|---------------------------|
| LoginDate                           | datum/tijd        | DATUM VAN API-aanvraag          |
| MfaCompliantRequestCount            | long            | Aantal aanvragen met MFA    |
| TotalRequestCount                   | long            | Totaal aantal aanvragen       |
| ApplicationID                       | tekenreeks          | De toepassings-id        |
| ApplicationName                     | tekenreeks          | De naam van de toepassing      |


## <a name="api-request-details"></a>DETAILS VAN API-aanvraag

API-aanvraag gedaan door APP + gebruikersreferenties. 

| Eigenschap                            | Type            | Beschrijving                              |
|-------------------------------------|-----------------|------------------------------------------|
| RequestId                           | tekenreeks          | MS-RequestId                             |
| CorrelationId                       | tekenreeks          | MS-CorrelationId                         |
| OperationName                       | tekenreeks          | Het API-pad met aanvraagmethode         |
| RequestDateTime                     | DateTime        | De tijd van de API-aanvraag                     |
| IpAddress                           | tekenreeks          | IP-adres van bron                        |
| ObjectId                            | tekenreeks          | Gebruikersobject-id                           |
| TenantId                            | tekenreeks          | Tenant-id van CSP                            |
| Upn                                 | tekenreeks          | User Principal Name                      |
| ApplicationID                       | tekenreeks          | Uw toepassing                         |
| MfaCompliant                        | booleaans            | De aanvraag met of zonder MFA aangeven |
