---
title: Licenties ophalen die aan een gebruiker zijn toegewezen per licentiegroep
description: Een lijst met door de gebruiker toegewezen licenties voor de opgegeven licentiegroepen op te halen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 54acf6f315e3062d03903a98d0c6c1946065f95e
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446000"
---
# <a name="get-licenses-assigned-to-a-user-by-license-group"></a><span data-ttu-id="7f447-103">Licenties ophalen die aan een gebruiker zijn toegewezen per licentiegroep</span><span class="sxs-lookup"><span data-stu-id="7f447-103">Get licenses assigned to a user by license group</span></span>

<span data-ttu-id="7f447-104">Een lijst met door de gebruiker toegewezen licenties voor de opgegeven licentiegroepen op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f447-104">How to get a list of user assigned licenses for the specified license groups.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f447-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7f447-105">Prerequisites</span></span>

- <span data-ttu-id="7f447-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7f447-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7f447-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7f447-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7f447-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f447-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7f447-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="7f447-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7f447-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="7f447-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7f447-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="7f447-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7f447-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="7f447-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7f447-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f447-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7f447-114">Een gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="7f447-114">A user identifier.</span></span>

- <span data-ttu-id="7f447-115">Een lijst met een of meer licentiegroep-id's.</span><span class="sxs-lookup"><span data-stu-id="7f447-115">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="7f447-116">C\#</span><span class="sxs-lookup"><span data-stu-id="7f447-116">C\#</span></span>

<span data-ttu-id="7f447-117">Als u wilt controleren welke licenties zijn toegewezen aan een gebruiker uit opgegeven licentiegroepen, begint u met het instantiëren van een [List/dotnet/api/system.collections.generic.list-1) van het type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid)en voegt u vervolgens de licentiegroepen toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="7f447-117">To check which licenses are assigned to a user from specified license groups, start by instantiating a [List/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="7f447-118">Gebruik vervolgens de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f447-118">Then, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="7f447-119">Roep vervolgens de [**methode Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f447-119">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="7f447-120">Haal vervolgens een interface op voor gebruikerslicentiebewerkingen van de klant via [**de eigenschap Licenties.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses)</span><span class="sxs-lookup"><span data-stu-id="7f447-120">Then, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="7f447-121">Geef ten slotte de lijst met licentiegroepen door aan de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) om de verzameling licenties op te halen die aan de gebruiker zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="7f447-121">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

``` csharp
// string selectedCustomerUserId;
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

// To get the group1 (Azure Active Directory (AAD)) assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group1 };
var customerUserAadAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);

// To get the group2 (Minecraft) assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group2 };
var customerUserSfbAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);

// To get both AAD and Minecraft assigned licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>(){ LicenseGroupId.Group1, LicenseGroupId.Group2 };
var customerUserBothAadAndSfbAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get(licenseGroupIds);
```

## <a name="rest-request"></a><span data-ttu-id="7f447-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f447-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7f447-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7f447-123">Request syntax</span></span>

| <span data-ttu-id="7f447-124">Methode</span><span class="sxs-lookup"><span data-stu-id="7f447-124">Method</span></span>  | <span data-ttu-id="7f447-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7f447-125">Request URI</span></span>                                                                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f447-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f447-126">**GET**</span></span> | <span data-ttu-id="7f447-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7f447-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="7f447-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f447-128">**GET**</span></span> | <span data-ttu-id="7f447-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7f447-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="7f447-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f447-130">**GET**</span></span> | <span data-ttu-id="7f447-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7f447-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="7f447-132">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="7f447-132">URI parameter</span></span>

<span data-ttu-id="7f447-133">Gebruik het volgende pad en de queryparameters om de klant-, gebruikers- en licentiegroepen te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f447-133">Use the following path and query parameters to identify the customer, user, and license groups.</span></span>

