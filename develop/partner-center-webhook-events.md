---
title: Partner centrum-gebeurtenissen voor webhooks
description: Documentatie voor alle webhook-gebeurtenissen die worden ondersteund door het partner centrum.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 5358aab8efdd68ad52c583936304f99ffae12708
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767344"
---
# <a name="partner-center-webhook-events"></a>Partner centrum-gebeurtenissen voor webhooks

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Partner Center-gebeurtenissen voor webhooks zijn bron wijzigings gebeurtenissen die worden geleverd in de vorm van HTTP-berichten naar een geregistreerde URL. Als u een gebeurtenis van het partner centrum wilt ontvangen, moet u een call back hosten waarin het partner centrum de gebeurtenis kan plaatsen. De gebeurtenis is digitaal ondertekend, zodat u kunt valideren dat deze is verzonden vanuit het partner centrum.

Voor informatie over het ontvangen van gebeurtenissen, het verifiëren van een call back en het gebruik van de Api's van de webhook van partner Center voor het maken, weer geven en bijwerken van een gebeurtenis registratie raadpleegt u [Partner Center-webhooks](partner-center-webhooks.md).

## <a name="supported-events"></a>Ondersteunde gebeurtenissen

De volgende webhook-gebeurtenissen worden ondersteund door het partner centrum.

### <a name="test-event"></a>Test gebeurtenis

Met deze gebeurtenis kunt u zelf onboards en uw registratie testen door een test gebeurtenis aan te vragen en de voortgang op te sporen. U kunt de fout berichten zien die van micro soft worden ontvangen tijdens het leveren van de gebeurtenis. Dit is alleen van toepassing op gebeurtenissen waarbij de test is gemaakt en gegevens die ouder zijn dan 7 dagen worden verwijderd.

>[!NOTE]
>Er geldt een beperkings limiet van 2 aanvragen per minuut bij het boeken van een test-gemaakte gebeurtenis.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde ' test-created '.                                          |
| ResourceUri               | URI                                | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/Registration/validationEvents/{{CorrelationId}}" |
| ResourceName              | tekenreeks                             | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde ' test '.                                  |
| AuditUri                  | URI                                | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{{CorrelationId}}",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### <a name="subscription-updated-event"></a>Gebeurtenis bijgewerkt abonnement

Deze gebeurtenis treedt op wanneer het opgegeven abonnement wordt gewijzigd. Er wordt een bijgewerkte gebeurtenis gegenereerd wanneer er sprake is van een interne wijziging naast wanneer wijzigingen worden aangebracht via de partner centrum-API.  Deze gebeurtenis wordt alleen gegenereerd als er wijzigingen op Commerce niveau zijn, bijvoorbeeld wanneer het aantal licenties wordt gewijzigd en wanneer de status van het abonnement wordt gewijzigd. Het wordt niet gegenereerd wanneer er resources worden gemaakt binnen het abonnement.

>[!NOTE]
>Er is een vertraging van Maxi maal 48 uur tussen het tijdstip waarop een abonnement wijzigt en wanneer de gebeurtenis bijgewerkt abonnement wordt geactiveerd.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde ' abonnement-bijgewerkt '.                                  |
| ResourceUri               | URI                                | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/Customers/{{CustomerId}}/Subscriptions/{{SubscriptionId}}" |
| ResourceName              | tekenreeks                             | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde ' abonnement '.                          |
| AuditUri                  | URI                                | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "subscription-updated",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/customers/{{CustomerId}}/subscriptions/{{SubscriptionId}}",
    "ResourceName": "subscription",
    "AuditUri": "https://api.partnercenter.microsoft.com/v1/auditrecords/{{AuditId}}",
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

### <a name="threshold-exceeded-event"></a>Gebeurtenis drempelwaarde overschreden

Deze gebeurtenis treedt op wanneer de hoeveelheid Microsoft Azure gebruik voor een klant groter is dan het bestedings budget van het gebruik (de drempel waarde). Zie voor meer informatie [een Azure-uitgaven budget instellen voor uw klanten/Partner-Center/set-a-Azure-besteding-budget-voor-uw klanten).

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde "usagerecords-thresholdExceeded".                                  |
| ResourceUri               | URI                                | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/Customers/usagerecords" |
| ResourceName              | tekenreeks                             | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde "usagerecords".                          |
| AuditUri                  | URI                                | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "usagerecords-thresholdExceeded",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/customers/usagerecords",
    "ResourceName": "usagerecords",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="referral-created-event"></a>Gebeurtenis verwijzing gemaakt

Deze gebeurtenis treedt op wanneer de verwijzing wordt gemaakt.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde ' Referral-created '.                                  |
| ResourceUri               | URI                                | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/Engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | tekenreeks                             | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde ' Referral '.                          |
| AuditUri                  | URI                                | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "referral-created",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="referral-updated-event"></a>Gebeurtenis verwijzing bijgewerkt

Deze gebeurtenis treedt op wanneer de verwijzing wordt bijgewerkt.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde ' referentie-bijgewerkt '.                                  |
| ResourceUri               | URI                                | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/Engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | tekenreeks                             | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde ' Referral '.                          |
| AuditUri                  | URI                                | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "referral-updated",
    "ResourceUri": "https://api.partnercenter.microsoft.com/engagements/v1/referrals/{{ReferralID}}",
    "ResourceName": "referral",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}
```

### <a name="invoice-ready-event"></a>Gebeurtenis factuur gereed

Deze gebeurtenis treedt op wanneer de nieuwe factuur gereed is.

| Eigenschap                  | Type                               | Description                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam | tekenreeks | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Voor deze gebeurtenis is de waarde ' factuur-gereed '. |
| ResourceUri | URI | De URI voor het ophalen van de resource. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{{InvoiceId}}" |
| ResourceName | tekenreeks | De naam van de resource waarmee de gebeurtenis wordt geactiveerd. Voor deze gebeurtenis is de waarde "invoice". |
| AuditUri |  URI | Beschrijving De URI voor het ophalen van de controle record, als deze bestaat. Gebruikt de syntaxis: "[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}") |
| ResourceChangeUtcDate | teken reeks in de UTC-datum-tijd notatie | De datum en tijd waarop de resource is gewijzigd. |

#### <a name="example"></a>Voorbeeld

```json
{
    "EventName": "invoice-ready",
    "ResourceUri": "https://api.partnercenter.microsoft.com/v1/invoices/{{InvoiceId}}",
    "ResourceName": "invoice",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2018-02-17T00:05:39.5485487+00:00"
}

```
