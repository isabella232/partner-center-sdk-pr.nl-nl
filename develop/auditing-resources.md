---
title: Controle bronnen
description: Meer informatie over Partner Center API auditing resources, zoals AuditRecord, die u kunt gebruiken om een record van de Partner Center-activiteit op te halen.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 31832492913e866b078c3c638e22c1a4b8d5e7e6
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767596"
---
# <a name="auditing-resources-that-help-you-get-a-record-of-partner-center-activity"></a>Controle bronnen die u helpen bij het ophalen van een record van de Partner Center-activiteit

**Van toepassing op:**

- Partnercentrum

U kunt de volgende resources gebruiken met audit bewerkingen.

## <a name="auditrecord"></a>AuditRecord

Vertegenwoordigt een record van een bewerking die wordt uitgevoerd door een partner gebruiker of-toepassing.

| Eigenschap | Type | Description |
| --- | --- | ---|
| customerId | tekenreeks | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |
| customerName | tekenreeks | De naam van de klant. |
| userPrincipalName | tekenreeks | De user principal name of de gebruikers-id. Deze eigenschap is doorgaans een aanmeldings naam voor Internet voor een gebruiker in een e-mailadres indeling op basis van Internet Standard RFC 822. |
| applicationId | tekenreeks | Een teken reeks waarmee de toepassing wordt geïdentificeerd die de bewerking heeft uitgevoerd. |
| resourceType | tekenreeks | Het type resource dat door de bewerking wordt verwerkt. Mogelijke waarden: `customer` , `customer_user` , `order` , `subscription` , `license` , `third_party_add_on` , `mpn_association` , `transfer` , `application` , `application_credential` , `partner_user` , `partner_relationship` . |
| resourceOldValue | tekenreeks | De oude waarde van de resource. |
| resourceNewValue | tekenreeks | De nieuwe waarde van de resource. |
| operationType | tekenreeks | Het type bewerking dat wordt uitgevoerd. Mogelijke waarden: `update_customer_qualification` , `update_subscription` , `upgrade_subscription` , `convert_trial_subscription` , `add_customer` , `update_customer_billing_profile` , `update_customer_partner_contract_company_name` , `update_customer_spending_budget` , `delete_customer` (alleen voor sandbox-integratie accounts), `remove_partner_customer_relationship` , `create_order` , `update_order` , `create_customer_user` ,, `delete_customer_user` , `update_customer_user` `update_customer_user_licenses` `reset_customer_user_password` `update_customer_user_principal_name` `restore_customer_user` `create_mpn_association` `update_mpn_association` `update_sfb_customer_user_licenses` `update_transfer` `create_partner_relationship` `register_application` `unregister_application` `add_application_credential` `remove_application_credential` `create_partner_user` `update_partner_user` `create_self_serve_policy` `update_self_serve_policy` `create_self_serve_policy` `delete_self_serve_policy` `remove_partner_relationship` `delete_tip_customer` `create_related_referral` `update_related_referral` `create_referral` `update_referral` `get_software_key` `get_software_download_link` `increase_spending_limit` `ready_invoice` `create_agreement` `extend_relationship` `create_transfer` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,. |
| operationDate | teken reeks in UTC-datum-tijd notatie | De datum en tijd waarop de bewerking is uitgevoerd. |
| operationStatus | tekenreeks | De status van de bewerking die wordt gecontroleerd. Mogelijke waarden: `succeeded` , `failed` of `progress` , wat betekent dat de bewerking nog steeds wordt uitgevoerd. |
| customizedData  | matrix van objecten | Aanvullende informatie. Elk object bevat twee JSON-sleutel-waardeparen: de eerste is `key` en een teken reeks waarde, de tweede is `value` en een teken reeks waarde. Het aantal objecten in de matrix is afhankelijk van het type bewerking dat is uitgevoerd. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. |
