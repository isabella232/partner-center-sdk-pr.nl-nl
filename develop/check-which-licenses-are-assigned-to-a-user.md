---
title: Licenties ophalen die aan een gebruiker zijn toegewezen
description: Meer informatie over het gebruik van partner Center-Api's voor het ophalen van een lijst met licenties die zijn toegewezen aan een gebruiker binnen een klant account.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b754ba4ecba7067f78c6868b387bac0190bfd230
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767626"
---
# <a name="get-licenses-assigned-to-a-user-within-a-customer-account"></a><span data-ttu-id="3480a-103">Licenties ophalen die zijn toegewezen aan een gebruiker binnen een klant account</span><span class="sxs-lookup"><span data-stu-id="3480a-103">Get licenses assigned to a user within a customer account</span></span>

<span data-ttu-id="3480a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="3480a-104">**Applies to:**</span></span>

- <span data-ttu-id="3480a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3480a-105">Partner Center</span></span>

<span data-ttu-id="3480a-106">Een lijst weer geven met licenties die zijn toegewezen aan een gebruiker binnen een klant account.</span><span class="sxs-lookup"><span data-stu-id="3480a-106">How to get a list of licenses assigned to a user within a customer account.</span></span> <span data-ttu-id="3480a-107">De voor beelden die hier worden weer gegeven, retour neren licenties die zijn toegewezen via Group1, de standaard licentie groep die de licenties vertegenwoordigt die worden beheerd door Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3480a-107">The examples shown here return licenses assigned from group1, the default license group that represents licenses managed by Azure Active Directory.</span></span> <span data-ttu-id="3480a-108">Zie [licenties die zijn toegewezen aan een gebruiker ophalen per licentie groep](get-licenses-assigned-to-a-user-by-license-group.md)voor meer informatie over licenties die zijn toegewezen via opgegeven licentie groepen.</span><span class="sxs-lookup"><span data-stu-id="3480a-108">To get licenses assigned from specified license groups, see [Get licenses assigned to a user by license group](get-licenses-assigned-to-a-user-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3480a-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3480a-109">Prerequisites</span></span>

- <span data-ttu-id="3480a-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3480a-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3480a-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3480a-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="3480a-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3480a-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3480a-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="3480a-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3480a-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="3480a-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3480a-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="3480a-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3480a-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="3480a-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3480a-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3480a-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="3480a-118">Een gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="3480a-118">A user identifier.</span></span>

## <a name="c"></a><span data-ttu-id="3480a-119">C\#</span><span class="sxs-lookup"><span data-stu-id="3480a-119">C\#</span></span>

<span data-ttu-id="3480a-120">Als u wilt controleren welke licenties zijn toegewezen aan een gebruiker uit de standaard Group1-licentie groep, gebruikt u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3480a-120">To check which licenses are assigned to a user from the default group1 license group, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="3480a-121">Roep vervolgens de gebruikers [**. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode aan met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3480a-121">Then call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="3480a-122">Vervolgens krijgt u een interface voor gebruikers licentie bewerkingen van de klant via de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) .</span><span class="sxs-lookup"><span data-stu-id="3480a-122">Next, get an interface to customer user license operations from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenses) property.</span></span> <span data-ttu-id="3480a-123">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) aan om de verzameling licenties op te halen die aan de gebruiker zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="3480a-123">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicensecollection.getasync) method to retrieve the collection of licenses assigned to the user.</span></span>

``` csharp
// string selectedCustomerUserId;
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserAssignedLicenses = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Licenses.Get();
```

<span data-ttu-id="3480a-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="3480a-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="3480a-125">**Project**: Partner Center SDK-voor beelden **klasse**: CustomerUserAssignedLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="3480a-125">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignedLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3480a-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3480a-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3480a-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3480a-127">Request syntax</span></span>

| <span data-ttu-id="3480a-128">Methode</span><span class="sxs-lookup"><span data-stu-id="3480a-128">Method</span></span>  | <span data-ttu-id="3480a-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3480a-129">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3480a-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="3480a-130">**GET**</span></span> | <span data-ttu-id="3480a-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenses http/1.1</span><span class="sxs-lookup"><span data-stu-id="3480a-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenses HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="3480a-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="3480a-132">URI parameter</span></span>

<span data-ttu-id="3480a-133">Gebruik de volgende para meters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3480a-133">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="3480a-134">Naam</span><span class="sxs-lookup"><span data-stu-id="3480a-134">Name</span></span>        | <span data-ttu-id="3480a-135">Type</span><span class="sxs-lookup"><span data-stu-id="3480a-135">Type</span></span>   | <span data-ttu-id="3480a-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="3480a-136">Required</span></span> | <span data-ttu-id="3480a-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3480a-137">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="3480a-138">klant-id</span><span class="sxs-lookup"><span data-stu-id="3480a-138">customer-id</span></span> | <span data-ttu-id="3480a-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3480a-139">string</span></span> | <span data-ttu-id="3480a-140">Yes</span><span class="sxs-lookup"><span data-stu-id="3480a-140">Yes</span></span>      | <span data-ttu-id="3480a-141">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="3480a-141">A GUID formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="3480a-142">user-id</span><span class="sxs-lookup"><span data-stu-id="3480a-142">user-id</span></span>     | <span data-ttu-id="3480a-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3480a-143">string</span></span> | <span data-ttu-id="3480a-144">Yes</span><span class="sxs-lookup"><span data-stu-id="3480a-144">Yes</span></span>      | <span data-ttu-id="3480a-145">Een teken reeks met een GUID-indeling waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="3480a-145">A GUID formatted string that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="3480a-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3480a-146">Request headers</span></span>

<span data-ttu-id="3480a-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3480a-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3480a-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3480a-148">Request body</span></span>

<span data-ttu-id="3480a-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="3480a-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3480a-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3480a-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/482e2152-4b49-48ec-b715-823365ce3d4c/licenses HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 68e50b00-e1ff-422a-a293-158617463d41
MS-CorrelationId: 813f15b3-eb18-4709-b2f3-668d62babf91
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="3480a-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3480a-151">REST response</span></span>

<span data-ttu-id="3480a-152">Als dit lukt, bevat de antwoord tekst de verzameling [licentie](license-resources.md#license) resources.</span><span class="sxs-lookup"><span data-stu-id="3480a-152">If successful, the response body contains the collection of [License](license-resources.md#license) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3480a-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3480a-153">Response success and error codes</span></span>

<span data-ttu-id="3480a-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3480a-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3480a-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3480a-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3480a-156">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3480a-156">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3480a-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3480a-157">Response example</span></span>

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