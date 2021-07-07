---
title: Licenties toewijzen aan een gebruiker
description: Meer informatie over het toewijzen van licenties aan een klantgebruiker via Partner Center API's, zoals het gebruik van C- of \# REST API's.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 88ce0f185b0b043c4a7862b7f9808fb8805d40b9
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974366"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a><span data-ttu-id="d542e-103">Licenties toewijzen aan een gebruiker via Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="d542e-103">Assign licenses to a user via Partner Center APIs</span></span>

<span data-ttu-id="d542e-104">Licenties toewijzen aan een klantgebruiker.</span><span class="sxs-lookup"><span data-stu-id="d542e-104">How to assign licenses to a customer user.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d542e-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d542e-105">Prerequisites</span></span>

- <span data-ttu-id="d542e-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d542e-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d542e-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="d542e-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d542e-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d542e-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d542e-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="d542e-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d542e-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="d542e-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d542e-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="d542e-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d542e-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="d542e-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d542e-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d542e-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d542e-114">Een gebruikers-id van de klant.</span><span class="sxs-lookup"><span data-stu-id="d542e-114">A customer user identifier.</span></span> <span data-ttu-id="d542e-115">Deze id identificeert de gebruiker aan wie de licentie moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="d542e-115">This ID identifies the user to whom to assign the license.</span></span>

- <span data-ttu-id="d542e-116">Een product-SKU-id die het product voor de licentie identificeert.</span><span class="sxs-lookup"><span data-stu-id="d542e-116">A product SKU identifier that identifies the product for the license.</span></span>

## <a name="assigning-licenses-through-code"></a><span data-ttu-id="d542e-117">Licenties toewijzen via code</span><span class="sxs-lookup"><span data-stu-id="d542e-117">Assigning licenses through code</span></span>

<span data-ttu-id="d542e-118">Wanneer u licenties toewijst aan een gebruiker, moet u kiezen uit de verzameling geabonneerde SKU's van de klant.</span><span class="sxs-lookup"><span data-stu-id="d542e-118">When you assign licenses to a user, you must choose from the customer's collection of subscribed SKUs.</span></span> <span data-ttu-id="d542e-119">Nadat u de producten hebt geïdentificeerd die u wilt toewijzen, moet u de product-SKU-id voor elk product verkrijgen om de toewijzingen te kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="d542e-119">Then, having identified the products that you want to assign, you must obtain the product SKU ID for each product in order to make the assignments.</span></span> <span data-ttu-id="d542e-120">Elk [**SubscribedSku-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) bevat een [**eigenschap ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) van waaruit u kunt verwijzen naar het [**ProductSku-object**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) en de id [**kunt op halen.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id)</span><span class="sxs-lookup"><span data-stu-id="d542e-120">Each [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) instance contains a [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) property from which you can reference the [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) object and get the [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).</span></span>

<span data-ttu-id="d542e-121">Een licentietoewijzingsaanvraag moet licenties uit één licentiegroep bevatten.</span><span class="sxs-lookup"><span data-stu-id="d542e-121">A license assignment request must contain licenses from a single license group.</span></span> <span data-ttu-id="d542e-122">U kunt bijvoorbeeld geen licenties van [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) en **Group2** toewijzen in dezelfde aanvraag.</span><span class="sxs-lookup"><span data-stu-id="d542e-122">For example, you cannot assign licenses from [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) and **Group2** in the same request.</span></span> <span data-ttu-id="d542e-123">Een poging om licenties van meer dan één groep in één aanvraag toe te wijzen, mislukt met een passende fout.</span><span class="sxs-lookup"><span data-stu-id="d542e-123">An attempt to assign licenses from more than one group in a single request will fail with an appropriate error.</span></span> <span data-ttu-id="d542e-124">Zie Get [a list of available licenses by license group (Een](get-a-list-of-available-licenses-by-license-group.md)lijst met beschikbare licenties per licentiegroep verkrijgen) voor meer informatie over welke licenties beschikbaar zijn per licentiegroep.</span><span class="sxs-lookup"><span data-stu-id="d542e-124">To find out what licenses are available by license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

<span data-ttu-id="d542e-125">Hier volgen de stappen voor het toewijzen van licenties via code:</span><span class="sxs-lookup"><span data-stu-id="d542e-125">Here are the steps to assign licenses through code:</span></span>

