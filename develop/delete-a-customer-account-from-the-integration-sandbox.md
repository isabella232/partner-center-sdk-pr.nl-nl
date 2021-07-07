---
title: Een klantaccount verwijderen uit de integratie-sandbox
description: Een klantaccount verwijderen uit de sandbox voor Testing in Production -integratie (Tip).
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b9d9e44ac9c40bd4e3c7e1a9e04253f853dfd96c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973125"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a><span data-ttu-id="95af9-103">Een klantaccount verwijderen uit de integratie-sandbox</span><span class="sxs-lookup"><span data-stu-id="95af9-103">Delete a customer account from the integration sandbox</span></span>

<span data-ttu-id="95af9-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="95af9-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="95af9-105">In dit artikel wordt uitgelegd hoe u de relatie tussen de partner en het klantaccount verbreekt en het quotum voor de sandbox voor Testing in Production -integratie (Tip) opnieuw kunt krijgen.</span><span class="sxs-lookup"><span data-stu-id="95af9-105">This article explains, how to break the relationship between the partner and the customer account and regain the quota for Testing in Production (Tip) integration sandbox.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95af9-106">Wanneer u een klantaccount verwijdert, worden alle resources verwijderd die zijn gekoppeld aan die klantten tenant.</span><span class="sxs-lookup"><span data-stu-id="95af9-106">When you delete a customer account, all resources associated with that customer tenant will be purged.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95af9-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="95af9-107">Prerequisites</span></span>

- <span data-ttu-id="95af9-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="95af9-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="95af9-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="95af9-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="95af9-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95af9-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="95af9-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="95af9-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="95af9-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="95af9-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="95af9-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="95af9-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="95af9-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="95af9-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="95af9-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="95af9-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="95af9-116">Alle Azure Reserved Virtual Machine Instances en software-aankooporders moeten worden geannuleerd voordat u een klant uit de Sandbox voor tipintegratie kunt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="95af9-116">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="c"></a><span data-ttu-id="95af9-117">C\#</span><span class="sxs-lookup"><span data-stu-id="95af9-117">C\#</span></span>

<span data-ttu-id="95af9-118">Een klant verwijderen uit de Sandbox voor Tip-integratie:</span><span class="sxs-lookup"><span data-stu-id="95af9-118">To delete a customer from the Tip integration sandbox:</span></span>

1. <span data-ttu-id="95af9-119">Geef uw Tip-accountreferenties door aan [**de methode CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) om een [**IPartner-interface**](/dotnet/api/microsoft.store.partnercenter.ipartner) voor partnerbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="95af9-119">Pass your Tip account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to partner operations.</span></span>

