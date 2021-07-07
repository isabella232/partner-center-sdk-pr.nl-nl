---
title: Partnercentrum-webhooks
description: Met webhooks kunnen partners zich registreren voor resourcewijzigingsgebeurtenissen.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 74d5981436ba29ea4f6f93a5693ec6da82777eb4
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547730"
---
# <a name="partner-center-webhooks"></a><span data-ttu-id="b8132-103">Partnercentrum-webhooks</span><span class="sxs-lookup"><span data-stu-id="b8132-103">Partner Center webhooks</span></span>

<span data-ttu-id="b8132-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b8132-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b8132-105">Met Partner Center webhook-API's kunnen partners zich registreren voor resourcewijzigingsgebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b8132-105">The Partner Center Webhook APIs allow partners to register for resource change events.</span></span> <span data-ttu-id="b8132-106">Deze gebeurtenissen worden geleverd in de vorm van HTTP POST's aan de geregistreerde URL van de partner.</span><span class="sxs-lookup"><span data-stu-id="b8132-106">These events are delivered in the form of HTTP POSTs to the partner's registered URL.</span></span> <span data-ttu-id="b8132-107">Als partners een gebeurtenis van Partner Center ontvangen, hosten ze een callback waar Partner Center de gebeurtenis van de resourcewijziging kan plaatsen.</span><span class="sxs-lookup"><span data-stu-id="b8132-107">To receive an event from Partner Center, partners will host a callback where Partner Center can POST the resource change event.</span></span> <span data-ttu-id="b8132-108">De gebeurtenis wordt digitaal ondertekend, zodat de partner kan controleren of deze is verzonden vanuit Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b8132-108">The event will be digitally signed so that the partner can verify that it was sent from Partner Center.</span></span>

<span data-ttu-id="b8132-109">Partners kunnen kiezen uit webhookgebeurtenissen, zoals de volgende voorbeelden, die worden ondersteund door Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b8132-109">Partners can select from Webhook events, like the following examples, that are supported by Partner Center.</span></span>

- <span data-ttu-id="b8132-110">**Testgebeurtenis ('test gemaakt')**</span><span class="sxs-lookup"><span data-stu-id="b8132-110">**Test Event ("test-created")**</span></span>

    <span data-ttu-id="b8132-111">Met deze gebeurtenis kunt u uw registratie zelf onboarden en testen door een testgebeurtenis aan te vragen en vervolgens de voortgang ervan bij te houden.</span><span class="sxs-lookup"><span data-stu-id="b8132-111">This event allows you to self-onboard and test your registration by requesting a test event and then tracking its progress.</span></span> <span data-ttu-id="b8132-112">U kunt de foutberichten zien die van Microsoft worden ontvangen tijdens het leveren van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b8132-112">You can see the failure messages that are being received from Microsoft while trying to deliver the event.</span></span> <span data-ttu-id="b8132-113">Deze beperking is alleen van toepassing op gebeurtenissen die zijn gemaakt door een test.</span><span class="sxs-lookup"><span data-stu-id="b8132-113">This restriction only applies to "test-created" events.</span></span> <span data-ttu-id="b8132-114">Gegevens ouder dan zeven dagen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b8132-114">Data older than seven days will be purged.</span></span>

- <span data-ttu-id="b8132-115">**Gebeurtenis bijgewerkt abonnement ('abonnement bijgewerkt')**</span><span class="sxs-lookup"><span data-stu-id="b8132-115">**Subscription Updated Event ("subscription-updated")**</span></span>

    <span data-ttu-id="b8132-116">Deze gebeurtenis wordt aan het werk gesteld wanneer het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b8132-116">This event is raised when the subscription changes.</span></span> <span data-ttu-id="b8132-117">Deze gebeurtenissen worden gegenereerd wanneer er een interne wijziging is naast wanneer wijzigingen worden aangebracht via de Partner Center API.</span><span class="sxs-lookup"><span data-stu-id="b8132-117">These events will be generated when there is an internal change in addition to when changes are made through the Partner Center API.</span></span>

    >[!NOTE]
    ><span data-ttu-id="b8132-118">Er is een vertraging van maximaal 48 uur tussen het moment waarop een abonnement wordt gewijzigd en het moment waarop de gebeurtenis Abonnement bijgewerkt wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b8132-118">There is a delay of up to 48 hours between the time a subscription changes and when the Subscription Updated event is triggered.</span></span>

