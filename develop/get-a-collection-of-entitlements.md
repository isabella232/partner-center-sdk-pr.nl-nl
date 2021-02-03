---
title: Een verzameling rechten ophalen
description: Een verzameling rechten ophalen.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d2cc485429941dd2080bd285553333a01fc0ffd1
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767358"
---
# <a name="get-a-collection-of-entitlements"></a><span data-ttu-id="9020e-103">Een verzameling rechten ophalen</span><span class="sxs-lookup"><span data-stu-id="9020e-103">Get a collection of entitlements</span></span>

<span data-ttu-id="9020e-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9020e-104">**Applies To**</span></span>

- <span data-ttu-id="9020e-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9020e-105">Partner Center</span></span>

<span data-ttu-id="9020e-106">Een verzameling rechten ophalen.</span><span class="sxs-lookup"><span data-stu-id="9020e-106">How to get a collection of entitlements.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9020e-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9020e-107">Prerequisites</span></span>

- <span data-ttu-id="9020e-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9020e-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9020e-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="9020e-109">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="9020e-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9020e-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9020e-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="9020e-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9020e-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="9020e-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9020e-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="9020e-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9020e-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="9020e-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9020e-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9020e-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="9020e-116">C\#</span><span class="sxs-lookup"><span data-stu-id="9020e-116">C\#</span></span>