2. <span data-ttu-id="95af9-120">Gebruik de interface voor partnerbewerkingen om de verzameling rechten op te halen:</span><span class="sxs-lookup"><span data-stu-id="95af9-120">Use the partner operations interface to retrieve the collection of entitlements:</span></span>

    1. <span data-ttu-id="95af9-121">Roep de [**methode Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant op te geven.</span><span class="sxs-lookup"><span data-stu-id="95af9-121">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer.</span></span>

    2. <span data-ttu-id="95af9-122">Roep de **eigenschap Rechten aan.**</span><span class="sxs-lookup"><span data-stu-id="95af9-122">Call the **Entitlements** property.</span></span>

    3. <span data-ttu-id="95af9-123">Roep de **methode Get** of **GetAsync aan** om de rechtenverzameling op [**te**](entitlement-resources.md) halen.</span><span class="sxs-lookup"><span data-stu-id="95af9-123">Call the **Get** or **GetAsync** method to retrieve the [**Entitlement**](entitlement-resources.md) collection.</span></span>

3. <span data-ttu-id="95af9-124">Zorg ervoor dat alle Azure Reserved Virtual Machine Instances- en softwareaankooporders voor die klant worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="95af9-124">Make sure that all Azure Reserved Virtual Machine Instances and software purchase orders for that customer are canceled.</span></span> <span data-ttu-id="95af9-125">Voor elk [**recht**](entitlement-resources.md) in de verzameling:</span><span class="sxs-lookup"><span data-stu-id="95af9-125">For each [**Entitlement**](entitlement-resources.md) in the collection:</span></span>

    1. <span data-ttu-id="95af9-126">Gebruik het [**recht. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) lokale kopie van de bijbehorende order [ophalen](order-resources.md#order) uit de verzameling orders van de klant.</span><span class="sxs-lookup"><span data-stu-id="95af9-126">Use the [**entitlement.ReferenceOrder.Id**](entitlement-resources.md#referenceorder) to get a local copy of the corresponding [Order](order-resources.md#order) from the customer's collection of orders.</span></span>

    2. <span data-ttu-id="95af9-127">Stel de [**eigenschap Order.Status**](order-resources.md#order) in op Geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="95af9-127">Set the [**Order.Status**](order-resources.md#order) property to "Cancelled".</span></span>

    3. <span data-ttu-id="95af9-128">Gebruik de **methode Patch()** om de volgorde bij te werken.</span><span class="sxs-lookup"><span data-stu-id="95af9-128">Use the **Patch()** method to update the order.</span></span>

4. <span data-ttu-id="95af9-129">Annuleer alle orders.</span><span class="sxs-lookup"><span data-stu-id="95af9-129">Cancel all orders.</span></span> <span data-ttu-id="95af9-130">In het volgende codevoorbeeld wordt bijvoorbeeld een lus gebruikt om elke bestelling te peilen totdat de status 'Geannuleerd' is.</span><span class="sxs-lookup"><span data-stu-id="95af9-130">For example, the following code sample uses a loop to poll each order until its status is "Cancelled".</span></span>

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be canceled.
    ResourceCollection<Entitlement> entitlements = tipAccountPartnerOperations.Customers.ById(customerTenantId).Entitlements.Get();

    // Cancel all orders
    foreach (var entitlement in entitlements)
    {
        var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
        order.Status = "Cancelled";
        order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(order.Id).Patch(order);
    }

    // Keep polling until the status of all orders is "Cancelled".
    bool proceed = true;
    do
    {
        // Check if all the orders were canceled.
        foreach (var entitlement in entitlements)
        {
            var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
            if (!order.Status.Equals("Cancelled", StringComparison.OrdinalIgnoreCase))
            {
                proceed = false;
            }
        }

        // Wait for a few seconds.
        Thread.Sleep(5000);
    }
    while (proceed == false);

    tipAccountPartnerOperations.Customers.ById(customerTenantId).Delete();
    ```

5. <span data-ttu-id="95af9-131">Zorg ervoor dat alle orders worden geannuleerd door de methode **Delete voor** de klant aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="95af9-131">Make sure all orders are canceled by calling the **Delete** method for the customer.</span></span>

<span data-ttu-id="95af9-132">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="95af9-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="95af9-133">**Project:** Partner Center PartnerCenterSDK.FeaturesSamples-klasse: DeleteCustomerFromTipAccount.cs</span><span class="sxs-lookup"><span data-stu-id="95af9-133">**Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="95af9-134">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="95af9-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="95af9-135">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="95af9-135">Request syntax</span></span>

| <span data-ttu-id="95af9-136">Methode</span><span class="sxs-lookup"><span data-stu-id="95af9-136">Method</span></span>     | <span data-ttu-id="95af9-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="95af9-137">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="95af9-138">DELETE</span><span class="sxs-lookup"><span data-stu-id="95af9-138">DELETE</span></span>     | <span data-ttu-id="95af9-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="95af9-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="95af9-140">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="95af9-140">URI parameter</span></span>

<span data-ttu-id="95af9-141">Gebruik de volgende queryparameter om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="95af9-141">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="95af9-142">Naam</span><span class="sxs-lookup"><span data-stu-id="95af9-142">Name</span></span>                   | <span data-ttu-id="95af9-143">Type</span><span class="sxs-lookup"><span data-stu-id="95af9-143">Type</span></span>     | <span data-ttu-id="95af9-144">Vereist</span><span class="sxs-lookup"><span data-stu-id="95af9-144">Required</span></span> | <span data-ttu-id="95af9-145">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="95af9-145">Description</span></span>                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="95af9-146">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="95af9-146">customer-tenant-id</span></span>     | <span data-ttu-id="95af9-147">GUID</span><span class="sxs-lookup"><span data-stu-id="95af9-147">GUID</span></span>     | <span data-ttu-id="95af9-148">J</span><span class="sxs-lookup"><span data-stu-id="95af9-148">Y</span></span>        | <span data-ttu-id="95af9-149">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="95af9-149">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="95af9-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="95af9-150">Request headers</span></span>

<span data-ttu-id="95af9-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="95af9-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="95af9-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="95af9-152">Request body</span></span>

<span data-ttu-id="95af9-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="95af9-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="95af9-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="95af9-154">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="95af9-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="95af9-155">REST response</span></span>

<span data-ttu-id="95af9-156">Als dit lukt, retourneert deze methode een leeg antwoord.</span><span class="sxs-lookup"><span data-stu-id="95af9-156">If successful, this method returns an empty response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="95af9-157">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="95af9-157">Response success and error codes</span></span>

<span data-ttu-id="95af9-158">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="95af9-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="95af9-159">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="95af9-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="95af9-160">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="95af9-160">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="95af9-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="95af9-161">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