- <span data-ttu-id="b8132-119">**Drempelwaarde overschreden gebeurtenis ('usagerecords-thresholdExceeded')**</span><span class="sxs-lookup"><span data-stu-id="b8132-119">**Threshold Exceeded Event ("usagerecords-thresholdExceeded")**</span></span>

    <span data-ttu-id="b8132-120">Deze gebeurtenis teert wanneer de hoeveelheid Microsoft Azure voor elke klant het gebruiksuitgavenbudget (hun drempelwaarde) overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="b8132-120">This event is raised when the amount of Microsoft Azure usage for any customer exceeds their usage spending budget (their threshold).</span></span> <span data-ttu-id="b8132-121">Zie [Een Azure-uitgavenbudget instellen voor uw klanten/partnercentrum/set-an-azure-spending-budget-for-your-customers) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b8132-121">For more information, see  [Set an Azure spending budget for your customers/partner-center/set-an-azure-spending-budget-for-your-customers).</span></span>

- <span data-ttu-id="b8132-122">**Door verwijzing gemaakte gebeurtenis ("verwijzing gemaakt")**</span><span class="sxs-lookup"><span data-stu-id="b8132-122">**Referral Created Event ("referral-created")**</span></span>

    <span data-ttu-id="b8132-123">Deze gebeurtenis wordt aangemaakt wanneer de verwijzing wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b8132-123">This event is raised when the referral is created.</span></span>

- <span data-ttu-id="b8132-124">**Gebeurtenis bijgewerkt door verwijzing ('verwijzing bijgewerkt')**</span><span class="sxs-lookup"><span data-stu-id="b8132-124">**Referral Updated Event ("referral-updated")**</span></span>

    <span data-ttu-id="b8132-125">Deze gebeurtenis wordt aan de orde gesteld wanneer de verwijzing wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="b8132-125">This event is raised when the referral is updated.</span></span>

- <span data-ttu-id="b8132-126">**Gebeurtenis gereed voor factuur ('factuur gereed')**</span><span class="sxs-lookup"><span data-stu-id="b8132-126">**Invoice Ready Event ("invoice-ready")**</span></span>

    <span data-ttu-id="b8132-127">Deze gebeurtenis wordt verhoogd wanneer de nieuwe factuur gereed is.</span><span class="sxs-lookup"><span data-stu-id="b8132-127">This event is raised when the new invoice is ready.</span></span>

<span data-ttu-id="b8132-128">Toekomstige webhookgebeurtenissen worden toegevoegd voor resources die wijzigen in het systeem waar de partner geen controle over heeft, en er worden verdere updates aangebracht om deze gebeurtenissen zo dicht mogelijk bij 'realtime' te krijgen.</span><span class="sxs-lookup"><span data-stu-id="b8132-128">Future Webhook events will be added for resources that change in the system that the partner isn't in control of, and further updates will be made to get those events as close to "real time" as possible.</span></span> <span data-ttu-id="b8132-129">Feedback van partners over welke gebeurtenissen waarde toevoegen aan hun bedrijf, is handig om te bepalen welke nieuwe gebeurtenissen moeten worden toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b8132-129">Feedback from Partners on which events add value to their business will be useful in determining what new events to add.</span></span>

