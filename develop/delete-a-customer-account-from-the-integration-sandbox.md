---
title: Een klantaccount verwijderen uit de integratie-sandbox
description: Een klant account verwijderen uit de sandbox met Testing in Production (tip) Integration.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e3a1642c0202c174ddd4f65a6aeda2752def9176
ms.sourcegitcommit: b1ff781b67b1d322820bbcac2c583229201a8c07
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "97767402"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a><span data-ttu-id="ae2be-103">Een klantaccount verwijderen uit de integratie-sandbox</span><span class="sxs-lookup"><span data-stu-id="ae2be-103">Delete a customer account from the integration sandbox</span></span>

<span data-ttu-id="ae2be-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="ae2be-104">**Applies to:**</span></span>

- <span data-ttu-id="ae2be-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="ae2be-105">Partner Center</span></span>
- <span data-ttu-id="ae2be-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="ae2be-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="ae2be-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="ae2be-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="ae2be-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ae2be-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ae2be-109">In dit artikel wordt uitgelegd hoe u de relatie tussen de partner en het klant account verbreekt en de sandbox-integratie voor Testing in Production (tip) in de quota kunt herstellen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-109">This article explains, how to break the relationship between the partner and the customer account and regain the quota for Testing in Production (Tip) integration sandbox.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae2be-110">Wanneer u een klant account verwijdert, worden alle resources die zijn gekoppeld aan de Tenant van de klant, verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ae2be-110">When you delete a customer account, all resources associated with that customer tenant will be purged.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae2be-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ae2be-111">Prerequisites</span></span>

- <span data-ttu-id="ae2be-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ae2be-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ae2be-113">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="ae2be-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="ae2be-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ae2be-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ae2be-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="ae2be-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ae2be-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="ae2be-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ae2be-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="ae2be-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ae2be-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="ae2be-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ae2be-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ae2be-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="ae2be-120">Alle Azure Reserved Virtual Machine Instances-en software-inkoop orders moeten worden geannuleerd voordat u een klant verwijdert uit de tip Integration sandbox.</span><span class="sxs-lookup"><span data-stu-id="ae2be-120">All Azure Reserved Virtual Machine Instances and software purchase orders must be cancelled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="c"></a><span data-ttu-id="ae2be-121">C\#</span><span class="sxs-lookup"><span data-stu-id="ae2be-121">C\#</span></span>

<span data-ttu-id="ae2be-122">Een klant verwijderen uit de tip Integration sandbox:</span><span class="sxs-lookup"><span data-stu-id="ae2be-122">To delete a customer from the Tip integration sandbox:</span></span>

1. <span data-ttu-id="ae2be-123">Geef de referenties van uw tip-account door aan de methode [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) om een [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) -interface te verkrijgen voor partner bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-123">Pass your Tip account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to partner operations.</span></span>

