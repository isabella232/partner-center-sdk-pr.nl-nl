---
title: Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de acceptatie van klanten kunt bevestigen van de Microsoft Cloud overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: d91f70cbd8bc9b8622b8d41ab9e601e2aee2cfab
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767547"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a><span data-ttu-id="19fda-103">Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="19fda-103">Get confirmation of customer acceptance of Microsoft Cloud Agreement</span></span>

<span data-ttu-id="19fda-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="19fda-104">**Applies To**</span></span>

- <span data-ttu-id="19fda-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="19fda-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="19fda-106">De bron van de **overeenkomst** wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="19fda-106">The **Agreement** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="19fda-107">Het is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="19fda-107">It isn't applicable to:</span></span>
>
> - <span data-ttu-id="19fda-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="19fda-108">Partner Center operated by 21Vianet</span></span>
> - <span data-ttu-id="19fda-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="19fda-109">Partner Center for Microsoft Cloud Germany</span></span>
> - <span data-ttu-id="19fda-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="19fda-110">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19fda-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="19fda-111">Prerequisites</span></span>

- <span data-ttu-id="19fda-112">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,9 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="19fda-112">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="19fda-113">Als u de Java SDK van het partner centrum gebruikt, is versie 1,8 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="19fda-113">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="19fda-114">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="19fda-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="19fda-115">Dit scenario ondersteunt alleen app + gebruikers verificatie.</span><span class="sxs-lookup"><span data-stu-id="19fda-115">This scenario supports only supports app + user authentication.</span></span>

- <span data-ttu-id="19fda-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="19fda-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="19fda-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="19fda-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="19fda-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="19fda-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="19fda-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="19fda-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="19fda-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="19fda-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="19fda-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="19fda-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net-version-14-or-newer"></a><span data-ttu-id="19fda-122">.NET (versie 1,4 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="19fda-122">.NET (version 1.4 or newer)</span></span>

<span data-ttu-id="19fda-123">Bevestiging (en) van door de klant geaccepteerde acceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="19fda-123">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="19fda-124">Gebruik de verzameling **IAggregatePartner. Customers** en roep **ById** methode aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="19fda-124">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="19fda-125">Haal de eigenschap **overeenkomsten** op en filter de resultaten op Microsoft Cloud overeenkomst door de methode **ByAgreementType** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="19fda-125">Fetch the **Agreements** property and filter the results to Microsoft Cloud Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="19fda-126">Roep **Get** -of **GetAsync** -methode aan.</span><span class="sxs-lookup"><span data-stu-id="19fda-126">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="19fda-127">Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="19fda-127">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="19fda-128">.NET (versie 1,9-1,13)</span><span class="sxs-lookup"><span data-stu-id="19fda-128">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="19fda-129">Bevestiging van een eerder gegeven klant acceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="19fda-129">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="19fda-130">Gebruik de verzameling **IAggregatePartner. Customers** en roep de methode **ById** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="19fda-130">Use the **IAggregatePartner.Customers** collection and call the **ById** method with the specified customer's identifier.</span></span> <span data-ttu-id="19fda-131">Vervolgens haalt u de eigenschap **overeenkomsten** op, gevolgd door de methoden **Get** of **GetAsync** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="19fda-131">Then, get the **Agreements** property, followed by calling the **Get** or **GetAsync** methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a><span data-ttu-id="19fda-132">Java</span><span class="sxs-lookup"><span data-stu-id="19fda-132">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="19fda-133">Bevestiging van een eerder gegeven klant acceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="19fda-133">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="19fda-134">Gebruik de functie **IAggregatePartner. getCustomers** en roep de functie **byId** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="19fda-134">Use the **IAggregatePartner.getCustomers** function and call the **byId** function with the specified customer's identifier.</span></span> <span data-ttu-id="19fda-135">Haal vervolgens de functie **getAgreements** op, gevolgd door de **Get** -functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="19fda-135">Then, get the **getAgreements** function, followed by calling the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

