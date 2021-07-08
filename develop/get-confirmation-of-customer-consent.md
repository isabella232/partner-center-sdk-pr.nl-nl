---
title: Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u bevestiging krijgt van de klantacceptatie van de Microsoft Cloud-overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: 1b1a8cbacb667e579bcd218a29c3f553afce26c2
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549260"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a><span data-ttu-id="c90d3-103">Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="c90d3-103">Get confirmation of customer acceptance of Microsoft Cloud Agreement</span></span>

<span data-ttu-id="c90d3-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="c90d3-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="c90d3-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c90d3-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c90d3-106">De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c90d3-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c90d3-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c90d3-107">Prerequisites</span></span>

- <span data-ttu-id="c90d3-108">Als u de .NET SDK Partner Center, is versie 1.9 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="c90d3-108">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="c90d3-109">Als u de Java SDK Partner Center, is versie 1.8 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="c90d3-109">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="c90d3-110">Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c90d3-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="c90d3-111">Dit scenario biedt alleen ondersteuning voor app- en gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="c90d3-111">This scenario only supports app + user authentication.</span></span>

- <span data-ttu-id="c90d3-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c90d3-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c90d3-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="c90d3-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c90d3-114">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="c90d3-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c90d3-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="c90d3-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c90d3-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="c90d3-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c90d3-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c90d3-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net-version-14-or-newer"></a><span data-ttu-id="c90d3-118">.NET (versie 1.4 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="c90d3-118">.NET (version 1.4 or newer)</span></span>

<span data-ttu-id="c90d3-119">Bevestiging(en) ophalen van de klantacceptatie die eerder is opgegeven:</span><span class="sxs-lookup"><span data-stu-id="c90d3-119">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="c90d3-120">Gebruik de **verzameling IAggregatePartner.Customers en** roep de **methode ById** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="c90d3-120">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="c90d3-121">Haal de **eigenschap Agreements** op en filter de resultaten naar Microsoft Cloud-overeenkomst door de **methode ByAgreementType aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="c90d3-121">Fetch the **Agreements** property and filter the results to Microsoft Cloud Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="c90d3-122">Roep **de methode Get** of **GetAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="c90d3-122">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="c90d3-123">Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)</span><span class="sxs-lookup"><span data-stu-id="c90d3-123">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="c90d3-124">.NET (versie 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="c90d3-124">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="c90d3-125">Bevestiging van eerder opgegeven klantacceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="c90d3-125">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="c90d3-126">Gebruik de **verzameling IAggregatePartner.Customers** en roep de **ById-methode** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="c90d3-126">Use the **IAggregatePartner.Customers** collection and call the **ById** method with the specified customer's identifier.</span></span> <span data-ttu-id="c90d3-127">Haal vervolgens de eigenschap **Agreements op,** gevolgd door de methoden **Get** of **GetAsync aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="c90d3-127">Then, get the **Agreements** property, followed by calling the **Get** or **GetAsync** methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a><span data-ttu-id="c90d3-128">Java</span><span class="sxs-lookup"><span data-stu-id="c90d3-128">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="c90d3-129">Bevestiging van eerder opgegeven klantacceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="c90d3-129">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="c90d3-130">Gebruik de **functie IAggregatePartner.getCustomers** en roep de **functie byId** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="c90d3-130">Use the **IAggregatePartner.getCustomers** function and call the **byId** function with the specified customer's identifier.</span></span> <span data-ttu-id="c90d3-131">Haal vervolgens de **functie getAgreements** op, gevolgd door het aanroepen van de **functie get.**</span><span class="sxs-lookup"><span data-stu-id="c90d3-131">Then, get the **getAgreements** function, followed by calling the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

<span data-ttu-id="c90d3-132">Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) van het [consoletest-app-project.](https://github.com/Microsoft/Partner-Center-Java-Samples)</span><span class="sxs-lookup"><span data-stu-id="c90d3-132">A complete sample can be found in the [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="c90d3-133">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c90d3-133">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="c90d3-134">Bevestiging van eerder opgegeven klantacceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="c90d3-134">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="c90d3-135">Gebruik de [**opdracht Get-PartnerCustomerAgreement.**](/powershell/module/partnercenter/get-partnercustomeragreement)</span><span class="sxs-lookup"><span data-stu-id="c90d3-135">Use the [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) command.</span></span>

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a><span data-ttu-id="c90d3-136">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c90d3-136">REST request</span></span>

<span data-ttu-id="c90d3-137">Zie de volgende instructies om de bevestiging op te halen dat de klant eerder is geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="c90d3-137">To retrieve confirmation of customer acceptance provided previously, see the following instructions.</span></span>

<span data-ttu-id="c90d3-138">Maak een nieuwe **Overeenkomst-resource** met de relevante certificeringsinformatie.</span><span class="sxs-lookup"><span data-stu-id="c90d3-138">Create a new **Agreement** resource with the relevant certification information.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c90d3-139">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c90d3-139">Request syntax</span></span>

| <span data-ttu-id="c90d3-140">Methode</span><span class="sxs-lookup"><span data-stu-id="c90d3-140">Method</span></span> | <span data-ttu-id="c90d3-141">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c90d3-141">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c90d3-142">GET</span><span class="sxs-lookup"><span data-stu-id="c90d3-142">GET</span></span>    | <span data-ttu-id="c90d3-143">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c90d3-143">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="c90d3-144">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="c90d3-144">URI parameter</span></span>

<span data-ttu-id="c90d3-145">Gebruik de volgende queryparameter om de klant op te geven die u wilt bevestigen.</span><span class="sxs-lookup"><span data-stu-id="c90d3-145">Use the following query parameter to specify the customer you are confirming.</span></span>

| <span data-ttu-id="c90d3-146">Naam</span><span class="sxs-lookup"><span data-stu-id="c90d3-146">Name</span></span>             | <span data-ttu-id="c90d3-147">Type</span><span class="sxs-lookup"><span data-stu-id="c90d3-147">Type</span></span> | <span data-ttu-id="c90d3-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="c90d3-148">Required</span></span> | <span data-ttu-id="c90d3-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c90d3-149">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="c90d3-150">CustomerTenantId</span><span class="sxs-lookup"><span data-stu-id="c90d3-150">CustomerTenantId</span></span> | <span data-ttu-id="c90d3-151">GUID</span><span class="sxs-lookup"><span data-stu-id="c90d3-151">GUID</span></span> | <span data-ttu-id="c90d3-152">J</span><span class="sxs-lookup"><span data-stu-id="c90d3-152">Y</span></span>        | <span data-ttu-id="c90d3-153">De waarde is een MET GUID **opgemaakte CustomerTenantId** waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c90d3-153">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c90d3-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c90d3-154">Request headers</span></span>

<span data-ttu-id="c90d3-155">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c90d3-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c90d3-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c90d3-156">Request body</span></span>

<span data-ttu-id="c90d3-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="c90d3-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c90d3-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c90d3-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="c90d3-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c90d3-159">REST response</span></span>

<span data-ttu-id="c90d3-160">Als dit lukt, retourneert deze methode een verzameling **Agreement-resources** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="c90d3-160">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c90d3-161">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c90d3-161">Response success and error codes</span></span>

<span data-ttu-id="c90d3-162">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c90d3-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c90d3-163">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c90d3-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c90d3-164">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c90d3-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c90d3-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c90d3-165">Response example</span></span>

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
