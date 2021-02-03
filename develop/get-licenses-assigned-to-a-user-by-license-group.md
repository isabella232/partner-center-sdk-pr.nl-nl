---
title: Licenties ophalen die aan een gebruiker zijn toegewezen per licentiegroep
description: Een lijst met door de gebruiker toegewezen licenties voor de opgegeven licentie groepen ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 28c10e3e2acb30e4110213344959a87d4ddfcffb
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767484"
---
# <a name="get-licenses-assigned-to-a-user-by-license-group"></a><span data-ttu-id="13aab-103">Licenties ophalen die aan een gebruiker zijn toegewezen per licentiegroep</span><span class="sxs-lookup"><span data-stu-id="13aab-103">Get licenses assigned to a user by license group</span></span>

<span data-ttu-id="13aab-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="13aab-104">**Applies To**</span></span>

- <span data-ttu-id="13aab-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="13aab-105">Partner Center</span></span>

<span data-ttu-id="13aab-106">Een lijst met door de gebruiker toegewezen licenties voor de opgegeven licentie groepen ophalen.</span><span class="sxs-lookup"><span data-stu-id="13aab-106">How to get a list of user assigned licenses for the specified license groups.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13aab-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="13aab-107">Prerequisites</span></span>

- <span data-ttu-id="13aab-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="13aab-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="13aab-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="13aab-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="13aab-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="13aab-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="13aab-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="13aab-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="13aab-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="13aab-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="13aab-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="13aab-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="13aab-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="13aab-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="13aab-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="13aab-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="13aab-116">Een gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="13aab-116">A user identifier.</span></span>

- <span data-ttu-id="13aab-117">Een lijst met een of meer licentie groep-id's.</span><span class="sxs-lookup"><span data-stu-id="13aab-117">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="13aab-118">C\#</span><span class="sxs-lookup"><span data-stu-id="13aab-118">C\#</span></span>

<span data-ttu-id="13aab-119">Als u wilt controleren welke licenties zijn toegewezen aan een gebruiker uit opgegeven licentie groepen, start u eerst een [list/DotNet/API/System. Collections. generic. List -1) van het type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid)en voegt u vervolgens de licentie groepen toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="13aab-119">To check which licenses are assigned to a user from specified license groups, start by instantiating a [List/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="13aab-120">Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="13aab-120">Then, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="13aab-121">Vervolgens roept u de methode [**Users. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="13aab-121">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="13aab-122">Vervolgens krijgt u een interface voor gebruikers licentie bewerkingen van de klant via de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) .</span><span class="sxs-lookup"><span data-stu-id="13aab-122">Then, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="13aab-123">Geef tot slot de lijst met licentie groepen door aan de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) om de verzameling licenties op te halen die aan de gebruiker zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="13aab-123">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="13aab-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="13aab-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="13aab-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="13aab-125">Request syntax</span></span>

| <span data-ttu-id="13aab-126">Methode</span><span class="sxs-lookup"><span data-stu-id="13aab-126">Method</span></span>  | <span data-ttu-id="13aab-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="13aab-127">Request URI</span></span>                                                                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="13aab-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="13aab-128">**GET**</span></span> | <span data-ttu-id="13aab-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenses? LicenseGroupIds = Group1 http/1.1</span><span class="sxs-lookup"><span data-stu-id="13aab-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="13aab-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="13aab-130">**GET**</span></span> | <span data-ttu-id="13aab-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenses? LicenseGroupIds = group2 http/1.1</span><span class="sxs-lookup"><span data-stu-id="13aab-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="13aab-132">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="13aab-132">**GET**</span></span> | <span data-ttu-id="13aab-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenses? LicenseGroupIds = Group1&LicenseGroupIds = group2 http/1.1</span><span class="sxs-lookup"><span data-stu-id="13aab-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="13aab-134">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="13aab-134">URI parameter</span></span>

