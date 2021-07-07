---
title: Licenties ophalen die aan een gebruiker zijn toegewezen
description: Meer informatie over het gebruik Partner Center API's om een lijst op te halen met licenties die zijn toegewezen aan een gebruiker binnen een klantaccount.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a51fc4493e2476107206b03be66004d030e2aa47
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974060"
---
# <a name="get-licenses-assigned-to-a-user-within-a-customer-account"></a><span data-ttu-id="f070f-103">Licenties krijgen die zijn toegewezen aan een gebruiker binnen een klantaccount</span><span class="sxs-lookup"><span data-stu-id="f070f-103">Get licenses assigned to a user within a customer account</span></span>

<span data-ttu-id="f070f-104">Een lijst met licenties op te halen die zijn toegewezen aan een gebruiker binnen een klantaccount.</span><span class="sxs-lookup"><span data-stu-id="f070f-104">How to get a list of licenses assigned to a user within a customer account.</span></span> <span data-ttu-id="f070f-105">De hier weergegeven voorbeelden retourneren licenties die zijn toegewezen vanuit group1, de standaardlicentiegroep die licenties vertegenwoordigt die worden beheerd door Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f070f-105">The examples shown here return licenses assigned from group1, the default license group that represents licenses managed by Azure Active Directory.</span></span> <span data-ttu-id="f070f-106">Zie Licenties die zijn toegewezen aan een gebruiker op licentiegroep om licenties toe te laten uit opgegeven [licentiegroepen.](get-licenses-assigned-to-a-user-by-license-group.md)</span><span class="sxs-lookup"><span data-stu-id="f070f-106">To get licenses assigned from specified license groups, see [Get licenses assigned to a user by license group](get-licenses-assigned-to-a-user-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f070f-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f070f-107">Prerequisites</span></span>

- <span data-ttu-id="f070f-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f070f-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f070f-109">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="f070f-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="f070f-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f070f-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f070f-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="f070f-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f070f-112">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="f070f-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f070f-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="f070f-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f070f-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="f070f-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f070f-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f070f-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f070f-116">Een gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="f070f-116">A user identifier.</span></span>

## <a name="c"></a><span data-ttu-id="f070f-117">C\#</span><span class="sxs-lookup"><span data-stu-id="f070f-117">C\#</span></span>

<span data-ttu-id="f070f-118">Als u wilt controleren welke licenties zijn toegewezen aan een gebruiker uit de standaardlicentiegroep group1, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f070f-118">To check which licenses are assigned to a user from the default group1 license group, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="f070f-119">Roep vervolgens de [**methode Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f070f-119">Then call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="f070f-120">Haal vervolgens een interface op voor gebruikerslicentiebewerkingen van de klant via [**de eigenschap**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) Licenties.</span><span class="sxs-lookup"><span data-stu-id="f070f-120">Next, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="f070f-121">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) of [**getAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) aan om de verzameling licenties op te halen die aan de gebruiker zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f070f-121">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

``` csharp
// string selectedCustomerUserId;
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get();
```

<span data-ttu-id="f070f-122">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="f070f-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="f070f-123">**Project**: Partnercentrum-SDK Samples **Class**: CustomerUserAssignedLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="f070f-123">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignedLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="f070f-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f070f-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f070f-125">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="f070f-125">Request syntax</span></span>

| <span data-ttu-id="f070f-126">Methode</span><span class="sxs-lookup"><span data-stu-id="f070f-126">Method</span></span>  | <span data-ttu-id="f070f-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f070f-127">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f070f-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="f070f-128">**GET**</span></span> | <span data-ttu-id="f070f-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f070f-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="f070f-130">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="f070f-130">URI parameter</span></span>

<span data-ttu-id="f070f-131">Gebruik de volgende padparameters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f070f-131">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="f070f-132">Naam</span><span class="sxs-lookup"><span data-stu-id="f070f-132">Name</span></span>        | <span data-ttu-id="f070f-133">Type</span><span class="sxs-lookup"><span data-stu-id="f070f-133">Type</span></span>   | <span data-ttu-id="f070f-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="f070f-134">Required</span></span> | <span data-ttu-id="f070f-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f070f-135">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="f070f-136">customer-id</span><span class="sxs-lookup"><span data-stu-id="f070f-136">customer-id</span></span> | <span data-ttu-id="f070f-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f070f-137">string</span></span> | <span data-ttu-id="f070f-138">Ja</span><span class="sxs-lookup"><span data-stu-id="f070f-138">Yes</span></span>      | <span data-ttu-id="f070f-139">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="f070f-139">A GUID formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="f070f-140">user-id</span><span class="sxs-lookup"><span data-stu-id="f070f-140">user-id</span></span>     | <span data-ttu-id="f070f-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f070f-141">string</span></span> | <span data-ttu-id="f070f-142">Ja</span><span class="sxs-lookup"><span data-stu-id="f070f-142">Yes</span></span>      | <span data-ttu-id="f070f-143">Een tekenreeks met GUID-indeling die de gebruiker identificeert.</span><span class="sxs-lookup"><span data-stu-id="f070f-143">A GUID formatted string that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="f070f-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f070f-144">Request headers</span></span>

<span data-ttu-id="f070f-145">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="f070f-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f070f-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f070f-146">Request body</span></span>

<span data-ttu-id="f070f-147">Geen.</span><span class="sxs-lookup"><span data-stu-id="f070f-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f070f-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f070f-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 68e50b00-e1ff-422a-a293-158617463d41
MS-CorrelationId: 813f15b3-eb18-4709-b2f3-668d62babf91
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="f070f-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f070f-149">REST response</span></span>

<span data-ttu-id="f070f-150">Als dit lukt, bevat de antwoord-body de verzameling [licentieresources.](license-resources.md#license)</span><span class="sxs-lookup"><span data-stu-id="f070f-150">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f070f-151">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="f070f-151">Response success and error codes</span></span>

<span data-ttu-id="f070f-152">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="f070f-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f070f-153">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f070f-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f070f-154">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="f070f-154">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f070f-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f070f-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 3883
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 813f15b3-eb18-4709-b2f3-668d62babf91
MS-RequestId: 68e50b00-e1ff-422a-a293-158617463d41
MS-CV: WYkHYMfWTUajFosK.0
MS-ServerId: 020021921
Date: Fri, 09 Jun 2017 00:29:24 GMT

{
    "totalCount": 1,
    "items": [{
            "servicePlans": [{
                    "displayName": "Azure Information Protection Premium P1",
                    "serviceName": "RMS_S_PREMIUM",
                    "id": "6c57d4b6-3b23-47a5-9bc9-69f17b4947b3",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Intune A Direct",
                    "serviceName": "INTUNE_A",
                    "id": "c1ec4a95-1f05-45b3-a911-aa3fa01094f5",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Active Directory Rights",
                    "serviceName": "RMS_S_ENTERPRISE",
                    "id": "bea4c11e-220a-4e6d-8eb8-8ea15d019f90",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Azure Active Directory Premium P1",
                    "serviceName": "AAD_PREMIUM",
                    "id": "41781fb2-bc02-4b7c-bd55-b576c07bb09d",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Multi-Factor Authentication",
                    "serviceName": "MFA_PREMIUM",
                    "id": "8a256a2b-b617-496d-b51b-e76466e88db0",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }
            ],
            "productSku": {
                "id": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e",
                "name": "Enterprise Mobility + Security E3",
                "skuPartNumber": "EMS",
                "licenseGroupId": "group1"
            },
            "attributes": {
                "objectType": "License"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```