---
title: Marge-resources
description: Resources die marges vertegenwoordigen. Bevat resources voor het beschrijven van de marges.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 83ea2f95c72f4e5074e3396ef226462b5b007878
ms.sourcegitcommit: deb3207935fb5a74df515ed0fd4ffec90e6a143c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2021
ms.locfileid: "129646390"
---
# <a name="margin-resources"></a>Marge-resources

Resources die beschikbare marges vertegenwoordigen. Bevat resources voor het beschrijven van een marge.  

Onafhankelijke softwareleveranciers (ISV's) kunnen kortingen of marges maken voor specifieke Cloud Solution Providers (CSP's). Hieronder vindt u resources die marges vertegenwoordigen en beschrijven.
                
## <a name="margin"></a>Margin                   
                        
Vertegenwoordigt een tevaleerbare marge voor een bepaalde CSP.
                
| Naam            | Type            | Beschrijving                               |
|-----------------|-----------------|-------------------------------------------|
| id              | tekenreeks          | De unieke id voor de marge.         |
| marginPercentage | getal         | Een kortingspercentage dat wordt toegepast op de CSP-retailprijs.  |
| productId       | tekenreeks          | De product-id waar de marge voor beschikbaar is.   |
| productTitle    | tekenreeks          | De producttitel waar de marge voor beschikbaar is. |
| productType     | tekenreeks          | Het producttype waar de marge beschikbaar voor is.   |
| publisherName   | tekenreeks          | De naam van de ISV die de marge heeft gemaakt.  |
| skuId           | tekenreeks          | De SKU-id waar de marge beschikbaar voor is.  |
| skuTitle        | tekenreeks          | De SKU-titel waar de marge beschikbaar voor is. |
| Startdate       | tekenreeks          | De begindatum waarop de marge beschikbaar is. |
| Enddate         | tekenreeks          | De einddatum waarop de marge in beschikbaar is. |
| status          | tekenreeks          | Status die aanklaagt of de marge beschikbaar is. |
| statusDate      | tekenreeks          | De datum waarop de status voor het laatst is bijgewerkt. |

## <a name="definitions"></a>Definities

Verschillende typen artefacten die marges beschrijven.                    

| Naam            | Beschrijving          |
|-----------------|----------------------|
| Margin |  Hiermee definieert u een afzonderlijke marge.  |    
| MarginSearchResponse |  Hiermee definieert u de antwoordgegevens voor de marge.  |  
        
## <a name="related-documentation"></a>Verwante documentatie

- [Overzicht van marges in Partner Center](/partner-center/csp-commercial-marketplace-margins)
- [Marketplace-aanbiedingen aanschaffen](/partner-center/csp-commercial-marketplace-purchase)
- [Marketplace-aanbiedingen beheren](/partner-center/csp-commercial-marketplace-manage)
- [Een lijst met marges op halen](get-margins.md)
- [Een lijst met marges downloaden](download-margins.md)
