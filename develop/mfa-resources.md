---
title: Bronnen voor de beveiliging van partners
description: Meer informatie over de acceptatie van multi-factor Authentication (MFA) om te voldoen aan de beveiligings vereisten van de partner.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: 5eb77c3c10e95c9dc835cfe05e014b9256531b51
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767212"
---
# <a name="partner-security-requirements-resources"></a>Bronnen voor de beveiliging van partners

**Van toepassing op:**

- Partnercentrum

Dit artikel helpt u bij het begrijpen van de vereisten voor de acceptatie van multi-factor Authentication (MFA), zodat uw organisatie kan voldoen aan de status van de beveiligings vereiste van de partner. 

## <a name="portal-request-without-mfa"></a>Portal aanvraag zonder MFA

Geef een gebruiker op die de Partner Center-Portal opent zonder MFA-verificatie.

| Eigenschap                            | Type            | Beschrijving                           |
|-------------------------------------|-----------------|---------------------------------------|
| ObjectId                            | tekenreeks          | Gebruikers object-ID                        |
| TenantId                            | tekenreeks          | CSP-Tenant-ID                         |
| UPN                                 | tekenreeks          | Principal-naam van gebruiker                   |
| LastNonMfaCompliantLoginDateTime    | datum/tijd        | Laatste keer dat de gebruiker zich aanmeldt zonder MFA |


## <a name="api-request-summarized-by-application"></a>API-aanvraag samenvatten door toepassing

Een samen vatting van de API-aanvraag die is gemaakt door de APP + gebruikers referentie, geaggregeerd op aanvraag datum en toepassings-id.

| Eigenschap                            | Type            | Description               |
|-------------------------------------|-----------------|---------------------------|
| LoginDate                           | datum/tijd        | API-aanvraag datum          |
| MfaCompliantRequestCount            | long            | Aantal aanvragen met MFA    |
| TotalRequestCount                   | long            | Totaal aantal aanvragen       |
| ApplicationID                       | tekenreeks          | De toepassings-ID        |
| ApplicationName                     | tekenreeks          | De naam van de toepassing      |


## <a name="api-request-details"></a>Details van API-aanvraag

API-aanvraag gemaakt door APP + gebruikers referentie. 

| Eigenschap                            | Type            | Description                              |
|-------------------------------------|-----------------|------------------------------------------|
| RequestId                           | tekenreeks          | MS-RequestId                             |
| CorrelationId                       | tekenreeks          | MS-CorrelationId                         |
| OperationName                       | tekenreeks          | Het API-pad met de aanvraag methode         |
| RequestDateTime                     | DateTime        | De API-aanvraag tijd                     |
| IPAdres                           | tekenreeks          | IP-adres van bron                        |
| ObjectId                            | tekenreeks          | Gebruikers object-ID                           |
| TenantId                            | tekenreeks          | CSP-Tenant-ID                            |
| UPN                                 | tekenreeks          | Principal-naam van gebruiker                      |
| ApplicationID                       | tekenreeks          | Uw toepassing                         |
| MfaCompliant                        | booleaans            | De aanvraag met of zonder MFA aangeven |