1. <span data-ttu-id="d542e-126">Instantieer een [**LicenseAssignment-object.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)</span><span class="sxs-lookup"><span data-stu-id="d542e-126">Instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object.</span></span> <span data-ttu-id="d542e-127">U gebruikt dit object om de product-SKU en serviceplannen op te geven die u wilt toewijzen.</span><span class="sxs-lookup"><span data-stu-id="d542e-127">You use this object to specify the product SKU and service plans to assign.</span></span>

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. <span data-ttu-id="d542e-128">Vul de objecteigenschappen in zoals hieronder wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d542e-128">Populate the object properties as shown below.</span></span> <span data-ttu-id="d542e-129">In deze code wordt ervan uit gegaan dat u al de product-SKU-id hebt en dat alle beschikbare serviceplannen worden toegewezen (dat wil zeggen, geen van de abonnementen wordt uitgesloten).</span><span class="sxs-lookup"><span data-stu-id="d542e-129">This code assumes that you already have the product SKU ID, and that all of the available service plans will be assigned (that is, none will be excluded).</span></span>

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. <span data-ttu-id="d542e-130">Als u niet de product-SKU-id hebt, moet u de verzameling geabonneerde SKU's ophalen en de product-SKU-id ophalen van een van deze SKU's.</span><span class="sxs-lookup"><span data-stu-id="d542e-130">If you don't have the product SKU ID, you need to retrieve the collection of subscribed SKUs and get the product SKU ID from one of them.</span></span> <span data-ttu-id="d542e-131">Hier ziet u een voorbeeld als u de naam van de product-SKU kent.</span><span class="sxs-lookup"><span data-stu-id="d542e-131">Here is an example if you know the product SKU name.</span></span>

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. <span data-ttu-id="d542e-132">Vervolgens maakt u een nieuwe lijst van het type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)en voegt u het licentieobject toe.</span><span class="sxs-lookup"><span data-stu-id="d542e-132">Next, instantiate a new list of type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), and add the license object.</span></span> <span data-ttu-id="d542e-133">U kunt meer dan één licentie toewijzen door elke licentie afzonderlijk aan de lijst toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="d542e-133">You can assign more than one license by adding each individually to the list.</span></span> <span data-ttu-id="d542e-134">De licenties die in deze lijst zijn opgenomen, moeten van dezelfde licentiegroep zijn.</span><span class="sxs-lookup"><span data-stu-id="d542e-134">The licenses included in this list must be from the same license group.</span></span>

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. <span data-ttu-id="d542e-135">Maak een [**LicenseUpdate-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) en wijs de lijst met licentietoewijzingen toe aan [**de eigenschap LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)</span><span class="sxs-lookup"><span data-stu-id="d542e-135">Create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. <span data-ttu-id="d542e-136">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-updateobject door zoals hieronder wordt weergegeven om de licenties toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="d542e-136">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object as shown below to assign the licenses.</span></span>

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a><span data-ttu-id="d542e-137">C\#</span><span class="sxs-lookup"><span data-stu-id="d542e-137">C\#</span></span>

<span data-ttu-id="d542e-138">Als u een licentie wilt toewijzen aan een klantgebruiker, maakt u eerst een [**LicenseAssignment-object**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) en vult u de [**eigenschappen Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) en [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) in.</span><span class="sxs-lookup"><span data-stu-id="d542e-138">To assign a license to a customer user, first instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object, and populate the [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) and [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) properties.</span></span> <span data-ttu-id="d542e-139">U gebruikt dit object om de product-SKU op te geven die moet worden toegewezen en om serviceplannen uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="d542e-139">You use this object to specify the product SKU to assign and service plans to exclude.</span></span> <span data-ttu-id="d542e-140">Vervolgens maakt u een nieuwe lijst van het type **LicenseAssignment** en voegt u het licentieobject toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="d542e-140">Next, instantiate a new list of type **LicenseAssignment**, and add the license object to the list.</span></span> <span data-ttu-id="d542e-141">Maak vervolgens een [**LicenseUpdate-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) en wijs de lijst met licentietoewijzingen toe aan [**de eigenschap LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)</span><span class="sxs-lookup"><span data-stu-id="d542e-141">Then create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

<span data-ttu-id="d542e-142">Gebruik vervolgens de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**methode Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d542e-142">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="d542e-143">Haal vervolgens een interface op voor updatebewerkingen voor gebruikerslicenties van de klant [**via de eigenschap LicenseUpdates.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates)</span><span class="sxs-lookup"><span data-stu-id="d542e-143">Then get an interface to customer user license update operations from the [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) property.</span></span>

<span data-ttu-id="d542e-144">Roep ten slotte de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-updateobject door om de licentie toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="d542e-144">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object to assign the license.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerUserId;
// string selectedCustomerId;
// string selectedProductSkuId;

// Instantiate and populate a LicenseAssignment object.
LicenseAssignment license = new LicenseAssignment();
license.SkuId = selectedProductSkuId;
license.ExcludedPlans = null;

// Instantiate a list of licenses to assign and add the license to it.
List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
licenseList.Add(license);

// Instantiate a LicenseUpdate object and add the list of licenses to assign.
LicenseUpdate updateLicense = new LicenseUpdate();
updateLicense.LicensesToAssign = licenseList;

