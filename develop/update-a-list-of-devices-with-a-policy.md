---
title: Een lijst met apparaten met een beleid bijwerken
description: Een lijst met apparaten bijwerken met een configuratie beleid voor de opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04c2ef33116335db40bd2934dc7e33d57f015097
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767512"
---
# <a name="update-a-list-of-devices-with-a-policy"></a><span data-ttu-id="fc8d3-103">Een lijst met apparaten met een beleid bijwerken</span><span class="sxs-lookup"><span data-stu-id="fc8d3-103">Update a list of devices with a policy</span></span>

<span data-ttu-id="fc8d3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="fc8d3-104">**Applies To**</span></span>

- <span data-ttu-id="fc8d3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fc8d3-105">Partner Center</span></span>
- <span data-ttu-id="fc8d3-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="fc8d3-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="fc8d3-107">Een lijst met apparaten bijwerken met een configuratie beleid voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-107">How to update a list of devices with a configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc8d3-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fc8d3-108">Prerequisites</span></span>

- <span data-ttu-id="fc8d3-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d3-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fc8d3-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fc8d3-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fc8d3-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fc8d3-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fc8d3-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fc8d3-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fc8d3-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="fc8d3-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fc8d3-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fc8d3-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="fc8d3-117">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-117">The policy identifier.</span></span>

- <span data-ttu-id="fc8d3-118">De apparaat-id's van de apparaten die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-118">The device identifiers of the devices to update.</span></span>

## <a name="c"></a><span data-ttu-id="fc8d3-119">C\#</span><span class="sxs-lookup"><span data-stu-id="fc8d3-119">C\#</span></span>

<span data-ttu-id="fc8d3-120">Als u een lijst met apparaten met het opgegeven configuratie beleid wilt bijwerken, maakt u eerst een [list/DotNet/API/System. Collections. generic. List -1) van het type [KeyValuePair/DotNet/API/System. Collections. generic. KeyValuePair -2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)String) en voegt u het toe te passen beleid, zoals wordt weer gegeven in het volgende code voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-120">To update a list of devices with the specified configuration policy, first, instantiate a [List/dotnet/api/system.collections.generic.list-1) of type [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) and add the policy to apply, as shown in the following code example.</span></span> <span data-ttu-id="fc8d3-121">U hebt de beleids-id van het beleid nodig.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-121">You will need the policy identifier of the policy.</span></span>

<span data-ttu-id="fc8d3-122">Maak vervolgens een lijst met [**device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) -objecten die moeten worden bijgewerkt met het beleid, waarbij de apparaat-id en de lijst die het toe te passen beleid bevat, voor elk apparaat worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-122">Then, create a list of [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) objects to be updated with the policy, specifying the device identifier and the list that contains the policy to apply, for each device.</span></span> <span data-ttu-id="fc8d3-123">Maak vervolgens een exemplaar van een [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) -object en stel de eigenschap [**devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) in op de lijst met apparaatgroepen.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-123">Next, instantiate a [**DevicePolicyUpdateRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) object and set the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of device objects.</span></span>

<span data-ttu-id="fc8d3-124">Als u de aanvraag voor het bijwerken van het apparaatbeleid wilt verwerken, roept u de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-124">To process the device policy update request, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="fc8d3-125">Vervolgens haalt u de eigenschap [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) op om een interface op te halen voor het verzamelen van klant apparaten.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-125">Then, retrieve the [**DevicePolicy**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) property to get an interface to customer device collection operations.</span></span> <span data-ttu-id="fc8d3-126">Roep tot slot de methode [**Update**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) aan met het object DevicePolicyUpdateRequest om de apparaten bij te werken met het beleid.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-126">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) method with the DevicePolicyUpdateRequest object to update the devices with the policy.</span></span>

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

<span data-ttu-id="fc8d3-127">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d3-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fc8d3-128">**Project**: Partner Center SDK-voor beelden **klasse**: UpdateDevicesPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="fc8d3-128">**Project**: Partner Center SDK Samples **Class**: UpdateDevicesPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="fc8d3-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fc8d3-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fc8d3-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fc8d3-130">Request syntax</span></span>

| <span data-ttu-id="fc8d3-131">Methode</span><span class="sxs-lookup"><span data-stu-id="fc8d3-131">Method</span></span>    | <span data-ttu-id="fc8d3-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fc8d3-132">Request URI</span></span>                                                                                         |
|-----------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fc8d3-133">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="fc8d3-133">**PATCH**</span></span> | <span data-ttu-id="fc8d3-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/DevicePolicyUpdates http/1.1</span><span class="sxs-lookup"><span data-stu-id="fc8d3-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/DevicePolicyUpdates HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="fc8d3-135">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="fc8d3-135">URI parameter</span></span>

<span data-ttu-id="fc8d3-136">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-136">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="fc8d3-137">Naam</span><span class="sxs-lookup"><span data-stu-id="fc8d3-137">Name</span></span>        | <span data-ttu-id="fc8d3-138">Type</span><span class="sxs-lookup"><span data-stu-id="fc8d3-138">Type</span></span>   | <span data-ttu-id="fc8d3-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="fc8d3-139">Required</span></span> | <span data-ttu-id="fc8d3-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fc8d3-140">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="fc8d3-141">klant-id</span><span class="sxs-lookup"><span data-stu-id="fc8d3-141">customer-id</span></span> | <span data-ttu-id="fc8d3-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fc8d3-142">string</span></span> | <span data-ttu-id="fc8d3-143">Yes</span><span class="sxs-lookup"><span data-stu-id="fc8d3-143">Yes</span></span>      | <span data-ttu-id="fc8d3-144">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-144">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fc8d3-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fc8d3-145">Request headers</span></span>

<span data-ttu-id="fc8d3-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d3-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fc8d3-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fc8d3-147">Request body</span></span>

<span data-ttu-id="fc8d3-148">De aanvraag tekst moet een [DevicePolicyUpdateRequest](device-deployment-resources.md#devicepolicyupdaterequest) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-148">The request body must contain a [DevicePolicyUpdateRequest](device-deployment-resources.md#devicepolicyupdaterequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="fc8d3-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fc8d3-149">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="fc8d3-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fc8d3-150">REST response</span></span>

<span data-ttu-id="fc8d3-151">Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de status van dit batch proces op te halen.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-151">If successful, the response contains a **Location** header that has a URI that can be used to retrieve the status of this batch process.</span></span> <span data-ttu-id="fc8d3-152">Sla deze URI op voor gebruik met andere verwante REST Api's.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-152">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fc8d3-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="fc8d3-153">Response success and error codes</span></span>

<span data-ttu-id="fc8d3-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fc8d3-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fc8d3-156">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fc8d3-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fc8d3-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fc8d3-157">Response example</span></span>

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
