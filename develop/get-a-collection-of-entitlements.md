---
title: Een verzameling rechten ophalen
description: Een verzameling rechten ophalen.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7bb8d3aefb11fae0af4bce790b41598d935de57c
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906423"
---
# <a name="get-a-collection-of-entitlements"></a><span data-ttu-id="a91ae-103">Een verzameling rechten ophalen</span><span class="sxs-lookup"><span data-stu-id="a91ae-103">Get a collection of entitlements</span></span>

<span data-ttu-id="a91ae-104">Een verzameling rechten ophalen.</span><span class="sxs-lookup"><span data-stu-id="a91ae-104">How to get a collection of entitlements.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a91ae-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a91ae-105">Prerequisites</span></span>

- <span data-ttu-id="a91ae-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a91ae-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a91ae-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="a91ae-107">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="a91ae-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a91ae-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a91ae-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="a91ae-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a91ae-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="a91ae-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a91ae-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="a91ae-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a91ae-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="a91ae-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a91ae-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a91ae-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="a91ae-114">C\#</span><span class="sxs-lookup"><span data-stu-id="a91ae-114">C\#</span></span>

<span data-ttu-id="a91ae-115">Als u een verzameling rechten voor een [](entitlement-resources.md#entitlement) klant wilt ophalen, verkrijgt u een interface voor Rechtenbewerkingen door de methode [**IAggregatePartner.Customers.ById() aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) te roepen met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="a91ae-115">To get an entitlements collection for a customer, obtain an interface to [**Entitlement**](entitlement-resources.md#entitlement) operations by calling the  [**IAggregatePartner.Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="a91ae-116">Haal vervolgens de interface op uit de eigenschap **Entitlements** en roep de methode **Get()** of **GetAsync()** aan om de verzameling rechten op te halen.</span><span class="sxs-lookup"><span data-stu-id="a91ae-116">Then, retrieve the interface from the **Entitlements** property and call the **Get()** or **GetAsync()** method to retrieve the collection of entitlements.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;

// Get the collection of entitlements.
var entitlements = partnerOperations.Customers.ById(customerId).Entitlements.Get();
```

<span data-ttu-id="a91ae-117">Als u de vervaldatums wilt in vullen voor de rechten die moeten worden opgehaald, roept u dezelfde bovenstaande methoden aan en stelt u de optionele Booleaanse parameter **showExpiry** in op true **Get(true)** of **GetAsync(true)**.</span><span class="sxs-lookup"><span data-stu-id="a91ae-117">To populate expiry dates for the entitlements to be retrieved, call the same methods above and set the optional boolean parameter **showExpiry** to true **Get(true)** or **GetAsync(true)**.</span></span> <span data-ttu-id="a91ae-118">Dit geeft aan dat vervaldatums voor rechten vereist zijn (indien van toepassing).</span><span class="sxs-lookup"><span data-stu-id="a91ae-118">This indicates that entitlement expiry dates are required (when applicable).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a91ae-119">On-premises rechtentypen hebben geen vervaldatums.</span><span class="sxs-lookup"><span data-stu-id="a91ae-119">On-premise entitlement types do not have expiry dates.</span></span>

## <a name="rest-request"></a><span data-ttu-id="a91ae-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a91ae-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a91ae-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="a91ae-121">Request syntax</span></span>

| <span data-ttu-id="a91ae-122">Methode</span><span class="sxs-lookup"><span data-stu-id="a91ae-122">Method</span></span> | <span data-ttu-id="a91ae-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a91ae-123">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="a91ae-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a91ae-124">**GET**</span></span> | <span data-ttu-id="a91ae-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/entitlements HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a91ae-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/entitlements HTTP/1.1</span></span>                            |

### <a name="uri-parameters"></a><span data-ttu-id="a91ae-126">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="a91ae-126">URI parameters</span></span>

<span data-ttu-id="a91ae-127">Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="a91ae-127">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="a91ae-128">Naam</span><span class="sxs-lookup"><span data-stu-id="a91ae-128">Name</span></span> | <span data-ttu-id="a91ae-129">Type</span><span class="sxs-lookup"><span data-stu-id="a91ae-129">Type</span></span> | <span data-ttu-id="a91ae-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="a91ae-130">Required</span></span> | <span data-ttu-id="a91ae-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a91ae-131">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="a91ae-132">customerId</span><span class="sxs-lookup"><span data-stu-id="a91ae-132">customerId</span></span> | <span data-ttu-id="a91ae-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a91ae-133">string</span></span> | <span data-ttu-id="a91ae-134">Ja</span><span class="sxs-lookup"><span data-stu-id="a91ae-134">Yes</span></span> | <span data-ttu-id="a91ae-135">Een in GUID opgemaakte customerId die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="a91ae-135">A GUID formatted customerId that identifies the customer.</span></span> |
| <span data-ttu-id="a91ae-136">entitlementType</span><span class="sxs-lookup"><span data-stu-id="a91ae-136">entitlementType</span></span> | <span data-ttu-id="a91ae-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a91ae-137">string</span></span> | <span data-ttu-id="a91ae-138">No</span><span class="sxs-lookup"><span data-stu-id="a91ae-138">No</span></span> | <span data-ttu-id="a91ae-139">Kan worden gebruikt om het type rechten op te geven dat moet worden opgehaald (**software** of **reservedInstance).**</span><span class="sxs-lookup"><span data-stu-id="a91ae-139">Can be used to specify the type of entitlements to be retrieved (**software** or **reservedInstance** ).</span></span> <span data-ttu-id="a91ae-140">Als dit niet is ingesteld, worden alle typen opgehaald</span><span class="sxs-lookup"><span data-stu-id="a91ae-140">If not set, all types will be retrieved</span></span> |
| <span data-ttu-id="a91ae-141">showExpiry</span><span class="sxs-lookup"><span data-stu-id="a91ae-141">showExpiry</span></span> | <span data-ttu-id="a91ae-142">booleaans</span><span class="sxs-lookup"><span data-stu-id="a91ae-142">boolean</span></span> | <span data-ttu-id="a91ae-143">Nee</span><span class="sxs-lookup"><span data-stu-id="a91ae-143">No</span></span> | <span data-ttu-id="a91ae-144">Optionele vlag die aangeeft of er vervaldatums voor rechten zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="a91ae-144">Optional flag that indicates if entitlements expiry dates are required.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a91ae-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a91ae-145">Request headers</span></span>

<span data-ttu-id="a91ae-146">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="a91ae-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a91ae-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a91ae-147">Request body</span></span>

<span data-ttu-id="a91ae-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="a91ae-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a91ae-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a91ae-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/entitlements HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="a91ae-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a91ae-150">REST response</span></span>

<span data-ttu-id="a91ae-151">Als dit lukt, bevat de antwoord-body een verzameling [rechtenresources.](entitlement-resources.md#entitlement)</span><span class="sxs-lookup"><span data-stu-id="a91ae-151">If successful, the response body contains a collection of [Entitlement](entitlement-resources.md#entitlement) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a91ae-152">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="a91ae-152">Response success and error codes</span></span>

<span data-ttu-id="a91ae-153">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="a91ae-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a91ae-154">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a91ae-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a91ae-155">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="a91ae-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a91ae-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a91ae-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 103778
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: EjFdw8fCpkKyMyza.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:42:51 GMT

{
  "totalCount": 2,
  "items": [
    {
      "includedEntitlements": [],
      "referenceOrder": {
        "id": "KaJ8XvkKc_GoNZOUyjVaRJalTBN5MWdV1",
        "lineItemId": "0"
      },
      "productId": "DZH318Z0BQ3W",
      "quantity": 1,
      "entitledArtifacts": [
        {
          "link": {
            "uri": "/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/reservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336",
            "method": "GET",
            "headers": []
          },
          "resourceId": "ebf2e74b-630e-4a09-857d-a1f6c6351336",
          "artifactType": "reservedinstance"
        }
      ],
      "skuId": "007J",
      "entitlementType": "reservedinstance"
      "dynamicAttributes": {
               "reservationType": "virtualmachines"
        }
    },
    {
      "includedEntitlements": [
        {
          "includedEntitlements": [],
          "referenceOrder": {
              "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
              "lineItemId": "0"
          },
          "productId": "DG7GMGF0DWTJ",
          "quantity": 1,
          "entitledArtifacts": [],
          "skuId": "0001",
          "entitlementType": "software"
        },
        {
          "includedEntitlements": [],
          "referenceOrder": {
            "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
            "lineItemId": "0"
          },
            "productId": "DG7GMGF0DWLG",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0002",
            "entitlementType": "software"
          }
        ],
        "referenceOrder": {
          "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
          "lineItemId": "0"
        },
        "productId": "DG7GMGF0DWTK",
        "quantity": 1,
        "entitledArtifacts": [],
        "skuId": "0002",
        "entitlementType": "software"
    }
  ],
  "attributes": {
    "objectType": "Collection"
  }
}
```

## <a name="additional-examples"></a><span data-ttu-id="a91ae-157">Aanvullende voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a91ae-157">Additional Examples</span></span>

<span data-ttu-id="a91ae-158">In het volgende voorbeeld ziet u hoe u een specifiek type rechten kunt ophalen, samen met vervaldatums (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="a91ae-158">The following example shows you how to retrieve a specific type of entitlements along with expiry dates (when applicable)</span></span>

### <a name="c-example"></a><span data-ttu-id="a91ae-159">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a91ae-159">C\# example</span></span>

<span data-ttu-id="a91ae-160">Als u een specifiek type rechten wilt ophalen, haalt u de **ByEntitlementType-interface** op via de interface **Rechten** en gebruikt u de methoden **Get()** of **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="a91ae-160">To retrieve a specific type of entitlements, obtain the **ByEntitlementType** interface from the **Entitlements** interface and use the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("software").Get(true);
```

### <a name="request-example"></a><span data-ttu-id="a91ae-161">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a91ae-161">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/de3dcef9-9991-459c-ac71-2903d1127414/entitlements?entitlementtype=software&showExpiry=true
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: 6517a410-67ce-4995-9bb7-116a52179f92
MS-CorrelationId: d9eb8194-9b99-4057-a2fe-98bdf05f013c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a91ae-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a91ae-162">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1791
Content-Type: application/json; charset=utf-8
MS-CorrelationId: d9eb8194-9b99-4057-a2fe-98bdf05f013c
MS-RequestId: 6517a410-67ce-4995-9bb7-116a52179f92
X-Locale: en-US
MS-CV: yD+4LBKePUSp/vqJ.0
MS-ServerId: 000002
Date: Mon, 28 Jan 2019 18:31:43 GMT

{
    "totalCount": 2,
    "items": [
        {
            "includedEntitlements": [
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "0",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWM2",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0001",
                    "entitlementType": "software"
                },
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "0",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWMK",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0001",
                    "entitlementType": "software"
                }
            ],
            "referenceOrder": {
                "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                "lineItemId": "0",
                "alternateId": "8f3af3dea1ea"
            },
            "productId": "DG7GMGF0DWM3",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0002",
            "entitlementType": "software"
        },
        {
            "includedEntitlements": [
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "1",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWV1",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0002",
                    "entitlementType": "software"
                },
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "1",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWV2",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0002",
                    "entitlementType": "software"
                }
            ],
            "referenceOrder": {
                "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                "lineItemId": "1",
                "alternateId": "8f3af3dea1ea"
            },
            "productId": "DG7GMGF0DWBQ",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0003",
            "entitlementType": "software",
            "expiryDate": "2022-01-28T00:00:00Z"
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

<span data-ttu-id="a91ae-163">In de volgende voorbeelden ziet u hoe u informatie over producten en reserveringen kunt ophalen van een recht.</span><span class="sxs-lookup"><span data-stu-id="a91ae-163">The following examples show you how to retrieve information about products and reservations from an entitlement.</span></span>

### <a name="retrieve-virtual-machine-reservation-details-from-an-entitlement-by-using-sdk-v18"></a><span data-ttu-id="a91ae-164">Reserveringsgegevens van virtuele machines ophalen uit een recht met behulp van SDK V1.8</span><span class="sxs-lookup"><span data-stu-id="a91ae-164">Retrieve virtual machine reservation details from an entitlement by using SDK V1.8</span></span>

### <a name="c-example"></a><span data-ttu-id="a91ae-165">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a91ae-165">C\# example</span></span>

<span data-ttu-id="a91ae-166">Als u meer details wilt ophalen met betrekking tot de reserveringen voor virtuele machines van een recht, roept u de URI aan die wordt blootgesteld onder entitledArtifacts.link met artifactType = virtual_machine_reserved_instance.</span><span class="sxs-lookup"><span data-stu-id="a91ae-166">To retrieve more details related to the virtual machine reservations from an entitlement, invoke the URI exposed under entitledArtifacts.link with artifactType = virtual_machine_reserved_instance.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("VirtualMachineReservedInstance").Get();

((VirtualMachineReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.VirtualMachineReservedInstance)).Link.InvokeAsync<VirtualMachineReservedInstanceArtifactDetails>(partnerOperations)
```

### <a name="request-example"></a><span data-ttu-id="a91ae-167">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a91ae-167">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/virtualmachinereservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a91ae-168">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a91ae-168">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 368
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: yrdTGsZ7IU2v9okv.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:45:14 GMT

{
  "type": "virtual_machine_reserved_instance",
  "virtualMachineReservations": [
    {
      "reservationId": "99f320db-c029-4c1b-a157-dad76e4481b6",
      "scopeType": "Shared",
      "quantity": 1,
      "expiryDateTime": "2019-02-23T00:00:00",
      "effectiveDateTime": "2018-02-23T18:15:24.6724884Z",
      "provisioningState": "Created"
    }
  ]
}
```

### <a name="retrieve-reservation-details-from-an-entitlement-by-using-sdk-v19"></a><span data-ttu-id="a91ae-169">Reserveringsgegevens ophalen van een recht met behulp van SDK V1.9</span><span class="sxs-lookup"><span data-stu-id="a91ae-169">Retrieve reservation details from an entitlement by using SDK V1.9</span></span>

### <a name="c-example"></a><span data-ttu-id="a91ae-170">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a91ae-170">C\# example</span></span>

<span data-ttu-id="a91ae-171">Als u meer details wilt ophalen met betrekking tot de reserveringen van een gereserveerde instantie, roept u de URI aan die wordt blootgesteld ```entitledArtifacts.link``` onder met ```artifactType = reservedinstance``` .</span><span class="sxs-lookup"><span data-stu-id="a91ae-171">To retrieve more details related to the reservations from a reserved instance entitlement, invoke the URI exposed under ```entitledArtifacts.link``` with ```artifactType = reservedinstance```.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("ReservedInstance").Get();

((ReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.ReservedInstance)).Link.InvokeAsync<ReservedInstanceArtifactDetails>(partnerOperations);
```

### <a name="request-example"></a><span data-ttu-id="a91ae-172">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a91ae-172">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/reservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a91ae-173">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a91ae-173">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 368
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: yrdTGsZ7IU2v9okv.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:45:14 GMT

{
  "type": "reservedinstance",
  "virtualMachineReservations": [
    {
      "reservationId": "99f320db-c029-4c1b-a157-dad76e4481b6",
      "scopeType": "Shared",
      "quantity": 1,
      "expiryDateTime": "2019-02-23T00:00:00",
      "effectiveDateTime": "2018-02-23T18:15:24.6724884Z",
      "provisioningState": "Created"
    }
  ]
}
```

### <a name="api-consumers"></a><span data-ttu-id="a91ae-174">API-consumenten</span><span class="sxs-lookup"><span data-stu-id="a91ae-174">API Consumers</span></span>

<span data-ttu-id="a91ae-175">Partners die de API gebruiken om de rechten van gereserveerde instanties van virtuele machines op te vragen: werk de aanvraag-URI bij **van /customers/{customerId}/entitlements?entitlementType=virtualmachinereservedinstance** om achterwaartse compatibiliteit te behouden.</span><span class="sxs-lookup"><span data-stu-id="a91ae-175">Partners who are using the API to query virtual machine reserved instance entitlements - Update the request URI from **/customers/{customerId}/entitlements to /customers/{customerId}/entitlements?entitlementType=virtualmachinereservedinstance** to maintain backward compatibility.</span></span> <span data-ttu-id="a91ae-176">Als u een virtuele machine of Azure SQL wilt gebruiken met een uitgebreid contract, moet u de aanvraag-URI bijwerken naar **/customers/{customerId}/entitlements?entitlementType=reservedinstance.**</span><span class="sxs-lookup"><span data-stu-id="a91ae-176">To consume virtual machine or Azure SQL with enhanced contract, update the request URI to **/customers/{customerId}/entitlements?entitlementType=reservedinstance**.</span></span>