| <span data-ttu-id="7f447-134">Naam</span><span class="sxs-lookup"><span data-stu-id="7f447-134">Name</span></span>            | <span data-ttu-id="7f447-135">Type</span><span class="sxs-lookup"><span data-stu-id="7f447-135">Type</span></span>   | <span data-ttu-id="7f447-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="7f447-136">Required</span></span> | <span data-ttu-id="7f447-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f447-137">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f447-138">customer-id</span><span class="sxs-lookup"><span data-stu-id="7f447-138">customer-id</span></span>     | <span data-ttu-id="7f447-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7f447-139">string</span></span> | <span data-ttu-id="7f447-140">Ja</span><span class="sxs-lookup"><span data-stu-id="7f447-140">Yes</span></span>      | <span data-ttu-id="7f447-141">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="7f447-141">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="7f447-142">user-id</span><span class="sxs-lookup"><span data-stu-id="7f447-142">user-id</span></span>         | <span data-ttu-id="7f447-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7f447-143">string</span></span> | <span data-ttu-id="7f447-144">Ja</span><span class="sxs-lookup"><span data-stu-id="7f447-144">Yes</span></span>      | <span data-ttu-id="7f447-145">Een tekenreeks met GUID-indeling die de gebruiker identificeert.</span><span class="sxs-lookup"><span data-stu-id="7f447-145">A GUID formatted string that identifies the user.</span></span>                                                                                                                                                                                                                     |
| <span data-ttu-id="7f447-146">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="7f447-146">licenseGroupIds</span></span> | <span data-ttu-id="7f447-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7f447-147">string</span></span> | <span data-ttu-id="7f447-148">No</span><span class="sxs-lookup"><span data-stu-id="7f447-148">No</span></span>       | <span data-ttu-id="7f447-149">Een enum-waarde die de licentiegroep van de toegewezen licenties aangeeft.</span><span class="sxs-lookup"><span data-stu-id="7f447-149">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="7f447-150">Geldige waarden: Group1, Group2 Group1: deze groep heeft alle producten waarvan de licentie kan worden beheerd in de Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="7f447-150">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="7f447-151">Group2: deze groep heeft alleen Minecraft productlicenties.</span><span class="sxs-lookup"><span data-stu-id="7f447-151">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7f447-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7f447-152">Request headers</span></span>

<span data-ttu-id="7f447-153">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7f447-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7f447-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7f447-154">Request body</span></span>

<span data-ttu-id="7f447-155">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f447-155">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7f447-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f447-156">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7f447-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7f447-157">REST response</span></span>

<span data-ttu-id="7f447-158">Als dit lukt, bevat de antwoord-body de verzameling [licentieresources.](license-resources.md#license)</span><span class="sxs-lookup"><span data-stu-id="7f447-158">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7f447-159">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7f447-159">Response success and error codes</span></span>

<span data-ttu-id="7f447-160">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7f447-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7f447-161">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7f447-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7f447-162">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7f447-162">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7f447-163">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7f447-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
    "totalCount": 2,
    "items": [{
            "servicePlans": [

            ],
            "productSku": {
                "id": "984df360-9a74-4647-8cf8-696749f6247a",
                "name": "Minecraft Education Edition Faculty",
                "skuPartNumber": "CFQ7TTC0K5DR/0002",
                "licenseGroupId": "group2"
            },
            "attributes": {
                "objectType": "License"
            }
        }, {
            "servicePlans": [{
                    "displayName": "Windows Defender Advanced Threat Protection",
                    "serviceName": "WINDEFATP",
                    "id": "871d91ec-ec1a-452b-a83f-bd76c7d770ef",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }, {
                    "displayName": "Windows 10 Enterprise E3",
                    "serviceName": "WIN10_PRO_ENT_SUB",
                    "id": "21b439ba-a0ca-424f-a6cc-52f954a5b111",
                    "capabilityStatus": "Assigned",
                    "targetType": "User"
                }
            ],
            "productSku": {
                "id": "1e7e1070-8ccb-4aca-b470-d7cb538cb07e",
                "name": "Windows 10 Enterprise E5",
                "skuPartNumber": "WIN_ENT_E5",
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

### <a name="response-example-no-matching-licenses-found"></a><span data-ttu-id="7f447-164">Voorbeeld van een antwoord (er zijn geen overeenkomende licenties gevonden)</span><span class="sxs-lookup"><span data-stu-id="7f447-164">Response example (no matching licenses found)</span></span>

<span data-ttu-id="7f447-165">Als er geen overeenkomende licenties kunnen worden gevonden voor de opgegeven licentiegroepen, bevat het antwoord een lege verzameling met een totalCount-element waarvan de waarde 0 is.</span><span class="sxs-lookup"><span data-stu-id="7f447-165">If no matching licenses can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 71
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CV: q05xrhUeDUKvhrFt.0
MS-ServerId: 030020525
Date: Fri, 09 Jun 2017 22:50:11 GMT

{
    "totalCount": 0,
    "items": [],
    "attributes": {
        "objectType": "Collection"
    }
}
```
