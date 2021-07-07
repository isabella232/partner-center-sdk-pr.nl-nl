---
title: Partner Center webhookgebeurtenissen
description: Informatie over het testen en gebruiken van webhookgebeurtenissen om te noteren wanneer abonnementen en andere gebeurtenissen in de Partner Center.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: e5e363a2f928dd38304887547bdc0e5d652728d6
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547737"
---
# <a name="partner-center-webhook-events"></a>Partner Center webhookgebeurtenissen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Partner Center webhookgebeurtenissen zijn gebeurtenissen voor resourcewijziging die worden geleverd in de vorm van HTTP POST's naar een geregistreerde URL. Als u een gebeurtenis wilt ontvangen van Partner Center, host u een callback waar Partner Center de gebeurtenis kan plaatsen. De gebeurtenis is digitaal ondertekend, zodat u kunt controleren of deze is verzonden vanuit Partner Center.

Zie [webhooks](partner-center-webhooks.md)voor meer informatie over het ontvangen van gebeurtenissen, het verifiëren van een callback en het gebruik van de Partner Center-webhook-API's om een gebeurtenisregistratie te maken Partner Center, weer te geven en bij te werken.

## <a name="supported-events"></a>Ondersteunde gebeurtenissen

De volgende webhookgebeurtenissen worden ondersteund door Partner Center.

### <a name="test-event"></a>Testgebeurtenis

Met deze gebeurtenis kunt u uw registratie zelf onboarden en testen door een testgebeurtenis aan te vragen en vervolgens de voortgang ervan bij te houden. U kunt de foutberichten zien die van Microsoft worden ontvangen tijdens het leveren van de gebeurtenis. Dit geldt alleen voor 'door een test gemaakte' gebeurtenissen en gegevens die ouder zijn dan zeven dagen worden verwijderd.

>[!NOTE]
>Er geldt een vertragingslimiet van 2 aanvragen per minuut bij het plaatsen van een door een test gemaakte gebeurtenis.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'test-created'.                                          |
| ResourceUri               | URI                                | De URI om de resource op te halen. Maakt gebruik van de syntaxis:[*"{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/registration/validationEvents/{{CorrelationId}}" |
| ResourceName              | tekenreeks                             | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde 'test'.                                  |
| AuditUri                  | URI                                | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de syntaxis:[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | tekenreeks in de UTC-datum/tijd-notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

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

### <a name="subscription-updated-event"></a>Gebeurtenis abonnement bijgewerkt

Deze gebeurtenis teert wanneer het opgegeven abonnement wordt gewijzigd. Er wordt een gebeurtenis Abonnement bijgewerkt gegenereerd wanneer er een interne wijziging is naast wanneer er wijzigingen worden aangebracht via de Partner Center API.  Deze gebeurtenis wordt alleen gegenereerd wanneer er wijzigingen in het commerceniveau zijn, bijvoorbeeld wanneer het aantal licenties wordt gewijzigd en wanneer de status van het abonnement verandert. Deze wordt niet gegenereerd wanneer resources binnen het abonnement worden gemaakt.

>[!NOTE]
>Er is een vertraging van maximaal 48 uur tussen het moment waarop een abonnement wordt gewijzigd en het moment waarop de gebeurtenis Abonnement bijgewerkt wordt geactiveerd.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'abonnement bijgewerkt'.                                  |
| ResourceUri               | URI                                | De URI om de resource op te halen. Maakt gebruik van de syntaxis :[*{baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/{{CustomerId}}/subscriptions/{{SubscriptionId}}" |
| ResourceName              | tekenreeks                             | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde 'abonnement'.                          |
| AuditUri                  | URI                                | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de syntaxis:[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | tekenreeks in de UTC-datum/tijd-notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

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

Deze gebeurtenis teert wanneer de hoeveelheid Microsoft Azure voor elke klant het gebruiksuitgavenbudget (hun drempelwaarde) overschrijdt. Zie [Een Azure-uitgavenbudget instellen voor uw klanten/partnercentrum/set-an-azure-spending-budget-for-your-customers) voor meer informatie.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'usagerecords-thresholdExceeded'.                                  |
| ResourceUri               | URI                                | De URI om de resource op te halen. Maakt gebruik van de [*syntaxis: {baseURL}*](partner-center-rest-urls.md)/webhooks/v1/customers/usagerecords |
| ResourceName              | tekenreeks                             | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde 'usagerecords'.                          |
| AuditUri                  | URI                                | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de syntaxis:[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | tekenreeks in de UTC-datum/tijd-notatie | De datum en tijd waarop de resource is gewijzigd.                                                         |

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

### <a name="referral-created-event"></a>Door verwijzing gemaakte gebeurtenis

Deze gebeurtenis wordt aangemaakt wanneer de verwijzing wordt gemaakt.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'verwijzing gemaakt'.                                  |
| ResourceUri               | URI                                | De URI om de resource op te halen. Maakt gebruik van de syntaxis:[*"{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | tekenreeks                             | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde verwijzing.                          |
| AuditUri                  | URI                                | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de [*syntaxis: {baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | tekenreeks in de UTC-datum/tijd-indeling | De datum en tijd waarop de resource is gewijzigd.                                                         |

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

### <a name="referral-updated-event"></a>Gebeurtenis bijgewerkt door verwijzing

Deze gebeurtenis t doet zich voor wanneer de verwijzing wordt bijgewerkt.

#### <a name="properties"></a>Eigenschappen

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam                 | tekenreeks                             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'verwijzing bijgewerkt'.                                  |
| ResourceUri               | URI                                | De URI om de resource op te halen. Maakt gebruik van de syntaxis:[*"{baseURL}*](partner-center-rest-urls.md)/engagements/v1/referrals/{{ReferralID}}" |
| ResourceName              | tekenreeks                             | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde verwijzing.                          |
| AuditUri                  | URI                                | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de [*syntaxis: {baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}" |
| ResourceChangeUtcDate     | tekenreeks in de UTC-datum/tijd-indeling | De datum en tijd waarop de resource is gewijzigd.                                                         |

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

### <a name="invoice-ready-event"></a>Gebeurtenis gereed voor factuur

Deze gebeurtenis wordt verhoogd wanneer de nieuwe factuur gereed is.

| Eigenschap                  | Type                               | Beschrijving                                                                                                  |
|---------------------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Gebeurtenisnaam | tekenreeks | De naam van de gebeurtenis. In de vorm {resource}-{action}. Voor deze gebeurtenis is de waarde 'gereed voor factuur'. |
| ResourceUri | URI | De URI om de resource op te halen. Maakt gebruik van de syntaxis :[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{{InvoiceId}}" |
| ResourceName | tekenreeks | De naam van de resource die de gebeurtenis activeert. Voor deze gebeurtenis is de waarde 'factuur'. |
| AuditUri |  URI | (Optioneel) De URI om de controlerecord op te halen, als deze bestaat. Maakt gebruik van de syntaxis:[*{baseURL}*](partner-center-rest-urls.md)/auditactivity/v1/auditrecords/{{AuditId}}") |
| ResourceChangeUtcDate | tekenreeks in de UTC-datum/tijd-indeling | De datum en tijd waarop de resource is gewijzigd. |

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