2. <span data-ttu-id="ae2be-124">Gebruik de interface voor partner bewerkingen om de verzameling van rechten op te halen:</span><span class="sxs-lookup"><span data-stu-id="ae2be-124">Use the partner operations interface to retrieve the collection of entitlements:</span></span>

    1. <span data-ttu-id="ae2be-125">Roep de methode [**klanten. ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan bij de klant-id om de klant op te geven.</span><span class="sxs-lookup"><span data-stu-id="ae2be-125">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer.</span></span>

    2. <span data-ttu-id="ae2be-126">Roep de eigenschap **rechten** aan.</span><span class="sxs-lookup"><span data-stu-id="ae2be-126">Call the **Entitlements** property.</span></span>

    3. <span data-ttu-id="ae2be-127">Roep de methode **Get** of **GetAsync** aan om de [**rechtings**](entitlement-resources.md) verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-127">Call the **Get** or **GetAsync** method to retrieve the [**Entitlement**](entitlement-resources.md) collection.</span></span>

3. <span data-ttu-id="ae2be-128">Zorg ervoor dat alle Azure Reserved Virtual Machine Instances-en software-inkoop orders voor die klant zijn geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="ae2be-128">Make sure that all Azure Reserved Virtual Machine Instances and software purchase orders for that customer are cancelled.</span></span> <span data-ttu-id="ae2be-129">Voor elke [**recht**](entitlement-resources.md) in de verzameling:</span><span class="sxs-lookup"><span data-stu-id="ae2be-129">For each [**Entitlement**](entitlement-resources.md) in the collection:</span></span>

    1. <span data-ttu-id="ae2be-130">Gebruik het [**recht. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) voor het ophalen van een lokale kopie van de bijbehorende [order](order-resources.md#order) van de verzameling orders van de klant.</span><span class="sxs-lookup"><span data-stu-id="ae2be-130">Use the [**entitlement.ReferenceOrder.Id**](entitlement-resources.md#referenceorder) to get a local copy of the corresponding [Order](order-resources.md#order) from the customer's collection of orders.</span></span>

    2. <span data-ttu-id="ae2be-131">Stel de eigenschap [**order. status**](order-resources.md#order) in op "geannuleerd".</span><span class="sxs-lookup"><span data-stu-id="ae2be-131">Set the [**Order.Status**](order-resources.md#order) property to "Cancelled".</span></span>

    3. <span data-ttu-id="ae2be-132">Gebruik de methode **patch ()** om de volg orde bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ae2be-132">Use the **Patch()** method to update the order.</span></span>

4. <span data-ttu-id="ae2be-133">Alle orders annuleren.</span><span class="sxs-lookup"><span data-stu-id="ae2be-133">Cancel all orders.</span></span> <span data-ttu-id="ae2be-134">Het volgende code voorbeeld maakt bijvoorbeeld gebruik van een lus om elke volg orde te pollen totdat de status ' geannuleerd ' is.</span><span class="sxs-lookup"><span data-stu-id="ae2be-134">For example, the following code sample uses a loop to poll each order until its status is "Cancelled".</span></span>

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be cancelled.
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
        // Check if all the orders were cancelled.
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

5. <span data-ttu-id="ae2be-135">Zorg ervoor dat alle orders zijn geannuleerd door de **verwijderings** methode voor de klant aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-135">Make sure all orders are cancelled by calling the **Delete** method for the customer.</span></span>

<span data-ttu-id="ae2be-136">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ae2be-136">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ae2be-137">**Project**: partner centrum PartnerCenterSDK. FeaturesSamples **klasse**: DeleteCustomerFromTipAccount.cs</span><span class="sxs-lookup"><span data-stu-id="ae2be-137">**Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ae2be-138">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ae2be-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ae2be-139">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ae2be-139">Request syntax</span></span>

| <span data-ttu-id="ae2be-140">Methode</span><span class="sxs-lookup"><span data-stu-id="ae2be-140">Method</span></span>     | <span data-ttu-id="ae2be-141">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ae2be-141">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="ae2be-142">DELETE</span><span class="sxs-lookup"><span data-stu-id="ae2be-142">DELETE</span></span>     | <span data-ttu-id="ae2be-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ae2be-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="ae2be-144">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="ae2be-144">URI parameter</span></span>

<span data-ttu-id="ae2be-145">Gebruik de volgende query parameter om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-145">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="ae2be-146">Naam</span><span class="sxs-lookup"><span data-stu-id="ae2be-146">Name</span></span>                   | <span data-ttu-id="ae2be-147">Type</span><span class="sxs-lookup"><span data-stu-id="ae2be-147">Type</span></span>     | <span data-ttu-id="ae2be-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="ae2be-148">Required</span></span> | <span data-ttu-id="ae2be-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ae2be-149">Description</span></span>                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="ae2be-150">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="ae2be-150">customer-tenant-id</span></span>     | <span data-ttu-id="ae2be-151">GUID</span><span class="sxs-lookup"><span data-stu-id="ae2be-151">GUID</span></span>     | <span data-ttu-id="ae2be-152">J</span><span class="sxs-lookup"><span data-stu-id="ae2be-152">Y</span></span>        | <span data-ttu-id="ae2be-153">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="ae2be-153">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ae2be-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ae2be-154">Request headers</span></span>

<span data-ttu-id="ae2be-155">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ae2be-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ae2be-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ae2be-156">Request body</span></span>

<span data-ttu-id="ae2be-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ae2be-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ae2be-158">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="ae2be-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ae2be-159">REST response</span></span>

<span data-ttu-id="ae2be-160">Als dit lukt, retourneert deze methode een leeg antwoord.</span><span class="sxs-lookup"><span data-stu-id="ae2be-160">If successful, this method returns an empty response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ae2be-161">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="ae2be-161">Response success and error codes</span></span>

<span data-ttu-id="ae2be-162">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="ae2be-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ae2be-163">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ae2be-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ae2be-164">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="ae2be-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ae2be-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ae2be-165">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
