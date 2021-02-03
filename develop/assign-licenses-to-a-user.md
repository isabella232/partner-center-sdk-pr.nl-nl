---
title: Licenties toewijzen aan een gebruiker
description: Meer informatie over het toewijzen van licenties aan een klant gebruiker via partner Center Api's, zoals het gebruik van C- \# of rest-api's.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6eb0b953b9157e48074415bb3207e2946cfb2ab4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767597"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a><span data-ttu-id="32d6b-103">Licenties toewijzen aan een gebruiker via partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="32d6b-103">Assign licenses to a user via Partner Center APIs</span></span>

<span data-ttu-id="32d6b-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="32d6b-104">**Applies to:**</span></span>

- <span data-ttu-id="32d6b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="32d6b-105">Partner Center</span></span>

<span data-ttu-id="32d6b-106">Licenties toewijzen aan een klant gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32d6b-106">How to assign licenses to a customer user.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32d6b-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="32d6b-107">Prerequisites</span></span>

- <span data-ttu-id="32d6b-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="32d6b-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="32d6b-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="32d6b-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="32d6b-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="32d6b-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="32d6b-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="32d6b-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="32d6b-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="32d6b-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="32d6b-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="32d6b-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="32d6b-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="32d6b-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="32d6b-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="32d6b-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="32d6b-116">De gebruikers-id van de klant.</span><span class="sxs-lookup"><span data-stu-id="32d6b-116">A customer user identifier.</span></span> <span data-ttu-id="32d6b-117">Deze ID geeft aan aan welke gebruiker de licentie moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-117">This ID identifies the user to whom to assign the license.</span></span>

- <span data-ttu-id="32d6b-118">Een product-SKU-id waarmee het product voor de licentie wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="32d6b-118">A product SKU identifier that identifies the product for the license.</span></span>

## <a name="assigning-licenses-through-code"></a><span data-ttu-id="32d6b-119">Licenties toewijzen via code</span><span class="sxs-lookup"><span data-stu-id="32d6b-119">Assigning licenses through code</span></span>

<span data-ttu-id="32d6b-120">Wanneer u licenties aan een gebruiker toewijst, moet u kiezen uit de verzameling van geabonneerde Sku's van de klant.</span><span class="sxs-lookup"><span data-stu-id="32d6b-120">When you assign licenses to a user, you must choose from the customer's collection of subscribed SKUs.</span></span> <span data-ttu-id="32d6b-121">Nadat u de producten hebt geïdentificeerd die u wilt toewijzen, moet u de product-SKU-ID voor elk product verkrijgen om de toewijzingen te kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="32d6b-121">Then, having identified the products that you want to assign, you must obtain the product SKU ID for each product in order to make the assignments.</span></span> <span data-ttu-id="32d6b-122">Elk [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) -exemplaar bevat een [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) -eigenschap van waaruit u kunt verwijzen naar het [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) -object en de [**id**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id)ophalen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-122">Each [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) instance contains a [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) property from which you can reference the [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) object and get the [**ID**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id).</span></span>

<span data-ttu-id="32d6b-123">Een aanvraag voor licentie toewijzing moet licenties van één licentie groep bevatten.</span><span class="sxs-lookup"><span data-stu-id="32d6b-123">A license assignment request must contain licenses from a single license group.</span></span> <span data-ttu-id="32d6b-124">U kunt bijvoorbeeld geen licenties toewijzen van [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) en **group2** in dezelfde aanvraag.</span><span class="sxs-lookup"><span data-stu-id="32d6b-124">For example, you cannot assign licenses from [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) and **Group2** in the same request.</span></span> <span data-ttu-id="32d6b-125">Een poging om licenties toe te wijzen vanuit meer dan één groep in één aanvraag, mislukt met de juiste fout.</span><span class="sxs-lookup"><span data-stu-id="32d6b-125">An attempt to assign licenses from more than one group in a single request will fail with an appropriate error.</span></span> <span data-ttu-id="32d6b-126">Zie [een lijst met beschik bare licenties per licentie groep ophalen](get-a-list-of-available-licenses-by-license-group.md)voor meer informatie over de licenties die beschikbaar zijn per licentie groep.</span><span class="sxs-lookup"><span data-stu-id="32d6b-126">To find out what licenses are available by license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

<span data-ttu-id="32d6b-127">Hier volgen de stappen voor het toewijzen van licenties via code:</span><span class="sxs-lookup"><span data-stu-id="32d6b-127">Here are the steps to assign licenses through code:</span></span>

