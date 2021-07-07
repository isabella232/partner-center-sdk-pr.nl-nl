---
title: Webwinkel van CSP-klant
description: Deze voorbeeldwebsitecode toont een werkende online winkel waar klanten abonnementen op Microsoft-producten kunnen kopen.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d68f17d707731f426cb980a566b6478790d3507c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973329"
---
# <a name="csp-customer-web-storefront"></a>Webwinkel van CSP-klant

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Deze voorbeeld-app is alleen van toepassing op het globale exemplaar van Partner Center.

De [Partner Center-webwinkel](https://github.com/Microsoft/Partner-Center-Storefront) is een **voorbeeldwebsite** voor een online winkel die klanten kunnen gebruiken om abonnementen op Microsoft-producten te kopen. U kunt deze **voorbeeldcode voor eigen** gebruik wijzigen om de [aanbiedingen te](#configure-offers)configureren, huisstijl toe te voegen en een [](#configure-branding) [betalingswijze toe te voegen.](#configure-payment-types)

## <a name="sample-code"></a>Voorbeeldcode

Download de [voorbeeldcode Partner Center webwinkel van](https://github.com/Microsoft/Partner-Center-Storefront) GitHub.

## <a name="configure-authentication"></a>Verificatie configureren

Voordat u de toepassing bouwt, moet u de volgende waarden in het Web.config-bestand bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md) Gebruik de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie (TiP).

- **partnerCenter.applicationId**
- **partnerCenter.applicationSecret**
- **partnerCenter.domain**
- **webPortal.clientId**
- **webPortal.clientSecret**
- **webPortal.domain**
- **webPortal.azureStorageConnectionString**

## <a name="configure-offers"></a>Aanbiedingen configureren

U kunt de set aanbiedingen (**MicrosoftOffer**) configureren in **OfferCatalogViewModel.**

## <a name="configure-branding"></a>Huisstijl configureren

Deze voorbeeldwebsite houdt de volgende bedrijfs- en merkinformatie bij in *BrandingConfiguration.cs* en *PortalBranding.cs:*

- Organisatienaam
- Organisatielogo
- Koptekstafbeelding
- Privacyovereenkomst
- E-mailadres van contactpersoon
- Telefoonnummer van contactpersoon
- Ondersteunings-e-mail
- Ondersteuningstelefoonnummer

### <a name="configure-payment-types"></a>Betalingstypen configureren

De app gebruikt momenteel een PayPal-gateway, geïmplementeerd in *PayPalGateway.cs.*