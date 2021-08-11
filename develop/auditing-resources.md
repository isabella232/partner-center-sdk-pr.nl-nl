---
title: Resources controleren
description: Meer informatie Partner Center API-controlebronnen, zoals AuditRecord, die u kunt gebruiken om een record van de Partner Center op te halen.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 50c90f7e7a5dfb274044fafab87818c7ac8428124ca9072770cc5fd9fa3806d5
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994656"
---
# <a name="auditing-resources-that-help-you-get-a-record-of-partner-center-activity"></a>Resources controleren die u helpen een record op te halen van Partner Center activiteit

U kunt de volgende resources gebruiken met controlebewerkingen.

## <a name="auditrecord"></a>AuditRecord

Vertegenwoordigt een record van een bewerking die wordt uitgevoerd door een partnergebruiker of -toepassing.

| Eigenschap | Type | Description |
| --- | --- | ---|
| customerId | tekenreeks | Een tekenreeks in GUID-indeling die de klant identificeert. |
| customerName | tekenreeks | De naam van de klant. |
| userPrincipalName | tekenreeks | De user principal name of gebruikers-id. Deze eigenschap is doorgaans een aanmeldingsnaam in internetstijl voor een gebruiker in een indeling voor e-mailadressen op basis van internetstandaard RFC 822. |
| applicationId | tekenreeks | Een tekenreeks die de toepassing identificeert die de bewerking heeft uitgevoerd. |
| resourceType | tekenreeks | Het type resource dat door de bewerking wordt uitgevoerd. Mogelijke waarden: `customer` , , , , , , , , , `customer_user` , , `order` , , , `subscription` , `license` `third_party_add_on` `mpn_association` `transfer` `application` `application_credential` `partner_user` `partner_relationship` `partner_customer_dap` `customer_directory_role` . |
| resourceOldValue | tekenreeks | De oude waarde van de resource. |
| resourceNewValue | tekenreeks | De nieuwe waarde van de resource. |
| operationType | tekenreeks | Het type uitgevoerde bewerking. Mogelijke waarden: `update_customer_qualification` , , , , , , , , , `update_subscription` , `upgrade_subscription` `convert_trial_subscription` `add_customer` `update_customer_billing_profile` `update_customer_partner_contract_company_name` `update_customer_spending_budget` `delete_customer` (alleen sandbox-integratieaccounts), `remove_partner_customer_relationship` , `create_order` , `update_order` `create_customer_user` `delete_customer_user` `update_customer_user` `update_customer_user_licenses` `reset_customer_user_password` `update_customer_user_principal_name` `restore_customer_user` `create_mpn_association` `update_mpn_association` `update_sfb_customer_user_licenses` `update_transfer` `create_partner_relationship` `register_application` `unregister_application` `add_application_credential` `remove_application_credential` `create_partner_user` `update_partner_user` `create_self_serve_policy` `update_self_serve_policy` `create_self_serve_policy` `delete_self_serve_policy` `remove_partner_relationship` `delete_tip_customer` `create_related_referral` `update_related_referral` `create_referral` `update_referral` `get_software_key` `get_software_download_link` `increase_spending_limit` `ready_invoice` `create_agreement` `extend_relationship` `create_transfer` `dap_admin_relationship_approved` `dap_admin_relationship_terminated` `add_user_member` `remove_user_member` . |
| operationDate | tekenreeks in UTC-datum/tijd-indeling | De datum en tijd waarop de bewerking is uitgevoerd. |
| operationStatus | tekenreeks | De status van de bewerking die wordt gecontroleerd. Mogelijke waarden: `succeeded` , of , wat betekent dat de bewerking nog wordt `failed` `progress` uitgevoerd. |
| customizedData  | matrix van objecten | Aanvullende informatie. Elk object bevat twee JSON-sleutel-waardeparen: de eerste is en een tekenreekswaarde, `key` de tweede is en een `value` tekenreekswaarde. Het aantal objecten in de matrix is afhankelijk van het type bewerking dat is uitgevoerd. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. |
