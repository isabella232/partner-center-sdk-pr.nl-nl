---
title: Een lijst met apparaten met een beleid bijwerken
description: Een lijst met apparaten bijwerken met een configuratiebeleid voor de opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 35b35873eb253b0929bfc01662b0beb9b31d0c6b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530069"
---
# <a name="update-a-list-of-devices-with-a-policy"></a><span data-ttu-id="d58ad-103">Een lijst met apparaten met een beleid bijwerken</span><span class="sxs-lookup"><span data-stu-id="d58ad-103">Update a list of devices with a policy</span></span>

<span data-ttu-id="d58ad-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d58ad-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="d58ad-105">Een lijst met apparaten bijwerken met een configuratiebeleid voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="d58ad-105">How to update a list of devices with a configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d58ad-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d58ad-106">Prerequisites</span></span>

- <span data-ttu-id="d58ad-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d58ad-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d58ad-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="d58ad-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d58ad-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d58ad-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d58ad-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="d58ad-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d58ad-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="d58ad-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d58ad-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="d58ad-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d58ad-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="d58ad-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d58ad-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d58ad-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d58ad-115">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="d58ad-115">The policy identifier.</span></span>

- <span data-ttu-id="d58ad-116">De apparaat-id's van de apparaten die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="d58ad-116">The device identifiers of the devices to update.</span></span>

## <a name="c"></a><span data-ttu-id="d58ad-117">C\#</span><span class="sxs-lookup"><span data-stu-id="d58ad-117">C\#</span></span>

<span data-ttu-id="d58ad-118">Als u een lijst met apparaten met het opgegeven configuratiebeleid wilt bijwerken, instantieert u eerst een [List/dotnet/api/system.collections.generic.list-1) van het type [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) en voegt u het toe te passen beleid toe, zoals wordt weergegeven in het volgende codevoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="d58ad-118">To update a list of devices with the specified configuration policy, first, instantiate a [List/dotnet/api/system.collections.generic.list-1) of type [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) and add the policy to apply, as shown in the following code example.</span></span> <span data-ttu-id="d58ad-119">U hebt de beleids-id van het beleid nodig.</span><span class="sxs-lookup"><span data-stu-id="d58ad-119">You will need the policy identifier of the policy.</span></span>

<span data-ttu-id="d58ad-120">Maak vervolgens een [](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) lijst met Apparaatobjecten die moeten worden bijgewerkt met het beleid, met de apparaat-id en de lijst met het toe te passen beleid voor elk apparaat.</span><span class="sxs-lookup"><span data-stu-id="d58ad-120">Then, create a list of [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) objects to be updated with the policy, specifying the device identifier and the list that contains the policy to apply, for each device.</span></span> <span data-ttu-id="d58ad-121">Vervolgens maakt u een [**DevicePolicyUpdateRequest-object**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) en stelt u de eigenschap [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) in op de lijst met apparaatobjecten.</span><span class="sxs-lookup"><span data-stu-id="d58ad-121">Next, instantiate a [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) object and set the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of device objects.</span></span>

<span data-ttu-id="d58ad-122">Als u de aanvraag voor het bijwerken van het apparaatbeleid wilt verwerken, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="d58ad-122">To process the device policy update request, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="d58ad-123">Haal vervolgens de eigenschap [**DevicePolicy op**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) om een interface op te halen voor bewerkingen voor het verzamelen van apparaten van klanten.</span><span class="sxs-lookup"><span data-stu-id="d58ad-123">Then, retrieve the [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) property to get an interface to customer device collection operations.</span></span> <span data-ttu-id="d58ad-124">Roep ten slotte de [**updatemethode**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) aan met het object DevicePolicyUpdateRequest om de apparaten bij te werken met het beleid.</span><span class="sxs-lookup"><span data-stu-id="d58ad-124">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) method with the DevicePolicyUpdateRequest object to update the devices with the policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;
string selectedDeviceId;

// Indicate the policy to apply to the list of devices.
List<KeyValuePair<PolicyCategory, string>>
    policyToBeAdded = new List<KeyValuePair<PolicyCategory, string>>
{
    new KeyValuePair<PolicyCategory, string>
        (PolicyCategory.OOBE, selectedConfigurationPolicyId)
};

// Create a list of devices to be updated with a policy.
List<Device> devices = new List<Device>
{
    new Device
    {
        Id = selectedDeviceId,
        Policies=policyToBeAdded
    }
};