<span data-ttu-id="9020e-117">Als u een verzameling rechten voor een klant wilt ophalen, moet u een interface voor de [**rechten**](entitlement-resources.md#entitlement) van de gebruiker verkrijgen door de methode  [**IAggregatePartner. Customs. ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9020e-117">To get an entitlements collection for a customer, obtain an interface to [**Entitlement**](entitlement-resources.md#entitlement) operations by calling the  [**IAggregatePartner.Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="9020e-118">Vervolgens haalt u de interface op uit de eigenschap **rechten** en roept u de methode **Get ()** of **GetAsync ()** aan om de verzameling van rechten op te halen.</span><span class="sxs-lookup"><span data-stu-id="9020e-118">Then, retrieve the interface from the **Entitlements** property and call the **Get()** or **GetAsync()** method to retrieve the collection of entitlements.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;

// Get the collection of entitlements.
var entitlements = partnerOperations.Customers.ById(customerId).Entitlements.Get();
```

<span data-ttu-id="9020e-119">Als u verval datums wilt invullen voor de rechten die moeten worden opgehaald, roept u dezelfde methoden op en stelt u de optionele Booleaanse para meter **showExpiry** in op True **Get (true)** of **GetAsync (true)**.</span><span class="sxs-lookup"><span data-stu-id="9020e-119">To populate expiry dates for the entitlements to be retrieved, call the same methods above and set the optional boolean parameter **showExpiry** to true **Get(true)** or **GetAsync(true)**.</span></span> <span data-ttu-id="9020e-120">Dit geeft aan dat de rechten voor verval datums vereist zijn (indien van toepassing).</span><span class="sxs-lookup"><span data-stu-id="9020e-120">This indicates that entitlement expiry dates are required (when applicable).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9020e-121">De typen voor on-premises rechten hebben geen verval datum.</span><span class="sxs-lookup"><span data-stu-id="9020e-121">On-premise entitlement types do not have expiry dates.</span></span>

## <a name="rest-request"></a><span data-ttu-id="9020e-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9020e-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-123">Request syntax</span></span>

| <span data-ttu-id="9020e-124">Methode</span><span class="sxs-lookup"><span data-stu-id="9020e-124">Method</span></span> | <span data-ttu-id="9020e-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9020e-125">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="9020e-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9020e-126">**GET**</span></span> | <span data-ttu-id="9020e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{customerId}/Entitlements http/1.1</span><span class="sxs-lookup"><span data-stu-id="9020e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/entitlements HTTP/1.1</span></span>                            |

### <a name="uri-parameters"></a><span data-ttu-id="9020e-128">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="9020e-128">URI parameters</span></span>

<span data-ttu-id="9020e-129">Gebruik de volgende pad-en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="9020e-129">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="9020e-130">Naam</span><span class="sxs-lookup"><span data-stu-id="9020e-130">Name</span></span> | <span data-ttu-id="9020e-131">Type</span><span class="sxs-lookup"><span data-stu-id="9020e-131">Type</span></span> | <span data-ttu-id="9020e-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="9020e-132">Required</span></span> | <span data-ttu-id="9020e-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9020e-133">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="9020e-134">customerId</span><span class="sxs-lookup"><span data-stu-id="9020e-134">customerId</span></span> | <span data-ttu-id="9020e-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9020e-135">string</span></span> | <span data-ttu-id="9020e-136">Yes</span><span class="sxs-lookup"><span data-stu-id="9020e-136">Yes</span></span> | <span data-ttu-id="9020e-137">Een KlantId met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="9020e-137">A GUID formatted customerId that identifies the customer.</span></span> |
| <span data-ttu-id="9020e-138">entitlementType</span><span class="sxs-lookup"><span data-stu-id="9020e-138">entitlementType</span></span> | <span data-ttu-id="9020e-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9020e-139">string</span></span> | <span data-ttu-id="9020e-140">No</span><span class="sxs-lookup"><span data-stu-id="9020e-140">No</span></span> | <span data-ttu-id="9020e-141">Kan worden gebruikt om het type rechten op te geven dat moet worden opgehaald (**Software** of **reservedInstance** ).</span><span class="sxs-lookup"><span data-stu-id="9020e-141">Can be used to specify the type of entitlements to be retrieved (**software** or **reservedInstance** ).</span></span> <span data-ttu-id="9020e-142">Als niet is ingesteld, worden alle typen opgehaald</span><span class="sxs-lookup"><span data-stu-id="9020e-142">If not set, all types will be retrieved</span></span> |
| <span data-ttu-id="9020e-143">showExpiry</span><span class="sxs-lookup"><span data-stu-id="9020e-143">showExpiry</span></span> | <span data-ttu-id="9020e-144">booleaans</span><span class="sxs-lookup"><span data-stu-id="9020e-144">boolean</span></span> | <span data-ttu-id="9020e-145">No</span><span class="sxs-lookup"><span data-stu-id="9020e-145">No</span></span> | <span data-ttu-id="9020e-146">Optionele vlag die aangeeft of verval datums van rechten zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="9020e-146">Optional flag which indicates if entitlements expiry dates are required.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9020e-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9020e-147">Request headers</span></span>

<span data-ttu-id="9020e-148">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9020e-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9020e-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9020e-149">Request body</span></span>

<span data-ttu-id="9020e-150">Geen.</span><span class="sxs-lookup"><span data-stu-id="9020e-150">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9020e-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-151">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/entitlements HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="9020e-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9020e-152">REST response</span></span>

<span data-ttu-id="9020e-153">Als dit lukt, bevat de antwoord tekst een verzameling [rechten](entitlement-resources.md#entitlement) resources.</span><span class="sxs-lookup"><span data-stu-id="9020e-153">If successful, the response body contains a collection of [Entitlement](entitlement-resources.md#entitlement) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9020e-154">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9020e-154">Response success and error codes</span></span>

<span data-ttu-id="9020e-155">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9020e-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9020e-156">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9020e-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9020e-157">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9020e-157">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9020e-158">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9020e-158">Response example</span></span>

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

## <a name="additional-examples"></a><span data-ttu-id="9020e-159">Aanvullende voor beelden</span><span class="sxs-lookup"><span data-stu-id="9020e-159">Additional Examples</span></span>

<span data-ttu-id="9020e-160">In het volgende voor beeld ziet u hoe u een specifiek type rechten kunt ophalen naast de verval datum (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="9020e-160">The following example shows you how to retrieve a specific type of entitlements along with expiry dates (when applicable)</span></span>

### <a name="c-example"></a><span data-ttu-id="9020e-161">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="9020e-161">C\# example</span></span>

<span data-ttu-id="9020e-162">Als u een specifiek type rechten wilt ophalen, moet u de **ByEntitlementType** -interface ophalen uit de **rechten** interface en de methoden **Get ()** of **GetAsync ()** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9020e-162">To retrieve a specific type of entitlements, obtain the **ByEntitlementType** interface from the **Entitlements** interface and use the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("software").Get(true);
```

### <a name="request-example"></a><span data-ttu-id="9020e-163">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-163">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/de3dcef9-9991-459c-ac71-2903d1127414/entitlements?entitlementtype=software&showExpiry=true
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: 6517a410-67ce-4995-9bb7-116a52179f92
MS-CorrelationId: d9eb8194-9b99-4057-a2fe-98bdf05f013c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="9020e-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9020e-164">Response example</span></span>

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

<span data-ttu-id="9020e-165">In de volgende voor beelden ziet u hoe u informatie over producten en reserve ringen kunt ophalen van een recht.</span><span class="sxs-lookup"><span data-stu-id="9020e-165">The following examples show you how to retrieve information about products and reservations from an entitlement.</span></span>

### <a name="retrieve-virtual-machine-reservation-details-from-an-entitlement-by-using-sdk-v18"></a><span data-ttu-id="9020e-166">Details van de virtuele-machine reservering ophalen van een recht met behulp van SDK V 1.8</span><span class="sxs-lookup"><span data-stu-id="9020e-166">Retrieve virtual machine reservation details from an entitlement by using SDK V1.8</span></span>

### <a name="c-example"></a><span data-ttu-id="9020e-167">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="9020e-167">C\# example</span></span>

<span data-ttu-id="9020e-168">Als u meer informatie wilt ophalen over de reserve ringen van de virtuele machine van een recht, roept u de URI aan die wordt weer gegeven onder entitledArtifacts. link with artifactType = virtual_machine_reserved_instance.</span><span class="sxs-lookup"><span data-stu-id="9020e-168">To retrieve more details related to the virtual machine reservations from an entitlement, invoke the URI exposed under entitledArtifacts.link with artifactType = virtual_machine_reserved_instance .</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("VirtualMachineReservedInstance").Get();

((VirtualMachineReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.VirtualMachineReservedInstance)).Link.InvokeAsync<VirtualMachineReservedInstanceArtifactDetails>(partnerOperations)
```

### <a name="request-example"></a><span data-ttu-id="9020e-169">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-169">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/virtualmachinereservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="9020e-170">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9020e-170">Response example</span></span>

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

### <a name="retrieve-reservation-details-from-an-entitlement-by-using-sdk-v19"></a><span data-ttu-id="9020e-171">Reserverings Details ophalen van een recht met behulp van SDK V 1,9</span><span class="sxs-lookup"><span data-stu-id="9020e-171">Retrieve reservation details from an entitlement by using SDK V1.9</span></span>

### <a name="c-example"></a><span data-ttu-id="9020e-172">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="9020e-172">C\# example</span></span>

<span data-ttu-id="9020e-173">Als u meer informatie wilt ophalen over de reserve ringen van een gereserveerde instantie recht, roept u de URI aan die wordt weer gegeven in ```entitledArtifacts.link``` met ```artifactType = reservedinstance``` .</span><span class="sxs-lookup"><span data-stu-id="9020e-173">To retrieve more details related to the reservations from a reserved instance entitlement, invoke the URI exposed under ```entitledArtifacts.link``` with ```artifactType = reservedinstance```.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("ReservedInstance").Get();

((ReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.ReservedInstance)).Link.InvokeAsync<ReservedInstanceArtifactDetails>(partnerOperations);
```

### <a name="request-example"></a><span data-ttu-id="9020e-174">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9020e-174">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/reservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="9020e-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9020e-175">Response example</span></span>

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

### <a name="api-consumers"></a><span data-ttu-id="9020e-176">API-gebruikers</span><span class="sxs-lookup"><span data-stu-id="9020e-176">API Consumers</span></span>

<span data-ttu-id="9020e-177">Partners die de API gebruiken om een query uit te voeren voor gereserveerde instanties van virtuele machines-de aanvraag-URI bijwerken van **/Customers/{customerId}/Entitlements naar/Customers/{customerId}/Entitlements? entitlementType = virtualmachinereservedinstance** om achterwaartse compatibiliteit te behouden.</span><span class="sxs-lookup"><span data-stu-id="9020e-177">Partners who are using the API to query virtual machine reserved instance entitlements - Update the request URI from **/customers/{customerId}/entitlements to /customers/{customerId}/entitlements?entitlementType=virtualmachinereservedinstance** to maintain backward compatibility.</span></span> <span data-ttu-id="9020e-178">Als u een virtuele machine of Azure SQL wilt gebruiken met uitgebreid contract, werkt u de aanvraag-URI bij naar **/Customers/{customerId}/Entitlements? entitlementType = reservedinstance**.</span><span class="sxs-lookup"><span data-stu-id="9020e-178">In order to consume virtual machine or Azure SQL with enhanced contract, update the request URI to **/customers/{customerId}/entitlements?entitlementType=reservedinstance**.</span></span>