1. <span data-ttu-id="32d6b-128">Een [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) -object instantiëren.</span><span class="sxs-lookup"><span data-stu-id="32d6b-128">Instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object.</span></span> <span data-ttu-id="32d6b-129">U gebruikt dit object om op te geven welke product-SKU en service plannen u wilt toewijzen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-129">You use this object to specify the product SKU and service plans to assign.</span></span>

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. <span data-ttu-id="32d6b-130">Vul de object eigenschappen in zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="32d6b-130">Populate the object properties as shown below.</span></span> <span data-ttu-id="32d6b-131">In deze code wordt ervan uitgegaan dat u de product-SKU-ID al hebt, en dat alle beschik bare service plannen worden toegewezen (dat wil zeggen, geen wordt uitgesloten).</span><span class="sxs-lookup"><span data-stu-id="32d6b-131">This code assumes that you already have the product SKU ID, and that all of the available service plans will be assigned (that is, none will be excluded).</span></span>

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. <span data-ttu-id="32d6b-132">Als u de product-SKU-ID niet hebt, moet u de verzameling geabonneerde Sku's ophalen en de product-SKU-ID ophalen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-132">If you don't have the product SKU ID, you need to retrieve the collection of subscribed SKUs and get the product SKU ID from one of them.</span></span> <span data-ttu-id="32d6b-133">Hier volgt een voor beeld als u de naam van de product-SKU kent.</span><span class="sxs-lookup"><span data-stu-id="32d6b-133">Here is an example if you know the product SKU name.</span></span>

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. <span data-ttu-id="32d6b-134">Vervolgens maakt u een nieuwe lijst van het type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)en voegt u het licentie object toe.</span><span class="sxs-lookup"><span data-stu-id="32d6b-134">Next, instantiate a new list of type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment), and add the license object.</span></span> <span data-ttu-id="32d6b-135">U kunt meer dan één licentie toewijzen door elk afzonderlijk toe te voegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="32d6b-135">You can assign more than one license by adding each individually to the list.</span></span> <span data-ttu-id="32d6b-136">De licenties die in deze lijst zijn opgenomen, moeten afkomstig zijn uit dezelfde licentie groep.</span><span class="sxs-lookup"><span data-stu-id="32d6b-136">The licenses included in this list must be from the same license group.</span></span>

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. <span data-ttu-id="32d6b-137">Maak een [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) -exemplaar en wijs de lijst met licentie toewijzingen toe aan de eigenschap [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) .</span><span class="sxs-lookup"><span data-stu-id="32d6b-137">Create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. <span data-ttu-id="32d6b-138">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het object licentie update door, zoals hieronder wordt weer gegeven, om de licenties toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-138">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object as shown below to assign the licenses.</span></span>

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a><span data-ttu-id="32d6b-139">C\#</span><span class="sxs-lookup"><span data-stu-id="32d6b-139">C\#</span></span>

<span data-ttu-id="32d6b-140">Als u een licentie wilt toewijzen aan een klant gebruiker, maakt u eerst een [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) -object en vult u de eigenschappen [**skuId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) en [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) in.</span><span class="sxs-lookup"><span data-stu-id="32d6b-140">To assign a license to a customer user, first instantiate a [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) object, and populate the [**Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) and [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) properties.</span></span> <span data-ttu-id="32d6b-141">U gebruikt dit object om de product-SKU op te geven die moet worden toegewezen en service plannen die moeten worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="32d6b-141">You use this object to specify the product SKU to assign and service plans to exclude.</span></span> <span data-ttu-id="32d6b-142">Vervolgens maakt u een nieuwe lijst van het type **LicenseAssignment** en voegt u het licentie object toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="32d6b-142">Next, instantiate a new list of type **LicenseAssignment**, and add the license object to the list.</span></span> <span data-ttu-id="32d6b-143">Maak vervolgens een [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) -exemplaar en wijs de lijst met licentie toewijzingen toe aan de eigenschap [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) .</span><span class="sxs-lookup"><span data-stu-id="32d6b-143">Then create a [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) instance and assign the list of license assignments to the [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) property.</span></span>

<span data-ttu-id="32d6b-144">Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode met de gebruikers-id om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="32d6b-144">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the user ID to identify the user.</span></span> <span data-ttu-id="32d6b-145">Haal vervolgens een interface op voor het bijwerken van klant licenties voor gebruikers via de eigenschap [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) .</span><span class="sxs-lookup"><span data-stu-id="32d6b-145">Then get an interface to customer user license update operations from the [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) property.</span></span>

<span data-ttu-id="32d6b-146">Roep tot slot de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-update object door om de licentie toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-146">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) method and pass the license update object to assign the license.</span></span>

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

