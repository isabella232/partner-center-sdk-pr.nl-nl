---
title: De ondertekening status van de micro soft partner overeenkomst van een indirecte wederverkoper verifiëren
description: U kunt de AgreementStatus-API gebruiken om te controleren of een indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fa9480424eccc933bc9c28c3879a195fbd5f2bb1
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711889"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a><span data-ttu-id="1dc88-103">De ondertekening status van de micro soft partner overeenkomst van een indirecte wederverkoper verifiëren</span><span class="sxs-lookup"><span data-stu-id="1dc88-103">Verify an indirect reseller's Microsoft Partner Agreement signing status</span></span>

<span data-ttu-id="1dc88-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="1dc88-104">**Applies to:**</span></span>

- <span data-ttu-id="1dc88-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1dc88-105">Partner Center</span></span>
- <span data-ttu-id="1dc88-106">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1dc88-106">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1dc88-107">U kunt controleren of een indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend met behulp van hun Microsoft Partner Network (MPN)-ID (PGA/PLA) of de Tenant-ID van de Cloud Solution Provider (CSP) (micro soft-ID).</span><span class="sxs-lookup"><span data-stu-id="1dc88-107">You can verify whether an indirect reseller has signed the Microsoft Partner Agreement using their Microsoft Partner Network (MPN) ID (PGA/PLA) or Cloud Solution Provider (CSP) tenant ID (Microsoft ID).</span></span> <span data-ttu-id="1dc88-108">U kunt een van deze id's gebruiken om de status van de micro soft Partner Agreement Sign te controleren met behulp van de **AgreementStatus** -API.</span><span class="sxs-lookup"><span data-stu-id="1dc88-108">You can use one of these identifiers to check the Microsoft Partner Agreement signing status using the **AgreementStatus** API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1dc88-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1dc88-109">Prerequisites</span></span>

- <span data-ttu-id="1dc88-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1dc88-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1dc88-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1dc88-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="1dc88-112">De MPN-ID (PGA/PLA) of de CSP-Tenant-ID (micro soft-ID) van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="1dc88-112">The MPN ID (PGA/PLA) or the CSP tenant ID (Microsoft ID) of the indirect reseller.</span></span> <span data-ttu-id="1dc88-113">*U moet een van deze twee id's gebruiken.*</span><span class="sxs-lookup"><span data-stu-id="1dc88-113">*You must use one of these two identifiers.*</span></span>

## <a name="c"></a><span data-ttu-id="1dc88-114">C\#</span><span class="sxs-lookup"><span data-stu-id="1dc88-114">C\#</span></span>

<span data-ttu-id="1dc88-115">De handtekening status van de micro soft-partner overeenkomst van een indirecte wederverkoper ophalen:</span><span class="sxs-lookup"><span data-stu-id="1dc88-115">To get the Microsoft Partner Agreement signature status of an indirect reseller:</span></span>

1. <span data-ttu-id="1dc88-116">Gebruik uw verzameling **IAggregatePartner. compliance** om de eigenschap **AgreementSignatureStatus** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="1dc88-116">Use your **IAggregatePartner.Compliance** collection to call the **AgreementSignatureStatus** property.</span></span>

