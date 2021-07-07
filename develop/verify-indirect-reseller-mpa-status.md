---
title: De handtekeningstatus van een indirecte reseller Microsoft Partner-overeenkomst controleren
description: U kunt de AgreementStatus-API gebruiken om te controleren of een indirecte reseller de Microsoft Partner-overeenkomst.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f83acc61624a72354c390905b1250bc021dd39aa
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529831"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a><span data-ttu-id="147ce-103">De handtekeningstatus van een indirecte reseller Microsoft Partner-overeenkomst controleren</span><span class="sxs-lookup"><span data-stu-id="147ce-103">Verify an indirect reseller's Microsoft Partner Agreement signing status</span></span>

<span data-ttu-id="147ce-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="147ce-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="147ce-105">U kunt controleren of een indirecte reseller de Microsoft Partner-overeenkomst heeft ondertekend met behulp van de Microsoft Partner Network-id (PGA/PLA) of de tenant-id van Cloud Solution Provider (CSP) (Microsoft ID).</span><span class="sxs-lookup"><span data-stu-id="147ce-105">You can verify whether an indirect reseller has signed the Microsoft Partner Agreement using their Microsoft Partner Network (MPN) ID (PGA/PLA) or Cloud Solution Provider (CSP) tenant ID (Microsoft ID).</span></span> <span data-ttu-id="147ce-106">U kunt een van deze id's gebruiken om de status van Microsoft Partner-overeenkomst te controleren met behulp van de **AgreementStatus-API.**</span><span class="sxs-lookup"><span data-stu-id="147ce-106">You can use one of these identifiers to check the Microsoft Partner Agreement signing status using the **AgreementStatus** API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="147ce-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="147ce-107">Prerequisites</span></span>

- <span data-ttu-id="147ce-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="147ce-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="147ce-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="147ce-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="147ce-110">De MPN-id (PGA/PLA) of de CSP-tenant-id (Microsoft-id) van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="147ce-110">The MPN ID (PGA/PLA) or the CSP tenant ID (Microsoft ID) of the indirect reseller.</span></span> <span data-ttu-id="147ce-111">*U moet een van deze twee id's gebruiken.*</span><span class="sxs-lookup"><span data-stu-id="147ce-111">*You must use one of these two identifiers.*</span></span>

## <a name="c"></a><span data-ttu-id="147ce-112">C\#</span><span class="sxs-lookup"><span data-stu-id="147ce-112">C\#</span></span>

<span data-ttu-id="147ce-113">De handtekeningstatus van Microsoft Partner-overeenkomst indirecte reseller op te halen:</span><span class="sxs-lookup"><span data-stu-id="147ce-113">To get the Microsoft Partner Agreement signature status of an indirect reseller:</span></span>

1. <span data-ttu-id="147ce-114">Gebruik de **verzameling IAggregatePartner.Compliance** om de eigenschap **AgreementSignatureStatus aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="147ce-114">Use your **IAggregatePartner.Compliance** collection to call the **AgreementSignatureStatus** property.</span></span>

