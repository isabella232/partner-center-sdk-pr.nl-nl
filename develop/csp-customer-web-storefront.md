---
title: Webwinkel van CSP-klant
description: Deze voorbeeldwebsitecode toont een werkende online winkel waar klanten abonnementen op Microsoft-producten kunnen kopen.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 07020c365db2ad578e7ff75602519d06eabb2a3bebf0913899fcd8b5345a0365
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995200"
---
# <a name="csp-customer-web-storefront"></a>Webwinkel van CSP-klant

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Deze voorbeeld-app is alleen van toepassing op het globale exemplaar van Partner Center.

De [Partner Center-webwinkel](https://github.com/Microsoft/Partner-Center-Storefront) is een **voorbeeldwebsite** voor een online winkel die klanten kunnen gebruiken om abonnementen op Microsoft-producten te kopen. U kunt deze **voorbeeldcode voor uw** eigen gebruik wijzigen om de [aanbiedingen te](#configure-offers)configureren, huisstijl toe te voegen en een [](#configure-branding) [betalingswijze toe te voegen.](#configure-payment-types)

## <a name="sample-code"></a>Voorbeeldcode

Download de [voorbeeldcode Partner Center webwinkel](https://github.com/Microsoft/Partner-Center-Storefront) van GitHub.

## <a name="configure-authentication"></a>Verificatie configureren

Voordat u de toepassing bouwt, moet u de volgende waarden in het Web.config-bestand bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie](partner-center-authentication.md). Gebruik de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie (TiP).

- **partnerCenter.applicationId**
- **partnerCenter.applicationSecret**
- **partnerCenter.domain**
- **webPortal.clientId**
- **webPortal.clientSecret**
- **webPortal.domain**
- **webPortal.azureStorageConnectionString**

## <a name="configure-offers"></a>Aanbiedingen configureren

U kunt de set aanbiedingen **(MicrosoftOffer)** configureren in **OfferCatalogViewModel.**

## <a name="configure-branding"></a>Huisstijl configureren

Deze voorbeeldwebsite houdt de volgende bedrijfs- en merkinformatie bij in *BrandingConfiguration.cs* en *PortalBranding.cs:*

- Organisatienaam
- Organisatielogo
- Koptekstafbeelding
- Privacyovereenkomst
- E-mailadres van contactpersoon
- Telefoonnummer van contactpersoon
- Ondersteunings-e-mail
- Telefoonnummer voor ondersteuning

### <a name="configure-payment-types"></a>Betalingstypen configureren

De app gebruikt momenteel een PayPal-gateway, geïmplementeerd in *PayPalGateway.cs.*