<span data-ttu-id="b8132-130">Zie webhookgebeurtenissen voor een volledige Partner Center [webhookgebeurtenissen Partner Center webhookgebeurtenissen.](partner-center-webhook-events.md)</span><span class="sxs-lookup"><span data-stu-id="b8132-130">For a complete list of Webhook events supported by Partner Center, see [Partner Center webhook events](partner-center-webhook-events.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8132-131">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b8132-131">Prerequisites</span></span>

- <span data-ttu-id="b8132-132">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b8132-132">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b8132-133">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b8132-133">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="receiving-events-from-partner-center"></a><span data-ttu-id="b8132-134">Gebeurtenissen ontvangen van Partner Center</span><span class="sxs-lookup"><span data-stu-id="b8132-134">Receiving events from Partner Center</span></span>

<span data-ttu-id="b8132-135">Als u gebeurtenissen van Partner Center, moet u een openbaar toegankelijk eindpunt beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="b8132-135">To receive events from Partner Center, you must expose a publicly accessible endpoint.</span></span> <span data-ttu-id="b8132-136">Omdat dit eindpunt wordt blootgesteld, moet u controleren of de communicatie afkomstig is van Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b8132-136">Because this endpoint is exposed, you must validate that the communication is from Partner Center.</span></span> <span data-ttu-id="b8132-137">Alle webhookgebeurtenissen die u ontvangt, worden digitaal ondertekend met een certificaat dat is geketend aan microsoft Root.</span><span class="sxs-lookup"><span data-stu-id="b8132-137">All Webhook events that you receive are digitally signed with a certificate that chains to the Microsoft Root.</span></span> <span data-ttu-id="b8132-138">Er wordt ook een koppeling naar het certificaat gegeven dat wordt gebruikt om de gebeurtenis te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="b8132-138">A link to the certificate used to sign the event will also be provided.</span></span> <span data-ttu-id="b8132-139">Hierdoor kan het certificaat worden vernieuwd zonder dat u uw service opnieuw moet configureren of opnieuw moet configureren.</span><span class="sxs-lookup"><span data-stu-id="b8132-139">This will allow the certificate to be renewed without you having to redeploy or reconfigure your service.</span></span> <span data-ttu-id="b8132-140">Partner Center zal 10 pogingen doen om de gebeurtenis te leveren.</span><span class="sxs-lookup"><span data-stu-id="b8132-140">Partner Center will make 10 attempts to deliver the event.</span></span> <span data-ttu-id="b8132-141">Als de gebeurtenis na tien pogingen nog steeds niet wordt geleverd, wordt deze verplaatst naar een offlinewachtrij en worden er geen verdere pogingen gedaan bij levering.</span><span class="sxs-lookup"><span data-stu-id="b8132-141">If the event is still not delivered after 10 attempts, it will be moved into an offline queue and no further attempts will be made at delivery.</span></span>

<span data-ttu-id="b8132-142">In het volgende voorbeeld ziet u een gebeurtenis die is gepost vanuit Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b8132-142">The following sample shows an event posted from Partner Center.</span></span>

```http
POST /webhooks/callback
Content-Type: application/json
Authorization: Signature VOhcjRqA4f7u/4R29ohEzwRZibZdzfgG5/w4fHUnu8FHauBEVch8m2+5OgjLZRL33CIQpmqr2t0FsGF0UdmCR2OdY7rrAh/6QUW+u+jRUCV1s62M76jbVpTTGShmrANxnl8gz4LsbY260LAsDHufd6ab4oejerx1Ey9sFC+xwVTa+J4qGgeyIepeu4YCM0oB2RFS9rRB2F1s1OeAAPEhG7olp8B00Jss3PQrpLGOoAr5+fnQp8GOK8IdKF1/abUIyyvHxEjL76l7DVQN58pIJg4YC+pLs8pi6sTKvOdSVyCnjf+uYQWwmmWujSHfyU37j2Fzz16PJyWH41K8ZXJJkw==
X-MS-Certificate-Url: https://3psostorageacct.blob.core.windows.net/cert/pcnotifications-dispatch.microsoft.com.cer
X-MS-Signature-Algorithm: rsa-sha256
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 195

{
    "EventName": "test-created",
    "ResourceUri": "http://localhost:16722/v1/webhooks/registration/test",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

>[!NOTE]
><span data-ttu-id="b8132-143">De autorisatieheader heeft een schema van 'Handtekening'.</span><span class="sxs-lookup"><span data-stu-id="b8132-143">The Authorization header has a scheme of "Signature".</span></span> <span data-ttu-id="b8132-144">Dit is een base64 gecodeerde handtekening van de inhoud.</span><span class="sxs-lookup"><span data-stu-id="b8132-144">This is a base64 encoded signature of the content.</span></span>

## <a name="how-to-authenticate-the-callback"></a><span data-ttu-id="b8132-145">De callback verifiëren</span><span class="sxs-lookup"><span data-stu-id="b8132-145">How to authenticate the callback</span></span>

<span data-ttu-id="b8132-146">Volg deze stappen om de callbackgebeurtenis te verifiëren die Partner Center ontvangen:</span><span class="sxs-lookup"><span data-stu-id="b8132-146">To authenticate the callback event received from Partner Center, follow these steps:</span></span>

1. <span data-ttu-id="b8132-147">Controleer of de vereiste headers aanwezig zijn (Authorization, x-ms-certificate-url, x-ms-signature-algorithm).</span><span class="sxs-lookup"><span data-stu-id="b8132-147">Verify the required headers are present (Authorization, x-ms-certificate-url, x-ms-signature-algorithm).</span></span>

2. <span data-ttu-id="b8132-148">Download het certificaat dat wordt gebruikt om de inhoud te ondertekenen (x-ms-certificate-url).</span><span class="sxs-lookup"><span data-stu-id="b8132-148">Download the certificate used to sign the content (x-ms-certificate-url).</span></span>

3. <span data-ttu-id="b8132-149">Controleer de certificaatketen.</span><span class="sxs-lookup"><span data-stu-id="b8132-149">Verify the Certificate Chain.</span></span>

4. <span data-ttu-id="b8132-150">Controleer de organisatie van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="b8132-150">Verify the "Organization" of the certificate.</span></span>

5. <span data-ttu-id="b8132-151">Lees de inhoud met UTF8-codering in een buffer.</span><span class="sxs-lookup"><span data-stu-id="b8132-151">Read the content with UTF8 encoding into a buffer.</span></span>

6. <span data-ttu-id="b8132-152">Maak een RSA Crypto Provider.</span><span class="sxs-lookup"><span data-stu-id="b8132-152">Create an RSA Crypto Provider.</span></span>

7. <span data-ttu-id="b8132-153">Controleer of de gegevens overeenkomt met wat is ondertekend met het opgegeven hash-algoritme (bijvoorbeeld SHA256).</span><span class="sxs-lookup"><span data-stu-id="b8132-153">Verify the data matches what was signed with the specified hash algorithm (for example SHA256).</span></span>

8. <span data-ttu-id="b8132-154">Als de verificatie is geslaagd, verwerkt u het bericht.</span><span class="sxs-lookup"><span data-stu-id="b8132-154">If the verification succeeds, process the message.</span></span>

> [!NOTE]
> <span data-ttu-id="b8132-155">Standaard wordt het handtekening-token verzonden in een Autorisatie-header.</span><span class="sxs-lookup"><span data-stu-id="b8132-155">By default, the signature token will be sent in an Authorization header.</span></span> <span data-ttu-id="b8132-156">Als u **SignatureTokenToMsSignatureHeader** in uw registratie in uw registratie in stelt op true, wordt het handtekeningtoken in plaats daarvan verzonden in de x-ms-signature-header.</span><span class="sxs-lookup"><span data-stu-id="b8132-156">If you set **SignatureTokenToMsSignatureHeader** to true in your registration, the signature token will be sent in the x-ms-signature header instead.</span></span>

## <a name="event-model"></a><span data-ttu-id="b8132-157">Gebeurtenismodel</span><span class="sxs-lookup"><span data-stu-id="b8132-157">Event model</span></span>

<span data-ttu-id="b8132-158">In de volgende tabel worden de eigenschappen van een Partner Center beschreven.</span><span class="sxs-lookup"><span data-stu-id="b8132-158">The following table describes the properties of a Partner Center event.</span></span>

### <a name="properties"></a><span data-ttu-id="b8132-159">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b8132-159">Properties</span></span>

| <span data-ttu-id="b8132-160">Naam</span><span class="sxs-lookup"><span data-stu-id="b8132-160">Name</span></span>                      | <span data-ttu-id="b8132-161">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b8132-161">Description</span></span>                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="b8132-162">**Gebeurtenisnaam**</span><span class="sxs-lookup"><span data-stu-id="b8132-162">**EventName**</span></span>             | <span data-ttu-id="b8132-163">De naam van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b8132-163">The name of the event.</span></span> <span data-ttu-id="b8132-164">In de vorm {resource}-{action}.</span><span class="sxs-lookup"><span data-stu-id="b8132-164">In the form {resource}-{action}.</span></span> <span data-ttu-id="b8132-165">Bijvoorbeeld 'test-created'.</span><span class="sxs-lookup"><span data-stu-id="b8132-165">For example, "test-created".</span></span>  |
| <span data-ttu-id="b8132-166">**ResourceUri**</span><span class="sxs-lookup"><span data-stu-id="b8132-166">**ResourceUri**</span></span>           | <span data-ttu-id="b8132-167">De URI van de resource die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b8132-167">The URI of the resource that changed.</span></span>                                                 |
| <span data-ttu-id="b8132-168">**Resourcename**</span><span class="sxs-lookup"><span data-stu-id="b8132-168">**ResourceName**</span></span>          | <span data-ttu-id="b8132-169">De naam van de resource die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b8132-169">The name of the resource that changed.</span></span>                                                |
| <span data-ttu-id="b8132-170">**AuditUrl**</span><span class="sxs-lookup"><span data-stu-id="b8132-170">**AuditUrl**</span></span>              | <span data-ttu-id="b8132-171">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="b8132-171">Optional.</span></span> <span data-ttu-id="b8132-172">De URI van de controlerecord.</span><span class="sxs-lookup"><span data-stu-id="b8132-172">The URI of the Audit record.</span></span>                                                |
| <span data-ttu-id="b8132-173">**ResourceChangeUtcDate**</span><span class="sxs-lookup"><span data-stu-id="b8132-173">**ResourceChangeUtcDate**</span></span> | <span data-ttu-id="b8132-174">De datum en tijd, in UTC-indeling, waarop de resource is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b8132-174">The date and time, in UTC format, when the resource change occurred.</span></span>                  |

### <a name="sample"></a><span data-ttu-id="b8132-175">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b8132-175">Sample</span></span>

<span data-ttu-id="b8132-176">In het volgende voorbeeld ziet u de structuur van een Partner Center gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b8132-176">The following sample shows the structure of a Partner Center event.</span></span>

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a><span data-ttu-id="b8132-177">Webhook-API's</span><span class="sxs-lookup"><span data-stu-id="b8132-177">Webhook APIs</span></span>

### <a name="authentication"></a><span data-ttu-id="b8132-178">Verificatie</span><span class="sxs-lookup"><span data-stu-id="b8132-178">Authentication</span></span>

<span data-ttu-id="b8132-179">Alle aanroepen naar de Webhook-API's worden geverifieerd met behulp van het Bearer-token in de autorisatieheader.</span><span class="sxs-lookup"><span data-stu-id="b8132-179">All calls to the Webhook APIs are authenticated using the Bearer token in the Authorization Header.</span></span> <span data-ttu-id="b8132-180">Een toegangs token verkrijgen voor toegang `https://api.partnercenter.microsoft.com` tot .</span><span class="sxs-lookup"><span data-stu-id="b8132-180">Acquire an access token to access `https://api.partnercenter.microsoft.com`.</span></span> <span data-ttu-id="b8132-181">Dit token is hetzelfde token dat wordt gebruikt voor toegang tot de rest van de Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="b8132-181">This token is the same token that is used to access the rest of the Partner Center APIs.</span></span>

### <a name="get-a-list-of-events"></a><span data-ttu-id="b8132-182">Een lijst met gebeurtenissen op halen</span><span class="sxs-lookup"><span data-stu-id="b8132-182">Get a list of events</span></span>

<span data-ttu-id="b8132-183">Retourneert een lijst met de gebeurtenissen die momenteel worden ondersteund door de Webhook-API's.</span><span class="sxs-lookup"><span data-stu-id="b8132-183">Returns a list of the events that are currently supported by the Webhook APIs.</span></span>

### <a name="resource-url"></a><span data-ttu-id="b8132-184">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-184">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/events`

### <a name="request-example"></a><span data-ttu-id="b8132-185">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-185">Request example</span></span>

```http
GET /webhooks/v1/registration/events
content-type: application/json
authorization: Bearer eyJ0e.......
accept: */*
host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="b8132-186">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-186">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 183
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: c0bcf3a3-46e9-48fd-8e05-f674b8fd5d66
MS-RequestId: 79419bbb-06ee-48da-8221-e09480537dfc
X-Locale: en-US

[ "subscription-updated", "test-created", "usagerecords-thresholdExceeded" ]
```

### <a name="register-to-receive-events"></a><span data-ttu-id="b8132-187">Registreren om gebeurtenissen te ontvangen</span><span class="sxs-lookup"><span data-stu-id="b8132-187">Register to receive events</span></span>

<span data-ttu-id="b8132-188">Registreert een tenant voor het ontvangen van de opgegeven gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b8132-188">Registers a tenant to receive the specified events.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="b8132-189">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-189">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="b8132-190">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-190">Request example</span></span>

```http
POST /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer eyJ0e.....
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 219

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="response-example"></a><span data-ttu-id="b8132-191">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-191">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 346
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 718f2336-8b56-4f42-93ac-54896047c59a
MS-RequestId: f04b1b5e-87b4-4d95-b087-d65fffec0bd2

{
    "SubscriberId": "e82cac64-dc67-4cd3-849b-78b6127dd57d",
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": [ "subscription-updated", "test-created" ]
}
```

### <a name="view-a-registration"></a><span data-ttu-id="b8132-192">Een registratie weergeven</span><span class="sxs-lookup"><span data-stu-id="b8132-192">View a registration</span></span>

<span data-ttu-id="b8132-193">Retourneert de webhooksgebeurtenisregistratie voor een tenant.</span><span class="sxs-lookup"><span data-stu-id="b8132-193">Returns the Webhooks event registration for a tenant.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="b8132-194">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-194">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="b8132-195">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-195">Request example</span></span>

```http
GET /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="b8132-196">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-196">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 341
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: c3b88ab0-b7bc-48d6-8c55-4ae6200f490a
MS-RequestId: ca30367d-4b24-4516-af08-74bba6dc6657
X-Locale: en-US

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="update-an-event-registration"></a><span data-ttu-id="b8132-197">Een gebeurtenisregistratie bijwerken</span><span class="sxs-lookup"><span data-stu-id="b8132-197">Update an event registration</span></span>

<span data-ttu-id="b8132-198">Werkt een bestaande gebeurtenisregistratie bij.</span><span class="sxs-lookup"><span data-stu-id="b8132-198">Updates an existing event registration.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="b8132-199">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-199">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="b8132-200">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-200">Request example</span></span>

```http
PUT /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOR...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 258

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="response-example"></a><span data-ttu-id="b8132-201">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-201">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 346
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 718f2336-8b56-4f42-93ac-54896047c59a
MS-RequestId: f04b1b5e-87b4-4d95-b087-d65fffec0bd2

{
    "SubscriberId": "e82cac64-dc67-4cd3-849b-78b6127dd57d",
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": [ "subscription-updated", "test-created" ]
}
```

### <a name="send-a-test-event-to-validate-your-registration"></a><span data-ttu-id="b8132-202">Een testgebeurtenis verzenden om uw registratie te valideren</span><span class="sxs-lookup"><span data-stu-id="b8132-202">Send a test event to validate your registration</span></span>

<span data-ttu-id="b8132-203">Genereert een testgebeurtenis om de webhooksregistratie te valideren.</span><span class="sxs-lookup"><span data-stu-id="b8132-203">Generates a test event to validate the Webhooks registration.</span></span> <span data-ttu-id="b8132-204">Deze test is bedoeld om te controleren of u gebeurtenissen kunt ontvangen van Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b8132-204">This test is intended to validate that you can receive events from Partner Center.</span></span> <span data-ttu-id="b8132-205">Gegevens voor deze gebeurtenissen worden zeven dagen na het maken van de eerste gebeurtenis verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b8132-205">Data for these events will be deleted seven days after the initial event is created.</span></span> <span data-ttu-id="b8132-206">U moet zijn geregistreerd voor de gebeurtenis 'test gemaakt' met behulp van de registratie-API voordat u een validatiegebeurtenis verstuurt.</span><span class="sxs-lookup"><span data-stu-id="b8132-206">You must be registered for the "test-created" event, using the registration API, before sending a validation event.</span></span>

>[!NOTE]
><span data-ttu-id="b8132-207">Er is een vertragingslimiet van 2 aanvragen per minuut bij het plaatsen van een validatiegebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b8132-207">There is a throttle limit of 2 requests per minute when posting a validation event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="b8132-208">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-208">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents`

### <a name="request-example"></a><span data-ttu-id="b8132-209">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-209">Request example</span></span>

```http
POST /webhooks/v1/registration/validationEvents
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length:
```

### <a name="response-example"></a><span data-ttu-id="b8132-210">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-210">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 181
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 04af2aea-d413-42db-824e-f328001484d1
MS-RequestId: 2f498d5a-a6ab-468f-98d8-93c96da09051
X-Locale: en-US

{ "correlationId": "04af2aea-d413-42db-824e-f328001484d1" }
```

### <a name="verify-that-the-event-was-delivered"></a><span data-ttu-id="b8132-211">Controleren of de gebeurtenis is geleverd</span><span class="sxs-lookup"><span data-stu-id="b8132-211">Verify that the event was delivered</span></span>

<span data-ttu-id="b8132-212">Retourneert de huidige status van de validatiegebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b8132-212">Returns the current state of the validation event.</span></span> <span data-ttu-id="b8132-213">Deze verificatie kan handig zijn voor het oplossen van problemen met de levering van gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b8132-213">This verification can be helpful for troubleshooting event delivery issues.</span></span> <span data-ttu-id="b8132-214">Het antwoord bevat een resultaat voor elke poging om de gebeurtenis te leveren.</span><span class="sxs-lookup"><span data-stu-id="b8132-214">The Response contains a result for each attempt that is made to deliver the event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="b8132-215">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="b8132-215">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{correlationId}`

### <a name="request-example"></a><span data-ttu-id="b8132-216">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8132-216">Request example</span></span>

```http
GET /webhooks/v1/registration/validationEvents/04af2aea-d413-42db-824e-f328001484d1
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="b8132-217">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8132-217">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 469
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 497e0a23-9498-4d6c-bd6a-bc4d6d0054e7
MS-RequestId: 0843bdb2-113a-4926-a51c-284aa01d722e
X-Locale: en-US

{
    "correlationId": "04af2aea-d413-42db-824e-f328001484d1",
    "partnerId": "00234d9d-8c2d-4ff5-8c18-39f8afc6f7f3",
    "status": "completed",
    "callbackUrl": "{{YourCallbackUrl}}",
    "results": [{
        "responseCode": "OK",
        "responseMessage": "",
        "systemError": false,
        "dateTimeUtc": "2017-12-08T21:39:48.2386997"
    }]
}
```

## <a name="example-for-signature-validation"></a><span data-ttu-id="b8132-218">Voorbeeld voor handtekeningvalidatie</span><span class="sxs-lookup"><span data-stu-id="b8132-218">Example for Signature Validation</span></span>

### <a name="sample-callback-controller-signature-aspnet"></a><span data-ttu-id="b8132-219">Voorbeeld van callback-controllerhandtekening (ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="b8132-219">Sample Callback Controller signature (ASP.NET)</span></span>

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a><span data-ttu-id="b8132-220">Handtekeningvalidatie</span><span class="sxs-lookup"><span data-stu-id="b8132-220">Signature Validation</span></span>

<span data-ttu-id="b8132-221">In het volgende voorbeeld ziet u hoe u een autorisatiekenmerk toevoegt aan de controller die callbacks van webhookgebeurtenissen ontvangt.</span><span class="sxs-lookup"><span data-stu-id="b8132-221">The following example shows how to add an Authorization Attribute to the controller that is receiving callbacks from Webhook events.</span></span>

``` csharp
namespace Webhooks.Security
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Linq;
    using System.Net;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using System.Security.Cryptography;
    using System.Security.Cryptography.X509Certificates;
    using System.Text;
    using System.Threading;
    using System.Threading.Tasks;
    using System.Web.Http;
    using System.Web.Http.Controllers;
    using Microsoft.Partner.Logging;

    /// <summary>
    /// Signature based Authorization
    /// </summary>
    public class AuthorizeSignatureAttribute : AuthorizeAttribute
    {
        private const string MsSignatureHeader = "x-ms-signature";
        private const string CertificateUrlHeader = "x-ms-certificate-url";
        private const string SignatureAlgorithmHeader = "x-ms-signature-algorithm";
        private const string MicrosoftCorporationIssuer = "O=Microsoft Corporation";
        private const string SignatureScheme = "Signature";

        /// <inheritdoc/>
        public override async Task OnAuthorizationAsync(HttpActionContext actionContext, CancellationToken cancellationToken)
        {
            ValidateAuthorizationHeaders(actionContext.Request);

            await VerifySignature(actionContext.Request);
        }

        private static async Task<string> GetContentAsync(HttpRequestMessage request)
        {
            // By default the stream can only be read once and we need to read it here so that we can hash the body to validate the signature from microsoft.
            // Load into a buffer, so that the stream can be accessed here and in the api when it binds the content to the expected model type.
            await request.Content.LoadIntoBufferAsync();

            var s = await request.Content.ReadAsStreamAsync();
            var reader = new StreamReader(s);
            var body = await reader.ReadToEndAsync();

            // set the stream position back to the beginning
            if (s.CanSeek)
            {
                s.Seek(0, SeekOrigin.Begin);
            }

            return body;
        }

        private static void ValidateAuthorizationHeaders(HttpRequestMessage request)
        {
            var authHeader = request.Headers.Authorization;
            if (string.IsNullOrWhiteSpace(authHeader?.Parameter) && string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, MsSignatureHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Authorization header missing."));
            }

            var signatureHeaderValue = GetHeaderValue(request.Headers, MsSignatureHeader);
            if (authHeader != null
                && !string.Equals(authHeader.Scheme, SignatureScheme, StringComparison.OrdinalIgnoreCase)
                && !string.IsNullOrWhiteSpace(signatureHeaderValue)
                && !signatureHeaderValue.StartsWith(SignatureScheme, StringComparison.OrdinalIgnoreCase))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, $"Authorization scheme needs to be '{SignatureScheme}'."));
            }

            if (string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, CertificateUrlHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.BadRequest, $"Request header {CertificateUrlHeader} missing."));
            }

            if (string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, SignatureAlgorithmHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.BadRequest, $"Request header {SignatureAlgorithmHeader} missing."));
            }
        }

        private static string GetHeaderValue(HttpHeaders headers, string key)
        {
            headers.TryGetValues(key, out var headerValues);

            return headerValues?.FirstOrDefault();
        }

        private static async Task VerifySignature(HttpRequestMessage request)
        {
            // Get signature value from either authorization header or x-ms-signature header.
            var base64Signature = request.Headers.Authorization?.Parameter ?? GetHeaderValue(request.Headers, MsSignatureHeader).Split(' ')[1];
            var signatureAlgorithm = GetHeaderValue(request.Headers, SignatureAlgorithmHeader);
            var certificateUrl = GetHeaderValue(request.Headers, CertificateUrlHeader);
            var certificate = await GetCertificate(certificateUrl);
            var content = await GetContentAsync(request);
            var alg = signatureAlgorithm.Split('-'); // for example RSA-SHA1
            var isValid = false;

            var logger = GetLoggerIfAvailable(request);

            // Validate the certificate
            VerifyCertificate(certificate, request, logger);

            if (alg.Length == 2 && alg[0].Equals("RSA", StringComparison.OrdinalIgnoreCase))
            {
                var signature = Convert.FromBase64String(base64Signature);
                var csp = (RSACryptoServiceProvider)certificate.PublicKey.Key;

                var encoding = new UTF8Encoding();
                var data = encoding.GetBytes(content);

                var hashAlgorithm = alg[1].ToUpper();

                isValid = csp.VerifyData(data, CryptoConfig.MapNameToOID(hashAlgorithm), signature);
            }

            if (!isValid)
            {
                // log that we were not able to validate the signature
                logger?.TrackTrace(
                    "Failed to validate signature for webhook callback",
                    new Dictionary<string, string> { { "base64Signature", base64Signature }, { "certificateUrl", certificateUrl }, { "signatureAlgorithm", signatureAlgorithm }, { "content", content } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Signature verification failed"));
            }
        }

        private static ILogger GetLoggerIfAvailable(HttpRequestMessage request)
        {
            return request.GetDependencyScope().GetService(typeof(ILogger)) as ILogger;
        }

        private static async Task<X509Certificate2> GetCertificate(string certificateUrl)
        {
            byte[] certBytes;
            using (var webClient = new WebClient())
            {
                certBytes = await webClient.DownloadDataTaskAsync(certificateUrl);
            }

            return new X509Certificate2(certBytes);
        }

        private static void VerifyCertificate(X509Certificate2 certificate, HttpRequestMessage request, ILogger logger)
        {
            if (!certificate.Verify())
            {
                logger?.TrackTrace("Failed to verify certificate for webhook callback.", new Dictionary<string, string> { { "Subject", certificate.Subject }, { "Issuer", certificate.Issuer } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Certificate verification failed."));
            }

            if (!certificate.Issuer.Contains(MicrosoftCorporationIssuer))
            {
                logger?.TrackTrace($"Certificate not issued by {MicrosoftCorporationIssuer}.", new Dictionary<string, string> { { "Issuer", certificate.Issuer } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, $"Certificate not issued by {MicrosoftCorporationIssuer}."));
            }
        }
    }
}
```