2. <span data-ttu-id="147ce-115">Roep de [**methode Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="147ce-115">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- <span data-ttu-id="147ce-116">Voorbeeld: **[Consoletest-app](console-test-app.md)**</span><span class="sxs-lookup"><span data-stu-id="147ce-116">Sample: **[Console test app](console-test-app.md)**</span></span>
- <span data-ttu-id="147ce-117">Project: **PartnerCenterSDK.FeaturesSamples**</span><span class="sxs-lookup"><span data-stu-id="147ce-117">Project: **PartnerCenterSDK.FeaturesSamples**</span></span>
- <span data-ttu-id="147ce-118">Klasse: **GetAgreementSignatureStatus.cs**</span><span class="sxs-lookup"><span data-stu-id="147ce-118">Class: **GetAgreementSignatureStatus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="147ce-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="147ce-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="147ce-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="147ce-120">Request syntax</span></span>

| <span data-ttu-id="147ce-121">Methode</span><span class="sxs-lookup"><span data-stu-id="147ce-121">Method</span></span> | <span data-ttu-id="147ce-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="147ce-122">Request URI</span></span> |
| ------ | ----------- |
| <span data-ttu-id="147ce-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="147ce-123">**GET**</span></span> | <span data-ttu-id="147ce-124">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId}</span><span class="sxs-lookup"><span data-stu-id="147ce-124">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="147ce-125">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="147ce-125">URI parameters</span></span>

<span data-ttu-id="147ce-126">U moet een van de volgende twee queryparameters opgeven om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="147ce-126">You must provide one of the following two query parameters to identify the partner.</span></span> <span data-ttu-id="147ce-127">Als u geen van deze twee queryparameters opvraagt, ontvangt u de **foutmelding 400 (Foute** aanvraag).</span><span class="sxs-lookup"><span data-stu-id="147ce-127">If you don't provide one of these two query parameters, you will receive a **400 (Bad request)** error.</span></span>

| <span data-ttu-id="147ce-128">Naam</span><span class="sxs-lookup"><span data-stu-id="147ce-128">Name</span></span> | <span data-ttu-id="147ce-129">Type</span><span class="sxs-lookup"><span data-stu-id="147ce-129">Type</span></span> | <span data-ttu-id="147ce-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="147ce-130">Required</span></span> | <span data-ttu-id="147ce-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="147ce-131">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="147ce-132">**MpnId**</span><span class="sxs-lookup"><span data-stu-id="147ce-132">**MpnId**</span></span> | <span data-ttu-id="147ce-133">int</span><span class="sxs-lookup"><span data-stu-id="147ce-133">int</span></span> | <span data-ttu-id="147ce-134">Nee</span><span class="sxs-lookup"><span data-stu-id="147ce-134">No</span></span> | <span data-ttu-id="147ce-135">Een Microsoft Partner Network-id (PGA/PLA) die de indirecte reseller identificeert.</span><span class="sxs-lookup"><span data-stu-id="147ce-135">A Microsoft Partner Network ID (PGA/PLA) that identifies the indirect reseller.</span></span> |
| <span data-ttu-id="147ce-136">**Tenant-ID**</span><span class="sxs-lookup"><span data-stu-id="147ce-136">**TenantId**</span></span> | <span data-ttu-id="147ce-137">GUID</span><span class="sxs-lookup"><span data-stu-id="147ce-137">GUID</span></span> | <span data-ttu-id="147ce-138">Nee</span><span class="sxs-lookup"><span data-stu-id="147ce-138">No</span></span> | <span data-ttu-id="147ce-139">Een Microsoft-id die het CSP-account van de indirecte reseller identificeert.</span><span class="sxs-lookup"><span data-stu-id="147ce-139">A Microsoft ID that identifies the CSP account of the indirect reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="147ce-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="147ce-140">Request headers</span></span>

<span data-ttu-id="147ce-141">Zie voor meer informatie [Partner Center REST.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="147ce-141">For more information, see [Partner Center REST](headers.md).</span></span>

### <a name="request-examples"></a><span data-ttu-id="147ce-142">Voorbeelden van aanvragen</span><span class="sxs-lookup"><span data-stu-id="147ce-142">Request examples</span></span>

#### <a name="request-using-mpn-id-pgapla"></a><span data-ttu-id="147ce-143">Aanvraag met MPN-id (PGA/PLA)</span><span class="sxs-lookup"><span data-stu-id="147ce-143">Request using MPN ID (PGA/PLA)</span></span>

<span data-ttu-id="147ce-144">Met de volgende voorbeeldaanvraag wordt de handtekeningstatus van de indirecte reseller Microsoft Partner-overeenkomst met behulp van de id van Microsoft Partner Network indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="147ce-144">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's Microsoft Partner Network ID.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a><span data-ttu-id="147ce-145">Aanvragen met behulp van CSP-tenant-id</span><span class="sxs-lookup"><span data-stu-id="147ce-145">Request using CSP tenant ID</span></span>

<span data-ttu-id="147ce-146">Met de volgende voorbeeldaanvraag wordt de ondertekeningsstatus van de indirecte reseller Microsoft Partner-overeenkomst met behulp van de CSP-tenant-id (Microsoft-id) van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="147ce-146">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's CSP tenant ID (Microsoft ID).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="147ce-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="147ce-147">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="147ce-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="147ce-148">Response success and error codes</span></span>

<span data-ttu-id="147ce-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="147ce-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="147ce-150">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="147ce-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="147ce-151">Zie voor de volledige lijst Partner Center [REST-fout](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="147ce-151">For the full list, see [Partner Center REST error](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="147ce-152">Voorbeeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="147ce-152">Response example (success)</span></span>

<span data-ttu-id="147ce-153">In het volgende voorbeeld wordt met succes een antwoord gegeven of de indirecte reseller de Microsoft Partner-overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="147ce-153">The following example response successfully returns whether the indirect reseller has signed the Microsoft Partner Agreement.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 29
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: jn3r+1wpE06nCt/0.0
MS-ServerId: 0000005B
Date: Tue, 15 Oct 2019 12:44:34 GMT
Connection: close
{
    "isAgreementSigned": true
}
```

### <a name="response-examples-failure"></a><span data-ttu-id="147ce-154">Antwoordvoorbeelden (fout)</span><span class="sxs-lookup"><span data-stu-id="147ce-154">Response examples (failure)</span></span>

<span data-ttu-id="147ce-155">Mogelijk ontvangt u antwoorden die vergelijkbaar zijn met de volgende voorbeelden wanneer de ondertekeningsstatus van de indirecte reseller-Microsoft Partner-overeenkomst niet kan worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="147ce-155">You may receive responses similar to the following examples when the signing status of the indirect reseller's Microsoft Partner Agreement can't be returned.</span></span>

#### <a name="non-guid-formatted-csp-tenant-id"></a><span data-ttu-id="147ce-156">Tenant-id zonder GUID-indeling</span><span class="sxs-lookup"><span data-stu-id="147ce-156">Non-GUID formatted CSP tenant ID</span></span>

<span data-ttu-id="147ce-157">Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer de CSP-tenant-id die u aan de API hebt doorgegeven, geen GUID is.</span><span class="sxs-lookup"><span data-stu-id="147ce-157">The following example response is returned when the CSP tenant ID that you passed to the API isn't a GUID.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 105
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: rbuZl5lbAkyq8WGK.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 08:55:23 GMT
Connection: close
{
    "code": 2000,
    "description": "Tenant Id must be a GUID.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="non-numeric-mpn-id"></a><span data-ttu-id="147ce-158">Niet-numerieke MPN-id</span><span class="sxs-lookup"><span data-stu-id="147ce-158">Non-numeric MPN ID</span></span>

<span data-ttu-id="147ce-159">Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer de MPN-id (PGA/PLA) die u aan de API hebt doorgegeven, niet-numeriek is.</span><span class="sxs-lookup"><span data-stu-id="147ce-159">The following example response is returned when the MPN ID (PGA/PLA) that you passed to the API is non-numeric.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 103
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: cP5JiS4sv0GJxlJ9.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 08:58:45 GMT
Connection: close
{
    "code": 2000,
    "description": "MPN Id must be numeric.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="no-mpn-id-or-csp-tenant-id"></a><span data-ttu-id="147ce-160">Geen MPN-id of CSP-tenant-id</span><span class="sxs-lookup"><span data-stu-id="147ce-160">No MPN ID or CSP tenant ID</span></span>

<span data-ttu-id="147ce-161">Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer u geen MPN-id (PGA/PLA) of CSP-tenant-id aan de API hebt doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="147ce-161">The following example response is returned when you haven't passed an MPN ID (PGA/PLA) or CSP tenant ID to the API.</span></span> <span data-ttu-id="147ce-162">U moet een van de twee id-typen doorgeven aan de API.</span><span class="sxs-lookup"><span data-stu-id="147ce-162">You must pass one of the two ID types to the API.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 114
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: hEV736v4qk6joDMR.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 09:00:30 GMT
Connection: close
{
    "code": 2001,
    "description": "Both MPN Id and Tenant Id cannot be empty.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a><span data-ttu-id="147ce-163">Zowel MPN-id als CSP-tenant-id doorgegeven</span><span class="sxs-lookup"><span data-stu-id="147ce-163">Both MPN ID and CSP tenant ID passed</span></span>

<span data-ttu-id="147ce-164">Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer u zowel de MPN-id (PGA/PLA) als de CSP-tenant-id door geeft aan de API.</span><span class="sxs-lookup"><span data-stu-id="147ce-164">The following example response is returned when you pass both the MPN ID (PGA/PLA) and CSP tenant ID to the API.</span></span> <span data-ttu-id="147ce-165">U hoeft slechts *één van de* twee id-typen door te geven aan de API.</span><span class="sxs-lookup"><span data-stu-id="147ce-165">You must pass *only one* of the two identifier types to the API.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2000,
    "description": "Both MPN Id and Tenant Id should not be passed.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a><span data-ttu-id="147ce-166">CSP Indirect Reseller MPN-id (PGA/PLA) is ongeldig of niet gemigreerd van Partner Membership Center naar Partner Center</span><span class="sxs-lookup"><span data-stu-id="147ce-166">CSP Indirect Reseller MPN ID (PGA/PLA) is either invalid or not migrated from Partner Membership Center to Partner Center</span></span>

<span data-ttu-id="147ce-167">Het volgende voorbeeld antwoord wordt geretourneerd wanneer indirecte reseller MPN ID (PGA/PLA) doorgegeven ongeldig is of niet wordt gemigreerd van Partner Membership Center naar Partner Center.</span><span class="sxs-lookup"><span data-stu-id="147ce-167">The following example response is returned when Indirect reseller MPN ID (PGA/PLA) passed is either invalid or it is not migrated from Partner Membership Center to Partner Center.</span></span> [<span data-ttu-id="147ce-168">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="147ce-168">Learn More</span></span>](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2200,
    "description": "MPN Id 123456 is either invalid or not yet migrated to Partner Center. Please advise your reseller to migrate the reseller MPN ID to Partner Center to continue with this order.",
    "data": [
        "https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx"
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a><span data-ttu-id="147ce-169">CSP Indirect Provider regio en CSP Indirect Reseller komen niet overeen</span><span class="sxs-lookup"><span data-stu-id="147ce-169">CSP Indirect Provider region and CSP Indirect Reseller region does not match</span></span>

<span data-ttu-id="147ce-170">Het volgende voorbeeld antwoord wordt geretourneerd wanneer de regio van de indirecte reseller MPN ID (PGA/PLA) komt niet overeen met de regio van de indirecte provider.</span><span class="sxs-lookup"><span data-stu-id="147ce-170">The following example response is returned when region of Indirect reseller MPN ID (PGA/PLA) doesn't match with region of the Indirect Provider.</span></span> <span data-ttu-id="147ce-171">[Meer informatie over](/partner-center/mpa-indirect-provider-faq) CSP-regio's.</span><span class="sxs-lookup"><span data-stu-id="147ce-171">[Learn more](/partner-center/mpa-indirect-provider-faq) about CSP Regions.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2201,
    "description": "The CSP region of the MPN ID 1234567 doesn’t match the CSP region from where you are placing the order. Provide the MPN ID for the CSP region where you are placing the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq" 
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a><span data-ttu-id="147ce-172">CSP Indirect Reseller account bestaat in Partner Center maar heeft de MPA niet ondertekend</span><span class="sxs-lookup"><span data-stu-id="147ce-172">CSP Indirect Reseller account exists in Partner Center but hasn't signed the MPA</span></span>

<span data-ttu-id="147ce-173">Het volgende voorbeeld wordt geretourneerd wanneer CSP Indirect Reseller account in Partner Center MPA niet heeft ondertekend.</span><span class="sxs-lookup"><span data-stu-id="147ce-173">The following example response is returned when CSP Indirect Reseller account in Partner Center hasn't signed the MPA.</span></span> [<span data-ttu-id="147ce-174">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="147ce-174">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2203,
    "description": "MPN Id 123456 has not signed Microsoft Partner Agreement (MPA) for the CSP region where the order is being placed. Please advise your reseller to sign MPA to continue with the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a><span data-ttu-id="147ce-175">Er CSP Indirect Reseller account gekoppeld aan de opgegeven MPN-id</span><span class="sxs-lookup"><span data-stu-id="147ce-175">No CSP Indirect Reseller account is associated with the given MPN ID</span></span>

<span data-ttu-id="147ce-176">Het volgende voorbeeld wordt geretourneerd wanneer Partner Center de MPN-id (PGA/PLA) kan herkennen die is doorgegeven in de aanvraag, maar er geen CSP-inschrijving is gekoppeld aan de opgegeven MPN-id (PGA/PLA).</span><span class="sxs-lookup"><span data-stu-id="147ce-176">The following example response is returned when Partner Center can recognize the MPN ID (PGA/PLA) passed in the request but there is no CSP enrollment associated to the given MPN ID (PGA/PLA).</span></span> [<span data-ttu-id="147ce-177">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="147ce-177">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2204,
    "description": "MPN Id 123456 is not associated with a CSP Indirect Reseller account in Partner Center. Please advise your reseller to enroll into the CSP program as an indirect reseller in Partner Center.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="invalid-tenant-id"></a><span data-ttu-id="147ce-178">Ongeldige tenant-id</span><span class="sxs-lookup"><span data-stu-id="147ce-178">Invalid Tenant ID</span></span>

<span data-ttu-id="147ce-179">Het volgende voorbeeld wordt geretourneerd wanneer Partner Center geen account vindt dat is gekoppeld aan de tenant-id die in de aanvraag is doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="147ce-179">The following example response is returned when Partner Center doesn't find any account associated to the Tenant ID passed in the request.</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2205,
    "description": "Partner Center doesn't find any account associated to the Tenant ID 12345678-ACBD-1234-ABCD-123456789ABC",
    "data": [],
    "source": "PartnerFD"
}
```

#### <a name="no-mpa-found-with-the-given-tenant-id"></a><span data-ttu-id="147ce-180">Er is geen MPA gevonden met de opgegeven tenant-id</span><span class="sxs-lookup"><span data-stu-id="147ce-180">No MPA found with the given Tenant ID</span></span>

<span data-ttu-id="147ce-181">Het volgende voorbeeld wordt geretourneerd wanneer Partner Center MPA-handtekening met de opgegeven tenant-id niet kan vinden.</span><span class="sxs-lookup"><span data-stu-id="147ce-181">The following example response is returned when Partner Center can't find any MPA signature with the given Tenant ID.</span></span> [<span data-ttu-id="147ce-182">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="147ce-182">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2206,
    "description": "Parnter Center Account associated to Tenant Id 12345678-ACBD-1234-ABCD-123456789ABC hasn't signed the agreement",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```