<span data-ttu-id="32d6b-147">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="32d6b-147">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="32d6b-148">**Project**: Partner Center SDK-voor beelden **klasse**: CustomerUserAssignLicenses.cs</span><span class="sxs-lookup"><span data-stu-id="32d6b-148">**Project**: Partner Center SDK Samples **Class**: CustomerUserAssignLicenses.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="32d6b-149">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="32d6b-149">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="32d6b-150">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32d6b-150">Request syntax</span></span>

| <span data-ttu-id="32d6b-151">Methode</span><span class="sxs-lookup"><span data-stu-id="32d6b-151">Method</span></span>   | <span data-ttu-id="32d6b-152">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="32d6b-152">Request URI</span></span>                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32d6b-153">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="32d6b-153">**POST**</span></span> | <span data-ttu-id="32d6b-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenseupdates http/1.1</span><span class="sxs-lookup"><span data-stu-id="32d6b-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="32d6b-155">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="32d6b-155">URI parameters</span></span>

<span data-ttu-id="32d6b-156">Gebruik de volgende para meters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="32d6b-156">Use the following path parameters to identify the customer and user.</span></span>

| <span data-ttu-id="32d6b-157">Naam</span><span class="sxs-lookup"><span data-stu-id="32d6b-157">Name</span></span>        | <span data-ttu-id="32d6b-158">Type</span><span class="sxs-lookup"><span data-stu-id="32d6b-158">Type</span></span>   | <span data-ttu-id="32d6b-159">Vereist</span><span class="sxs-lookup"><span data-stu-id="32d6b-159">Required</span></span> | <span data-ttu-id="32d6b-160">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32d6b-160">Description</span></span>                                       |
|-------------|--------|----------|---------------------------------------------------|
| <span data-ttu-id="32d6b-161">klant-id</span><span class="sxs-lookup"><span data-stu-id="32d6b-161">customer-id</span></span> | <span data-ttu-id="32d6b-162">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="32d6b-162">string</span></span> | <span data-ttu-id="32d6b-163">Yes</span><span class="sxs-lookup"><span data-stu-id="32d6b-163">Yes</span></span>      | <span data-ttu-id="32d6b-164">Een ID met de GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="32d6b-164">A GUID formatted ID that identifies the customer.</span></span> |
| <span data-ttu-id="32d6b-165">user-id</span><span class="sxs-lookup"><span data-stu-id="32d6b-165">user-id</span></span>     | <span data-ttu-id="32d6b-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="32d6b-166">string</span></span> | <span data-ttu-id="32d6b-167">Yes</span><span class="sxs-lookup"><span data-stu-id="32d6b-167">Yes</span></span>      | <span data-ttu-id="32d6b-168">Een ID met de GUID-indeling waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="32d6b-168">A GUID formatted ID that identifies the user.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="32d6b-169">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="32d6b-169">Request headers</span></span>

<span data-ttu-id="32d6b-170">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="32d6b-170">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="32d6b-171">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="32d6b-171">Request body</span></span>

<span data-ttu-id="32d6b-172">Neem een [LicenseUpdate](license-resources.md#licenseupdate) -resource op in de aanvraag tekst die aangeeft welke licenties moeten worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-172">Include a [LicenseUpdate](license-resources.md#licenseupdate) resource in the request body that specifies the licenses to assign.</span></span>

### <a name="request-example"></a><span data-ttu-id="32d6b-173">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32d6b-173">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="32d6b-174">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="32d6b-174">REST response</span></span>

<span data-ttu-id="32d6b-175">Als dit lukt, wordt een HTTP-antwoord status code 201 geretourneerd en de antwoord tekst bevat een [LicenseUpdate](license-resources.md#licenseupdate) -resource met de licentie gegevens.</span><span class="sxs-lookup"><span data-stu-id="32d6b-175">If successful, an HTTP response status code 201 is returned and the response body contains a [LicenseUpdate](license-resources.md#licenseupdate) resource with the license information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="32d6b-176">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="32d6b-176">Response success and error codes</span></span>

<span data-ttu-id="32d6b-177">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="32d6b-177">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="32d6b-178">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="32d6b-178">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="32d6b-179">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="32d6b-179">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="32d6b-180">Voor beeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="32d6b-180">Response example (success)</span></span>

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

### <a name="response-example-license-isnt-available"></a><span data-ttu-id="32d6b-181">Antwoord voorbeeld (licentie is niet beschikbaar)</span><span class="sxs-lookup"><span data-stu-id="32d6b-181">Response example (license isn't available)</span></span>

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