2. <span data-ttu-id="1dc88-117">Roep de methode [**Get ()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="1dc88-117">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- <span data-ttu-id="1dc88-118">Voor beeld: **[console test-app](console-test-app.md)**</span><span class="sxs-lookup"><span data-stu-id="1dc88-118">Sample: **[Console test app](console-test-app.md)**</span></span>
- <span data-ttu-id="1dc88-119">Project: **PartnerCenterSDK. FeaturesSamples**</span><span class="sxs-lookup"><span data-stu-id="1dc88-119">Project: **PartnerCenterSDK.FeaturesSamples**</span></span>
- <span data-ttu-id="1dc88-120">Klasse: **GetAgreementSignatureStatus. cs**</span><span class="sxs-lookup"><span data-stu-id="1dc88-120">Class: **GetAgreementSignatureStatus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="1dc88-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1dc88-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1dc88-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1dc88-122">Request syntax</span></span>

| <span data-ttu-id="1dc88-123">Methode</span><span class="sxs-lookup"><span data-stu-id="1dc88-123">Method</span></span> | <span data-ttu-id="1dc88-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1dc88-124">Request URI</span></span> |
| ------ | ----------- |
| <span data-ttu-id="1dc88-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="1dc88-125">**GET**</span></span> | <span data-ttu-id="1dc88-126">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus? mpnId = {mpnId} &tenantId = {tenantId}</span><span class="sxs-lookup"><span data-stu-id="1dc88-126">*[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="1dc88-127">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="1dc88-127">URI parameters</span></span>

<span data-ttu-id="1dc88-128">U moet een van de volgende twee query parameters opgeven om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="1dc88-128">You must provide one of the following two query parameters to identify the partner.</span></span> <span data-ttu-id="1dc88-129">Als u niet een van deze twee query parameters opgeeft, ontvangt u een fout melding van **400 (ongeldige aanvraag)** .</span><span class="sxs-lookup"><span data-stu-id="1dc88-129">If you don't provide one of these two query parameters, you will receive a **400 (Bad request)** error.</span></span>

| <span data-ttu-id="1dc88-130">Naam</span><span class="sxs-lookup"><span data-stu-id="1dc88-130">Name</span></span> | <span data-ttu-id="1dc88-131">Type</span><span class="sxs-lookup"><span data-stu-id="1dc88-131">Type</span></span> | <span data-ttu-id="1dc88-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="1dc88-132">Required</span></span> | <span data-ttu-id="1dc88-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1dc88-133">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="1dc88-134">**MpnId**</span><span class="sxs-lookup"><span data-stu-id="1dc88-134">**MpnId**</span></span> | <span data-ttu-id="1dc88-135">int</span><span class="sxs-lookup"><span data-stu-id="1dc88-135">int</span></span> | <span data-ttu-id="1dc88-136">Nee</span><span class="sxs-lookup"><span data-stu-id="1dc88-136">No</span></span> | <span data-ttu-id="1dc88-137">Een Microsoft Partner Network-ID (PGA/PLA) waarmee de indirecte wederverkoper wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="1dc88-137">A Microsoft Partner Network ID (PGA/PLA) that identifies the indirect reseller.</span></span> |
| <span data-ttu-id="1dc88-138">**Tenant-ID**</span><span class="sxs-lookup"><span data-stu-id="1dc88-138">**TenantId**</span></span> | <span data-ttu-id="1dc88-139">GUID</span><span class="sxs-lookup"><span data-stu-id="1dc88-139">GUID</span></span> | <span data-ttu-id="1dc88-140">Nee</span><span class="sxs-lookup"><span data-stu-id="1dc88-140">No</span></span> | <span data-ttu-id="1dc88-141">Een micro soft-ID waarmee het CSP-account van de indirecte wederverkoper wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="1dc88-141">A Microsoft ID that identifies the CSP account of the indirect reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1dc88-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1dc88-142">Request headers</span></span>

<span data-ttu-id="1dc88-143">Zie de REST van het [Partner Center](headers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1dc88-143">For more information, see [Partner Center REST](headers.md).</span></span>

### <a name="request-examples"></a><span data-ttu-id="1dc88-144">Aanvraag voorbeelden</span><span class="sxs-lookup"><span data-stu-id="1dc88-144">Request examples</span></span>

#### <a name="request-using-mpn-id-pgapla"></a><span data-ttu-id="1dc88-145">Aanvraag met behulp van MPN-ID (PGA/PLA)</span><span class="sxs-lookup"><span data-stu-id="1dc88-145">Request using MPN ID (PGA/PLA)</span></span>

<span data-ttu-id="1dc88-146">In het volgende voor beeld wordt de ID van de micro soft-partner overeenkomst voor de indirecte wederverkoper opgehaald met behulp van de beMicrosoft Partner Networkcode van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="1dc88-146">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's Microsoft Partner Network ID.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a><span data-ttu-id="1dc88-147">Aanvraag met de Tenant-ID van CSP</span><span class="sxs-lookup"><span data-stu-id="1dc88-147">Request using CSP tenant ID</span></span>

<span data-ttu-id="1dc88-148">In het volgende voor beeld wordt de ID van de micro soft Partner Agreement Sign van de indirecte wederverkoper opgehaald met behulp van de CSP-Tenant van de indirecte wederverkoper (micro soft-ID).</span><span class="sxs-lookup"><span data-stu-id="1dc88-148">The following example request gets the indirect reseller's Microsoft Partner Agreement signing status using the indirect reseller's CSP tenant ID (Microsoft ID).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="1dc88-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1dc88-149">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1dc88-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1dc88-150">Response success and error codes</span></span>

<span data-ttu-id="1dc88-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1dc88-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1dc88-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1dc88-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1dc88-153">Zie [rest-fout partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1dc88-153">For the full list, see [Partner Center REST error](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="1dc88-154">Voor beeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="1dc88-154">Response example (success)</span></span>

<span data-ttu-id="1dc88-155">Het volgende voor beeld van een antwoord geeft aan of de indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend.</span><span class="sxs-lookup"><span data-stu-id="1dc88-155">The following example response successfully returns whether the indirect reseller has signed the Microsoft Partner Agreement.</span></span>

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

### <a name="response-examples-failure"></a><span data-ttu-id="1dc88-156">Voor beelden van antwoorden (fout)</span><span class="sxs-lookup"><span data-stu-id="1dc88-156">Response examples (failure)</span></span>

<span data-ttu-id="1dc88-157">U ontvangt mogelijk antwoorden die vergelijkbaar zijn met de volgende voor beelden wanneer de handtekening status van de micro soft-partner overeenkomst van de indirecte wederverkoper niet kan worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1dc88-157">You may receive responses similar to the following examples when the signing status of the indirect reseller's Microsoft Partner Agreement can't be returned.</span></span>

#### <a name="non-guid-formatted-csp-tenant-id"></a><span data-ttu-id="1dc88-158">Niet-GUID geformatteerde CSP-Tenant-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-158">Non-GUID formatted CSP tenant ID</span></span>

<span data-ttu-id="1dc88-159">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de CSP-Tenant-ID die u aan de API hebt door gegeven, geen GUID is.</span><span class="sxs-lookup"><span data-stu-id="1dc88-159">The following example response is returned when the CSP tenant ID that you passed to the API isn't a GUID.</span></span>

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

#### <a name="non-numeric-mpn-id"></a><span data-ttu-id="1dc88-160">Niet-numerieke MPN-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-160">Non-numeric MPN ID</span></span>

<span data-ttu-id="1dc88-161">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de MPN-ID (PGA/PLA) die u aan de API hebt door gegeven, niet numeriek is.</span><span class="sxs-lookup"><span data-stu-id="1dc88-161">The following example response is returned when the MPN ID (PGA/PLA) that you passed to the API is non-numeric.</span></span>

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

#### <a name="no-mpn-id-or-csp-tenant-id"></a><span data-ttu-id="1dc88-162">Geen MPN-ID of CSP-Tenant-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-162">No MPN ID or CSP tenant ID</span></span>

<span data-ttu-id="1dc88-163">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer u een MPN-ID (PGA/PLA) of CSP-Tenant-ID niet hebt door gegeven aan de API.</span><span class="sxs-lookup"><span data-stu-id="1dc88-163">The following example response is returned when you haven't passed an MPN ID (PGA/PLA) or CSP tenant ID to the API.</span></span> <span data-ttu-id="1dc88-164">U moet een van de twee ID-typen door geven aan de API.</span><span class="sxs-lookup"><span data-stu-id="1dc88-164">You must pass one of the two ID types to the API.</span></span>

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

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a><span data-ttu-id="1dc88-165">Zowel de MPN-ID als de CSP-Tenant-ID zijn door gegeven</span><span class="sxs-lookup"><span data-stu-id="1dc88-165">Both MPN ID and CSP tenant ID passed</span></span>

<span data-ttu-id="1dc88-166">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer u zowel de MPN-ID (PGA/PLA) als de CSP-Tenant-ID door geven aan de API.</span><span class="sxs-lookup"><span data-stu-id="1dc88-166">The following example response is returned when you pass both the MPN ID (PGA/PLA) and CSP tenant ID to the API.</span></span> <span data-ttu-id="1dc88-167">U moet *slechts één* van de twee id-typen door geven aan de API.</span><span class="sxs-lookup"><span data-stu-id="1dc88-167">You must pass *only one* of the two identifier types to the API.</span></span>

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

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a><span data-ttu-id="1dc88-168">De MPN-id (PGA/PLA) van de CSP indirecte dealer is ongeldig of niet gemigreerd van het partner lidmaatschaps centrum naar het partner centrum</span><span class="sxs-lookup"><span data-stu-id="1dc88-168">CSP Indirect Reseller MPN Id (PGA/PLA) is either invalid or not migrated from Partner Membership Center to Partner Center</span></span>

<span data-ttu-id="1dc88-169">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer een door gegeven indirecte wederverkoper MPN-ID (PGA/PLA) ongeldig is of niet is gemigreerd van het Partner Membership Center naar het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="1dc88-169">The following example response is returned when Indirect reseller MPN ID (PGA/PLA) passed is either invalid or it is not migrated from Partner Membership Center to Partner Center.</span></span> [<span data-ttu-id="1dc88-170">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="1dc88-170">Learn More</span></span>](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

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

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a><span data-ttu-id="1dc88-171">De SSP-regio en de CSP indirecte wederverkoper-regio komen niet overeen</span><span class="sxs-lookup"><span data-stu-id="1dc88-171">CSP Indirect Provider region and CSP Indirect Reseller region does not match</span></span>

<span data-ttu-id="1dc88-172">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de regio van de indirecte reseller MPN-ID (PGA/PLA) niet overeenkomt met de regio van de indirecte provider.</span><span class="sxs-lookup"><span data-stu-id="1dc88-172">The following example response is returned when region of Indirect reseller MPN ID (PGA/PLA) doesn't match with region of the Indirect Provider.</span></span> <span data-ttu-id="1dc88-173">Meer [informatie](/partner-center/mpa-indirect-provider-faq) over CSP-regio's.</span><span class="sxs-lookup"><span data-stu-id="1dc88-173">[Learn more](/partner-center/mpa-indirect-provider-faq) about CSP Regions.</span></span>

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

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a><span data-ttu-id="1dc88-174">Het account voor de indirecte dealer van CSP bestaat in het partner centrum, maar heeft de MPA niet ondertekend</span><span class="sxs-lookup"><span data-stu-id="1dc88-174">CSP Indirect Reseller account exists in Partner Center but hasn't signed the MPA</span></span>

<span data-ttu-id="1dc88-175">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het CSP indirecte reseller-account in het partner centrum de MPA niet heeft ondertekend.</span><span class="sxs-lookup"><span data-stu-id="1dc88-175">The following example response is returned when CSP Indirect Reseller account in Partner Center hasn't signed the MPA.</span></span> [<span data-ttu-id="1dc88-176">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="1dc88-176">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a><span data-ttu-id="1dc88-177">Er is geen indirect-dealer account voor CSP gekoppeld aan de opgegeven MPN-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-177">No CSP Indirect Reseller account is associated with the given MPN ID</span></span>

<span data-ttu-id="1dc88-178">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het partner centrum de MPN-ID (PGA/PLA) kan herkennen die in de aanvraag is gegeven, maar er geen CSP-registratie is gekoppeld aan de opgegeven MPN-ID (PGA/PLA).</span><span class="sxs-lookup"><span data-stu-id="1dc88-178">The following example response is returned when Partner Center can recognize the MPN ID (PGA/PLA) passed in the request but there is no CSP enrollment associated to the given MPN ID (PGA/PLA).</span></span> [<span data-ttu-id="1dc88-179">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="1dc88-179">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="invalid-tenant-id"></a><span data-ttu-id="1dc88-180">Ongeldige Tenant-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-180">Invalid Tenant ID</span></span>

<span data-ttu-id="1dc88-181">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het partner centrum geen account vindt dat is gekoppeld aan de Tenant-ID die in de aanvraag is door gegeven.</span><span class="sxs-lookup"><span data-stu-id="1dc88-181">The following example response is returned when Partner Center doesn't find any account associated to the Tenant ID passed in the request.</span></span>

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

#### <a name="no-mpa-found-with-the-given-tenant-id"></a><span data-ttu-id="1dc88-182">Er is geen MPA gevonden met de opgegeven Tenant-ID</span><span class="sxs-lookup"><span data-stu-id="1dc88-182">No MPA found with the given Tenant ID</span></span>

<span data-ttu-id="1dc88-183">Het volgende voor beeld van een antwoord wordt geretourneerd wanneer in het partner centrum geen MPA-hand tekening met de opgegeven Tenant-ID is gevonden.</span><span class="sxs-lookup"><span data-stu-id="1dc88-183">The following example response is returned when Partner Center can't find any MPA signature with the given Tenant ID.</span></span> [<span data-ttu-id="1dc88-184">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="1dc88-184">Learn More</span></span>](/partner-center/mpa-indirect-provider-faq)

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