// Instantiate a DevicePolicyUpdateRequest object.
DevicePolicyUpdateRequest
    devicePolicyUpdateRequest = new DevicePolicyUpdateRequest
{
    Devices = devices
};

// Process the DevicePolicyUpdateRequest.
var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DevicePolicy.Update(devicePolicyUpdateRequest);
```

<span data-ttu-id="d58ad-125">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d58ad-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d58ad-126">**Project**: Partnercentrum-SDK Samples **Class**: UpdateDevicesPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="d58ad-126">**Project**: Partner Center SDK Samples **Class**: UpdateDevicesPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d58ad-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d58ad-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d58ad-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="d58ad-128">Request syntax</span></span>

| <span data-ttu-id="d58ad-129">Methode</span><span class="sxs-lookup"><span data-stu-id="d58ad-129">Method</span></span>    | <span data-ttu-id="d58ad-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d58ad-130">Request URI</span></span>                                                                                         |
|-----------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d58ad-131">**Patch**</span><span class="sxs-lookup"><span data-stu-id="d58ad-131">**PATCH**</span></span> | <span data-ttu-id="d58ad-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/DevicePolicyUpdates HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d58ad-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/DevicePolicyUpdates HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d58ad-133">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="d58ad-133">URI parameter</span></span>

<span data-ttu-id="d58ad-134">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="d58ad-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="d58ad-135">Naam</span><span class="sxs-lookup"><span data-stu-id="d58ad-135">Name</span></span>        | <span data-ttu-id="d58ad-136">Type</span><span class="sxs-lookup"><span data-stu-id="d58ad-136">Type</span></span>   | <span data-ttu-id="d58ad-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="d58ad-137">Required</span></span> | <span data-ttu-id="d58ad-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d58ad-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="d58ad-139">customer-id</span><span class="sxs-lookup"><span data-stu-id="d58ad-139">customer-id</span></span> | <span data-ttu-id="d58ad-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d58ad-140">string</span></span> | <span data-ttu-id="d58ad-141">Ja</span><span class="sxs-lookup"><span data-stu-id="d58ad-141">Yes</span></span>      | <span data-ttu-id="d58ad-142">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="d58ad-142">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d58ad-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d58ad-143">Request headers</span></span>

<span data-ttu-id="d58ad-144">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="d58ad-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d58ad-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d58ad-145">Request body</span></span>

<span data-ttu-id="d58ad-146">De aanvraag moet een [DevicePolicyUpdateRequest-resource](device-deployment-resources.md#devicepolicyupdaterequest) bevatten.</span><span class="sxs-lookup"><span data-stu-id="d58ad-146">The request body must contain a [DevicePolicyUpdateRequest](device-deployment-resources.md#devicepolicyupdaterequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="d58ad-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d58ad-147">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/DevicePolicyUpdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 363
Expect: 100-continue
Connection: Keep-Alive

{
    "Devices": [{
            "Id": "9993-8627-3608-6844-6369-4361-72",
            "SerialNumber": null,
            "ProductKey": null,
            "HardwareHash": null,
            "Policies": [{
                    "Key": "o_o_b_e",
                    "Value": "15a04610-9229-4e80-94e0-0e826a09c9e2"
                }
            ],
            "CreatedBy": null,
            "UploadedDate": "0001-01-01T00:00:00",
            "AllowedOperations": null,
            "Attributes": {
                "ObjectType": "Device"
            }
        }
    ],
    "Attributes": {
        "ObjectType": "DevicePolicyUpdateRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="d58ad-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d58ad-148">REST response</span></span>

<span data-ttu-id="d58ad-149">Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de status van dit batchproces op te halen.</span><span class="sxs-lookup"><span data-stu-id="d58ad-149">If successful, the response contains a **Location** header that has a URI that can be used to retrieve the status of this batch process.</span></span> <span data-ttu-id="d58ad-150">Sla deze URI op voor gebruik met andere gerelateerde REST API's.</span><span class="sxs-lookup"><span data-stu-id="d58ad-150">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d58ad-151">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="d58ad-151">Response success and error codes</span></span>

<span data-ttu-id="d58ad-152">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="d58ad-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d58ad-153">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d58ad-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d58ad-154">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="d58ad-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d58ad-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d58ad-155">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/a15f3996-620a-4404-9f1f-4c2de78de0de
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CV: rCXyd8Z/lUSxUd0P.0
MS-ServerId: 020021921
Date: Thu, 28 Sep 2017 21:33:05 GMT
```