<span data-ttu-id="19fda-136">Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) -klasse in het [console test-app](https://github.com/Microsoft/Partner-Center-Java-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="19fda-136">A complete sample can be found in the [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="19fda-137">PowerShell</span><span class="sxs-lookup"><span data-stu-id="19fda-137">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="19fda-138">Bevestiging van een eerder gegeven klant acceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="19fda-138">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="19fda-139">Gebruik de opdracht [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) .</span><span class="sxs-lookup"><span data-stu-id="19fda-139">Use the [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) command.</span></span>

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a><span data-ttu-id="19fda-140">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="19fda-140">REST request</span></span>

<span data-ttu-id="19fda-141">Zie de volgende instructies voor het ophalen van de bevestiging van de klant acceptatie die eerder is verschaft.</span><span class="sxs-lookup"><span data-stu-id="19fda-141">To retrieve confirmation of customer acceptance provided previously, see the following instructions.</span></span>

<span data-ttu-id="19fda-142">Maak een nieuwe **overeenkomst** resource met de relevante certificerings informatie.</span><span class="sxs-lookup"><span data-stu-id="19fda-142">Create a new **Agreement** resource with the relevant certification information.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="19fda-143">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="19fda-143">Request syntax</span></span>

| <span data-ttu-id="19fda-144">Methode</span><span class="sxs-lookup"><span data-stu-id="19fda-144">Method</span></span> | <span data-ttu-id="19fda-145">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="19fda-145">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="19fda-146">GET</span><span class="sxs-lookup"><span data-stu-id="19fda-146">GET</span></span>    | <span data-ttu-id="19fda-147">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements http/1.1</span><span class="sxs-lookup"><span data-stu-id="19fda-147">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="19fda-148">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="19fda-148">URI parameter</span></span>

<span data-ttu-id="19fda-149">Gebruik de volgende query parameter om de klant op te geven die u bevestigt.</span><span class="sxs-lookup"><span data-stu-id="19fda-149">Use the following query parameter to specify the customer you are confirming.</span></span>

| <span data-ttu-id="19fda-150">Naam</span><span class="sxs-lookup"><span data-stu-id="19fda-150">Name</span></span>             | <span data-ttu-id="19fda-151">Type</span><span class="sxs-lookup"><span data-stu-id="19fda-151">Type</span></span> | <span data-ttu-id="19fda-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="19fda-152">Required</span></span> | <span data-ttu-id="19fda-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="19fda-153">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="19fda-154">CustomerTenantId</span><span class="sxs-lookup"><span data-stu-id="19fda-154">CustomerTenantId</span></span> | <span data-ttu-id="19fda-155">GUID</span><span class="sxs-lookup"><span data-stu-id="19fda-155">GUID</span></span> | <span data-ttu-id="19fda-156">J</span><span class="sxs-lookup"><span data-stu-id="19fda-156">Y</span></span>        | <span data-ttu-id="19fda-157">De waarde is een GUID-indeling **CustomerTenantId** waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="19fda-157">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="19fda-158">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="19fda-158">Request headers</span></span>

<span data-ttu-id="19fda-159">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="19fda-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="19fda-160">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="19fda-160">Request body</span></span>

<span data-ttu-id="19fda-161">Geen.</span><span class="sxs-lookup"><span data-stu-id="19fda-161">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="19fda-162">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="19fda-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="19fda-163">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="19fda-163">REST response</span></span>

<span data-ttu-id="19fda-164">Als dit lukt, retourneert deze methode een verzameling **overeenkomst** resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="19fda-164">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="19fda-165">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="19fda-165">Response success and error codes</span></span>

<span data-ttu-id="19fda-166">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="19fda-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="19fda-167">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="19fda-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="19fda-168">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="19fda-168">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="19fda-169">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="19fda-169">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2018-07-28T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2017-08-01T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        }
    ]
}
```