<span data-ttu-id="13aab-135">Gebruik de volgende pad-en query parameters om de klant-, gebruikers-en licentie groepen te identificeren.</span><span class="sxs-lookup"><span data-stu-id="13aab-135">Use the following path and query parameters to identify the customer, user and license groups.</span></span>

| <span data-ttu-id="13aab-136">Naam</span><span class="sxs-lookup"><span data-stu-id="13aab-136">Name</span></span>            | <span data-ttu-id="13aab-137">Type</span><span class="sxs-lookup"><span data-stu-id="13aab-137">Type</span></span>   | <span data-ttu-id="13aab-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="13aab-138">Required</span></span> | <span data-ttu-id="13aab-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="13aab-139">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="13aab-140">klant-id</span><span class="sxs-lookup"><span data-stu-id="13aab-140">customer-id</span></span>     | <span data-ttu-id="13aab-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="13aab-141">string</span></span> | <span data-ttu-id="13aab-142">Yes</span><span class="sxs-lookup"><span data-stu-id="13aab-142">Yes</span></span>      | <span data-ttu-id="13aab-143">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="13aab-143">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="13aab-144">user-id</span><span class="sxs-lookup"><span data-stu-id="13aab-144">user-id</span></span>         | <span data-ttu-id="13aab-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="13aab-145">string</span></span> | <span data-ttu-id="13aab-146">Yes</span><span class="sxs-lookup"><span data-stu-id="13aab-146">Yes</span></span>      | <span data-ttu-id="13aab-147">Een teken reeks met een GUID-indeling waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="13aab-147">A GUID formatted string that identifies the user.</span></span>                                                                                                                                                                                                                     |
| <span data-ttu-id="13aab-148">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="13aab-148">licenseGroupIds</span></span> | <span data-ttu-id="13aab-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="13aab-149">string</span></span> | <span data-ttu-id="13aab-150">No</span><span class="sxs-lookup"><span data-stu-id="13aab-150">No</span></span>       | <span data-ttu-id="13aab-151">Een Enum-waarde die de licentie groep van de toegewezen licenties aangeeft.</span><span class="sxs-lookup"><span data-stu-id="13aab-151">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="13aab-152">Geldige waarden: group1, group2 Group1-deze groep heeft alle producten waarvan de licentie kan worden beheerd in de Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="13aab-152">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="13aab-153">Group2: deze groep heeft alleen Minecraft-product licenties.</span><span class="sxs-lookup"><span data-stu-id="13aab-153">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="13aab-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="13aab-154">Request headers</span></span>

<span data-ttu-id="13aab-155">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="13aab-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="13aab-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="13aab-156">Request body</span></span>

<span data-ttu-id="13aab-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="13aab-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="13aab-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="13aab-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="13aab-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="13aab-159">REST response</span></span>

<span data-ttu-id="13aab-160">Als dit lukt, bevat de antwoord tekst de verzameling [licentie](license-resources.md#license) resources.</span><span class="sxs-lookup"><span data-stu-id="13aab-160">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="13aab-161">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="13aab-161">Response success and error codes</span></span>

<span data-ttu-id="13aab-162">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="13aab-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="13aab-163">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="13aab-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="13aab-164">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="13aab-164">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="13aab-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="13aab-165">Response example</span></span>

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

### <a name="response-example-no-matching-licenses-found"></a><span data-ttu-id="13aab-166">Antwoord voorbeeld (er zijn geen overeenkomende licenties gevonden)</span><span class="sxs-lookup"><span data-stu-id="13aab-166">Response example (no matching licenses found)</span></span>

<span data-ttu-id="13aab-167">Als er geen overeenkomende licenties kunnen worden gevonden voor de opgegeven licentie groepen, bevat het antwoord een lege verzameling met een totalCount-element waarvan de waarde 0 is.</span><span class="sxs-lookup"><span data-stu-id="13aab-167">If no matching licenses can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

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
