---
title: Resources controleren
description: Meer informatie Partner Center API-controlebronnen, zoals AuditRecord, die u kunt gebruiken om een record van Partner Center op te halen.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9d78a305c2d27dc692c609e30817b34b1f814157
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974349"
---
# <a name="auditing-resources-that-help-you-get-a-record-of-partner-center-activity"></a>Resources controleren die u helpen een record van uw Partner Center op te halen

U kunt de volgende resources gebruiken met auditbewerkingen.

## <a name="auditrecord"></a>AuditRecord

Vertegenwoordigt een record van een bewerking die wordt uitgevoerd door een partnergebruiker of -toepassing.

| Eigenschap | Type | Beschrijving |
| --- | --- | ---|
| customerId | tekenreeks | Een tekenreeks in GUID-indeling die de klant identificeert. |
| customerName | tekenreeks | De naam van de klant. |
| userPrincipalName | tekenreeks | De user principal name of gebruikers-id. Normaal gesproken is deze eigenschap een aanmeldingsnaam in internetstijl voor een gebruiker in een e-mailadresindeling op basis van de internetstandaard RFC 822. |
| applicationId | tekenreeks | Een tekenreeks die de toepassing identificeert die de bewerking heeft uitgevoerd. |
| resourceType | tekenreeks | Het type resource waarop de bewerking heeft uitgevoerd. Mogelijke waarden: `customer` , , , , , , , , `customer_user` , , `order` , , , `subscription` , `license` , `third_party_add_on` `mpn_association` `transfer` `application` `application_credential` `partner_user` `partner_relationship` `partner_customer_dap` `customer_directory_role` . |
| resourceOldValue | tekenreeks | De oude waarde van de resource. |
| resourceNewValue | tekenreeks | De nieuwe waarde van de resource. |
| operationType | tekenreeks | Het type bewerking dat is uitgevoerd. Mogelijke waarden: `update_customer_qualification` , , , , , , , ( `update_subscription` alleen `upgrade_subscription` `convert_trial_subscription` `add_customer` `update_customer_billing_profile` `update_customer_partner_contract_company_name` `update_customer_spending_budget` `delete_customer` sandbox-integratieaccounts), `remove_partner_customer_relationship` , `create_order` `update_order` `create_customer_user` `delete_customer_user` `update_customer_user` `update_customer_user_licenses` `reset_customer_user_password` `update_customer_user_principal_name` `restore_customer_user` `create_mpn_association` `update_mpn_association` `update_sfb_customer_user_licenses` `update_transfer` `create_partner_relationship` `register_application` , `unregister_application` `add_application_credential` `remove_application_credential` `create_partner_user` `update_partner_user` , , `create_self_serve_policy` `update_self_serve_policy` , `create_self_serve_policy` `delete_self_serve_policy` , `remove_partner_relationship` `delete_tip_customer` , `create_related_referral` `update_related_referral` , `create_referral` `update_referral` `get_software_key` `get_software_download_link` `increase_spending_limit` `ready_invoice` `create_agreement` `extend_relationship` `create_transfer` `dap_admin_relationship_approved` `dap_admin_relationship_terminated` `add_user_member` `remove_user_member` . |
| operationDate | tekenreeks in UTC-datum/tijd-indeling | De datum en tijd waarop de bewerking is uitgevoerd. |
| operationStatus | tekenreeks | De status van de bewerking die wordt gecontroleerd. Mogelijke waarden: `succeeded` , of , wat betekent dat de bewerking nog wordt `failed` `progress` uitgevoerd. |
| customizedData  | matrix met objecten | Aanvullende informatie. Elk object bevat twee JSON-sleutel-waardeparen: het eerste is en een tekenreekswaarde, `key` de tweede is en een `value` tekenreekswaarde. Het aantal objecten in de matrix is afhankelijk van het type bewerking dat is uitgevoerd. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. |
