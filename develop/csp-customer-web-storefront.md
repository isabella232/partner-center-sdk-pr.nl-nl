---
title: Webwinkel van CSP-klant
description: Deze voorbeeld website code toont een werkend online archief voor klanten om abonnementen op micro soft-producten te kopen.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bd488b9b9bf2c1df4bebc8513d230a02b06b2ce4
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767194"
---
# <a name="csp-customer-web-storefront"></a>Webwinkel van CSP-klant

**Van toepassing op:**

- Partnercentrum

> [!NOTE]
> Deze voor beeld-app is alleen van toepassing op het globale exemplaar van partner centrum. Het is niet van toepassing op het partner centrum voor Microsoft Cloud Duitsland of het partner centrum voor Microsoft Cloud voor de Amerikaanse overheid.

Het [Partner Center-winkel](https://github.com/Microsoft/Partner-Center-Storefront) is een voor beeld van een **website** voor een online winkel die klanten kunnen gebruiken om abonnementen op micro soft-producten te kopen. U kunt deze **voorbeeld code** voor eigen gebruik wijzigen om [de aanbiedingen te configureren](#configure-offers), een [huis stijl toe te voegen](#configure-branding) en [een betalings methode toe te voegen](#configure-payment-types).

## <a name="sample-code"></a>Voorbeeldcode

Down load de [voorbeeld code van het Partner Center-winkel programma](https://github.com/Microsoft/Partner-Center-Storefront) vanuit github.

## <a name="configure-authentication"></a>Verificatie configureren

Voordat u de toepassing bouwt, moet u de volgende waarden bijwerken in het Web.config-bestand om de Azure AD-verificatie gegevens weer te geven die u hebt gemaakt in [Partner Center-verificatie](partner-center-authentication.md). U moet uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor testen in productie (TiP).

- **partnerCenter. applicationId**
- **partnerCenter.applicationSecret**
- **partnerCenter. Domain**
- **webportal. clientId**
- **webportal. clientSecret**
- **webportal. domein**
- **webportal. azureStorageConnectionString**

## <a name="configure-offers"></a>Aanbiedingen configureren

U kunt de set met aanbiedingen (**MicrosoftOffer**) configureren in de **OfferCatalogViewModel**.

## <a name="configure-branding"></a>Huis stijl configureren

Deze voorbeeld website houdt de volgende bedrijfs-en merk gegevens bij in *BrandingConfiguration.cs* en *PortalBranding.cs*:

- Organisatienaam
- Logo van organisatie
- Afbeelding van koptekst
- Privacyverklaring
- E-mailadres van contactpersoon
- Telefoon nummer contact persoon
- E-mail voor ondersteuning
- Telefoon nummer voor ondersteuning

### <a name="configure-payment-types"></a>Betalings typen configureren

De app maakt momenteel gebruik van een PayPal-gateway, geïmplementeerd in *PayPalGateway.cs*.