// Update the user licenses.
var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
```

<span data-ttu-id="d542e-145">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d542e-145">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d542e-146">**Project**: Partnercentrum-SDK Samples **Class**: CustomerUserAssignLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="d542e-146">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d542e-147">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d542e-147">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d542e-148">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="d542e-148">Request syntax</span></span>

| <span data-ttu-id="d542e-149">Methode</span><span class="sxs-lookup"><span data-stu-id="d542e-149">Method</span></span>   | <span data-ttu-id="d542e-150">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d542e-150">Request URI</span></span>                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d542e-151">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="d542e-151">**POST**</span></span> | <span data-ttu-id="d542e-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d542e-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="d542e-153">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="d542e-153">URI parameters</span></span>

<span data-ttu-id="d542e-154">Gebruik de volgende padparameters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d542e-154">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="d542e-155">Naam</span><span class="sxs-lookup"><span data-stu-id="d542e-155">Name</span></span>        | <span data-ttu-id="d542e-156">Type</span><span class="sxs-lookup"><span data-stu-id="d542e-156">Type</span></span>   | <span data-ttu-id="d542e-157">Vereist</span><span class="sxs-lookup"><span data-stu-id="d542e-157">Required</span></span> | <span data-ttu-id="d542e-158">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d542e-158">Description</span></span>                                       |
|-------------|--------|----------|---------------------------------------------------|
| <span data-ttu-id="d542e-159">customer-id</span><span class="sxs-lookup"><span data-stu-id="d542e-159">customer-id</span></span> | <span data-ttu-id="d542e-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d542e-160">string</span></span> | <span data-ttu-id="d542e-161">Ja</span><span class="sxs-lookup"><span data-stu-id="d542e-161">Yes</span></span>      | <span data-ttu-id="d542e-162">Een id met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="d542e-162">A GUID formatted ID that identifies the customer.</span></span> |
| <span data-ttu-id="d542e-163">user-id</span><span class="sxs-lookup"><span data-stu-id="d542e-163">user-id</span></span>     | <span data-ttu-id="d542e-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d542e-164">string</span></span> | <span data-ttu-id="d542e-165">Ja</span><span class="sxs-lookup"><span data-stu-id="d542e-165">Yes</span></span>      | <span data-ttu-id="d542e-166">Een id met GUID-indeling die de gebruiker identificeert.</span><span class="sxs-lookup"><span data-stu-id="d542e-166">A GUID formatted ID that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="d542e-167">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d542e-167">Request headers</span></span>

<span data-ttu-id="d542e-168">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="d542e-168">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d542e-169">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d542e-169">Request body</span></span>

<span data-ttu-id="d542e-170">Neem een [LicenseUpdate-resource](license-resources.md#licenseupdate) op in de aanvraag body waarin de licenties worden opgegeven die moeten worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="d542e-170">Include a [LicenseUpdate](license-resources.md#licenseupdate) resource in the request body that specifies the licenses to assign.</span></span>

### <a name="request-example"></a><span data-ttu-id="d542e-171">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d542e-171">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/554526aa-cf5e-46fa-95df-98dbc55d8a1e/licenseupdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 183
Expect: 100-continue

{
    "LicensesToAssign": [{
            "ExcludedPlans": null,
            "SkuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "LicensesToRemove": null,
    "LicenseWarnings": null,
    "Attributes": {
        "ObjectType": "LicenseUpdate"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="d542e-172">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d542e-172">REST response</span></span>

<span data-ttu-id="d542e-173">Als dit lukt, wordt de HTTP-antwoordstatuscode 201 geretourneerd en bevat de antwoord-body een [LicenseUpdate-resource](license-resources.md#licenseupdate) met de licentiegegevens.</span><span class="sxs-lookup"><span data-stu-id="d542e-173">If successful, an HTTP response status code 201 is returned and the response body contains a [LicenseUpdate](license-resources.md#licenseupdate) resource with the license information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d542e-174">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="d542e-174">Response success and error codes</span></span>

<span data-ttu-id="d542e-175">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="d542e-175">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d542e-176">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d542e-176">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d542e-177">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="d542e-177">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="d542e-178">Voorbeeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="d542e-178">Response example (success)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 139
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CV: 5AnzcZQrvUqCq3kd.0
MS-ServerId: 030020525
Date: Thu, 20 Apr 2017 21:50:39 GMT

{
    "licensesToAssign": [{
            "skuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "licenseWarnings": [],
    "attributes": {
        "objectType": "LicenseUpdate"
    }
}
```

### <a name="response-example-license-isnt-available"></a><span data-ttu-id="d542e-179">Voorbeeld van antwoord (licentie is niet beschikbaar)</span><span class="sxs-lookup"><span data-stu-id="d542e-179">Response example (license isn't available)</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 341
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: f4f3b748-8b22-4d07-a5a1-dceb32824192
MS-CV: 5npA0K22CUmWPOzB.0
MS-ServerId: 102030524
Date: Thu, 20 Apr 2017 22:12:36 GMT

{
    "code": 60012,
    "description": "We&#39;re sorry, it looks like you've run out of licenses. Buy more licenses, and then try again.",
    "data": ["LicenseQuotaExceededException : Subscription with Account 0c39d6d5-c70d-4c55-bc02-f620844f3fd1 and SKU f8a1db68-be16-40ed-86d5-cb42ce701560 does not have any available licenses left."],
    "source": "PartnerFD"
}
```
