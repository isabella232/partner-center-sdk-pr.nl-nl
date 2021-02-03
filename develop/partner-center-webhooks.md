---
title: Partnercentrum-webhooks
description: Met webhooks kunnen partners zich registreren voor bron wijzigings gebeurtenissen.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 8225623ade7e922ac23ebf0ed9215686b0601244
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767336"
---
# <a name="partner-center-webhooks"></a><span data-ttu-id="32c81-103">Partnercentrum-webhooks</span><span class="sxs-lookup"><span data-stu-id="32c81-103">Partner Center webhooks</span></span>

<span data-ttu-id="32c81-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="32c81-104">**Applies To**</span></span>

- <span data-ttu-id="32c81-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="32c81-105">Partner Center</span></span>
- <span data-ttu-id="32c81-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="32c81-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="32c81-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="32c81-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="32c81-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="32c81-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="32c81-109">Met de webhook-Api's van partner Center kunnen partners zich registreren voor bron wijzigings gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="32c81-109">The Partner Center Webhook APIs allow partners to register for resource change events.</span></span> <span data-ttu-id="32c81-110">Deze gebeurtenissen worden in de vorm van HTTP-berichten verzonden naar de geregistreerde URL van de partner.</span><span class="sxs-lookup"><span data-stu-id="32c81-110">These events are delivered in the form of HTTP POSTs to the partner's registered URL.</span></span> <span data-ttu-id="32c81-111">Als u een gebeurtenis van het partner centrum wilt ontvangen, hosten partners een call back waarbij het partner centrum de wijzigings gebeurtenis van de resource kan posten.</span><span class="sxs-lookup"><span data-stu-id="32c81-111">To receive an event from Partner Center, partners will host a callback where Partner Center can POST the resource change event.</span></span> <span data-ttu-id="32c81-112">De gebeurtenis wordt digitaal ondertekend, zodat de partner kan controleren of deze is verzonden vanuit het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="32c81-112">The event will be digitally signed so that the partner can verify that it was sent from Partner Center.</span></span>

<span data-ttu-id="32c81-113">Partners kunnen een keuze maken uit webhook-gebeurtenissen, zoals de volgende voor beelden, die worden ondersteund door het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="32c81-113">Partners can select from Webhook events, like the following examples, that are supported by Partner Center.</span></span>

- <span data-ttu-id="32c81-114">**Test gebeurtenis ("test-created")**</span><span class="sxs-lookup"><span data-stu-id="32c81-114">**Test Event ("test-created")**</span></span>

    <span data-ttu-id="32c81-115">Met deze gebeurtenis kunt u zelf onboards en uw registratie testen door een test gebeurtenis aan te vragen en de voortgang op te sporen.</span><span class="sxs-lookup"><span data-stu-id="32c81-115">This event allows you to self-onboard and test your registration by requesting a test event and then tracking its progress.</span></span> <span data-ttu-id="32c81-116">U kunt de fout berichten bekijken die van micro soft worden ontvangen tijdens het leveren van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-116">You can see the failure messages that are being received from Microsoft while trying to deliver the event.</span></span> <span data-ttu-id="32c81-117">Deze beperking is alleen van toepassing op gebeurtenissen die zijn gemaakt met een test.</span><span class="sxs-lookup"><span data-stu-id="32c81-117">This restriction only applies to "test-created" events.</span></span> <span data-ttu-id="32c81-118">Gegevens die ouder zijn dan zeven dagen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="32c81-118">Data older than seven days will be purged.</span></span>

- <span data-ttu-id="32c81-119">**Bijgewerkte gebeurtenis van abonnement (abonnement-bijgewerkt)**</span><span class="sxs-lookup"><span data-stu-id="32c81-119">**Subscription Updated Event ("subscription-updated")**</span></span>

    <span data-ttu-id="32c81-120">Deze gebeurtenis treedt op wanneer het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32c81-120">This event is raised when the subscription changes.</span></span> <span data-ttu-id="32c81-121">Deze gebeurtenissen worden gegenereerd wanneer er een interne wijziging in aanvulling is op wanneer wijzigingen worden aangebracht via de partner centrum-API.</span><span class="sxs-lookup"><span data-stu-id="32c81-121">These events will be generated when there is an internal change in addition to when changes are made through the Partner Center API.</span></span>

    >[!NOTE]
    ><span data-ttu-id="32c81-122">Er is een vertraging van Maxi maal 48 uur tussen het tijdstip waarop een abonnement wijzigt en wanneer de gebeurtenis bijgewerkt abonnement wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="32c81-122">There is a delay of up to 48 hours between the time a subscription changes and when the Subscription Updated event is triggered.</span></span>

- <span data-ttu-id="32c81-123">**Gebeurtenis drempelwaarde overschreden ("usagerecords-thresholdExceeded")**</span><span class="sxs-lookup"><span data-stu-id="32c81-123">**Threshold Exceeded Event ("usagerecords-thresholdExceeded")**</span></span>

    <span data-ttu-id="32c81-124">Deze gebeurtenis treedt op wanneer de hoeveelheid Microsoft Azure gebruik voor een klant groter is dan het bestedings budget van het gebruik (de drempel waarde).</span><span class="sxs-lookup"><span data-stu-id="32c81-124">This event is raised when the amount of Microsoft Azure usage for any customer exceeds their usage spending budget (their threshold).</span></span> <span data-ttu-id="32c81-125">Zie voor meer informatie [een Azure-uitgaven budget instellen voor uw klanten/Partner-Center/set-a-Azure-besteding-budget-voor-uw klanten).</span><span class="sxs-lookup"><span data-stu-id="32c81-125">For more information, see  [Set an Azure spending budget for your customers/partner-center/set-an-azure-spending-budget-for-your-customers).</span></span>

- <span data-ttu-id="32c81-126">**Gebeurtenis voor het maken van een referral (' verwijzing-gemaakt ')**</span><span class="sxs-lookup"><span data-stu-id="32c81-126">**Referral Created Event ("referral-created")**</span></span>

    <span data-ttu-id="32c81-127">Deze gebeurtenis treedt op wanneer de verwijzing wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32c81-127">This event is raised when the referral is created.</span></span>

- <span data-ttu-id="32c81-128">**De gebeurtenis Referral update (' verwijzing-bijgewerkt ')**</span><span class="sxs-lookup"><span data-stu-id="32c81-128">**Referral Updated Event ("referral-updated")**</span></span>

    <span data-ttu-id="32c81-129">Deze gebeurtenis treedt op wanneer de verwijzing wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="32c81-129">This event is raised when the referral is updated.</span></span>

- <span data-ttu-id="32c81-130">**Factuur gereed gebeurtenis ("factuur gereed")**</span><span class="sxs-lookup"><span data-stu-id="32c81-130">**Invoice Ready Event ("invoice-ready")**</span></span>

    <span data-ttu-id="32c81-131">Deze gebeurtenis treedt op wanneer de nieuwe factuur gereed is.</span><span class="sxs-lookup"><span data-stu-id="32c81-131">This event is raised when the new invoice is ready.</span></span>

<span data-ttu-id="32c81-132">Toekomstige webhook-gebeurtenissen worden toegevoegd voor resources die veranderen in het systeem waarvan de partner niet in beheer is, en er worden verdere updates uitgevoerd om deze gebeurtenissen zo snel mogelijk op te halen.</span><span class="sxs-lookup"><span data-stu-id="32c81-132">Future Webhook events will be added for resources that change in the system that the partner isn't in control of, and further updates will be made to get those events as close to "real time" as possible.</span></span> <span data-ttu-id="32c81-133">Feedback van partners over welke gebeurtenissen een waarde toevoegen aan hun bedrijf is handig om te bepalen welke nieuwe gebeurtenissen moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="32c81-133">Feedback from Partners on which events add value to their business will be useful in determining what new events to add.</span></span>

<span data-ttu-id="32c81-134">Zie [Partner Center-gebeurtenissen voor webhooks](partner-center-webhook-events.md)voor een volledige lijst van webhook-gebeurtenissen die worden ondersteund door het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="32c81-134">For a complete list of Webhook events supported by Partner Center, see [Partner Center webhook events](partner-center-webhook-events.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32c81-135">Vereisten</span><span class="sxs-lookup"><span data-stu-id="32c81-135">Prerequisites</span></span>

- <span data-ttu-id="32c81-136">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="32c81-136">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="32c81-137">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="32c81-137">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="receiving-events-from-partner-center"></a><span data-ttu-id="32c81-138">Gebeurtenissen ontvangen van het partner centrum</span><span class="sxs-lookup"><span data-stu-id="32c81-138">Receiving events from Partner Center</span></span>

<span data-ttu-id="32c81-139">Als u gebeurtenissen van het partner centrum wilt ontvangen, moet u een openbaar toegankelijk eind punt zichtbaar maken.</span><span class="sxs-lookup"><span data-stu-id="32c81-139">To receive events from Partner Center, you must expose a publicly accessible endpoint.</span></span> <span data-ttu-id="32c81-140">Omdat dit eind punt wordt weer gegeven, moet u controleren of de communicatie van het partner centrum is.</span><span class="sxs-lookup"><span data-stu-id="32c81-140">Because this endpoint is exposed, you must validate that the communication is from Partner Center.</span></span> <span data-ttu-id="32c81-141">Alle webhook-gebeurtenissen die u ontvangt, worden digitaal ondertekend met een certificaat dat is gekoppeld aan de micro soft root.</span><span class="sxs-lookup"><span data-stu-id="32c81-141">All Webhook events that you receive are digitally signed with a certificate that chains to the Microsoft Root.</span></span> <span data-ttu-id="32c81-142">Er wordt ook een koppeling weer gegeven naar het certificaat dat wordt gebruikt om de gebeurtenis te ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="32c81-142">A link to the certificate used to sign the event will also be provided.</span></span> <span data-ttu-id="32c81-143">Hierdoor kan het certificaat worden vernieuwd zonder dat u uw service opnieuw hoeft te implementeren of opnieuw te configureren.</span><span class="sxs-lookup"><span data-stu-id="32c81-143">This will allow the certificate to be renewed without you having to redeploy or reconfigure your service.</span></span> <span data-ttu-id="32c81-144">Het partner centrum maakt 10 pogingen om de gebeurtenis te leveren.</span><span class="sxs-lookup"><span data-stu-id="32c81-144">Partner Center will make 10 attempts to deliver the event.</span></span> <span data-ttu-id="32c81-145">Als de gebeurtenis na 10 pogingen nog niet is bezorgd, wordt deze naar een offline wachtrij verplaatst en worden er geen nieuwe pogingen gedaan bij de levering.</span><span class="sxs-lookup"><span data-stu-id="32c81-145">If the event is still not delivered after 10 attempts, it will be moved into an offline queue and no further attempts will be made at delivery.</span></span>

<span data-ttu-id="32c81-146">In het volgende voor beeld ziet u een gebeurtenis die is gepost vanuit het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="32c81-146">The following sample shows an event posted from Partner Center.</span></span>

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
><span data-ttu-id="32c81-147">De autorisatie-header heeft het schema hand tekening.</span><span class="sxs-lookup"><span data-stu-id="32c81-147">The Authorization header has a scheme of "Signature".</span></span> <span data-ttu-id="32c81-148">Dit is een met base64 gecodeerde hand tekening van de inhoud.</span><span class="sxs-lookup"><span data-stu-id="32c81-148">This is a base64 encoded signature of the content.</span></span>

## <a name="how-to-authenticate-the-callback"></a><span data-ttu-id="32c81-149">De call back verifiëren</span><span class="sxs-lookup"><span data-stu-id="32c81-149">How to authenticate the callback</span></span>

<span data-ttu-id="32c81-150">Voer de volgende stappen uit om de retour aanroep gebeurtenis te verifiëren die is ontvangen van het partner centrum:</span><span class="sxs-lookup"><span data-stu-id="32c81-150">To authenticate the callback event received from Partner Center, follow these steps:</span></span>

1. <span data-ttu-id="32c81-151">Controleer of de vereiste headers aanwezig zijn (autorisatie, x-MS-Certificate-URL, x-MS-Signature-algoritme).</span><span class="sxs-lookup"><span data-stu-id="32c81-151">Verify the required headers are present (Authorization, x-ms-certificate-url, x-ms-signature-algorithm).</span></span>

2. <span data-ttu-id="32c81-152">Down load het certificaat dat wordt gebruikt om de inhoud te ondertekenen (x-MS-Certificate-URL).</span><span class="sxs-lookup"><span data-stu-id="32c81-152">Download the certificate used to sign the content (x-ms-certificate-url).</span></span>

3. <span data-ttu-id="32c81-153">Controleer de certificaat keten.</span><span class="sxs-lookup"><span data-stu-id="32c81-153">Verify the Certificate Chain.</span></span>

4. <span data-ttu-id="32c81-154">Controleer de organisatie van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="32c81-154">Verify the "Organization" of the certificate.</span></span>

5. <span data-ttu-id="32c81-155">Lees de inhoud met UTF8-code ring in een buffer.</span><span class="sxs-lookup"><span data-stu-id="32c81-155">Read the content with UTF8 encoding into a buffer.</span></span>

6. <span data-ttu-id="32c81-156">Maak een RSA crypto-provider.</span><span class="sxs-lookup"><span data-stu-id="32c81-156">Create an RSA Crypto Provider.</span></span>

7. <span data-ttu-id="32c81-157">Controleer of de gegevens overeenkomen met wat is ondertekend met het opgegeven hash-algoritme (bijvoorbeeld SHA256).</span><span class="sxs-lookup"><span data-stu-id="32c81-157">Verify the data matches what was signed with the specified hash algorithm (for example SHA256).</span></span>

8. <span data-ttu-id="32c81-158">Als de verificatie slaagt, verwerkt u het bericht.</span><span class="sxs-lookup"><span data-stu-id="32c81-158">If the verification succeeds, process the message.</span></span>

> [!NOTE]
> <span data-ttu-id="32c81-159">Het handtekening token wordt standaard verzonden in een autorisatie-header.</span><span class="sxs-lookup"><span data-stu-id="32c81-159">By default, the signature token will be sent in an Authorization header.</span></span> <span data-ttu-id="32c81-160">Als u in uw registratie **SignatureTokenToMsSignatureHeader** instelt op True, wordt het handtekening token in plaats daarvan in de x-MS-Signature-header verzonden.</span><span class="sxs-lookup"><span data-stu-id="32c81-160">If you set **SignatureTokenToMsSignatureHeader** to true in your registration, the signature token will be sent in the x-ms-signature header instead.</span></span>

## <a name="event-model"></a><span data-ttu-id="32c81-161">Gebeurtenis model</span><span class="sxs-lookup"><span data-stu-id="32c81-161">Event model</span></span>

<span data-ttu-id="32c81-162">In de volgende tabel worden de eigenschappen van een partner centrum-gebeurtenis beschreven.</span><span class="sxs-lookup"><span data-stu-id="32c81-162">The following table describes the properties of a Partner Center event.</span></span>

### <a name="properties"></a><span data-ttu-id="32c81-163">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="32c81-163">Properties</span></span>

| <span data-ttu-id="32c81-164">Naam</span><span class="sxs-lookup"><span data-stu-id="32c81-164">Name</span></span>                      | <span data-ttu-id="32c81-165">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32c81-165">Description</span></span>                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="32c81-166">**Gebeurtenisnaam**</span><span class="sxs-lookup"><span data-stu-id="32c81-166">**EventName**</span></span>             | <span data-ttu-id="32c81-167">De naam van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-167">The name of the event.</span></span> <span data-ttu-id="32c81-168">In de vorm {Resource}-{Action}.</span><span class="sxs-lookup"><span data-stu-id="32c81-168">In the form {resource}-{action}.</span></span> <span data-ttu-id="32c81-169">Bijvoorbeeld ' test-created '.</span><span class="sxs-lookup"><span data-stu-id="32c81-169">For example, "test-created".</span></span>  |
| <span data-ttu-id="32c81-170">**ResourceUri**</span><span class="sxs-lookup"><span data-stu-id="32c81-170">**ResourceUri**</span></span>           | <span data-ttu-id="32c81-171">De URI van de resource die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32c81-171">The URI of the resource that changed.</span></span>                                                 |
| <span data-ttu-id="32c81-172">**ResourceName**</span><span class="sxs-lookup"><span data-stu-id="32c81-172">**ResourceName**</span></span>          | <span data-ttu-id="32c81-173">De naam van de resource die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32c81-173">The name of the resource that changed.</span></span>                                                |
| <span data-ttu-id="32c81-174">**AuditUrl**</span><span class="sxs-lookup"><span data-stu-id="32c81-174">**AuditUrl**</span></span>              | <span data-ttu-id="32c81-175">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="32c81-175">Optional.</span></span> <span data-ttu-id="32c81-176">De URI van de controle record.</span><span class="sxs-lookup"><span data-stu-id="32c81-176">The URI of the Audit record.</span></span>                                                |
| <span data-ttu-id="32c81-177">**ResourceChangeUtcDate**</span><span class="sxs-lookup"><span data-stu-id="32c81-177">**ResourceChangeUtcDate**</span></span> | <span data-ttu-id="32c81-178">De datum en tijd, in UTC-notatie, wanneer de resource is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32c81-178">The date and time, in UTC format, when the resource change occurred.</span></span>                  |

### <a name="sample"></a><span data-ttu-id="32c81-179">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="32c81-179">Sample</span></span>

<span data-ttu-id="32c81-180">In het volgende voor beeld ziet u de structuur van een partner centrum gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-180">The following sample shows the structure of a Partner Center event.</span></span>

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a><span data-ttu-id="32c81-181">Webhook-Api's</span><span class="sxs-lookup"><span data-stu-id="32c81-181">Webhook APIs</span></span>

### <a name="authentication"></a><span data-ttu-id="32c81-182">Verificatie</span><span class="sxs-lookup"><span data-stu-id="32c81-182">Authentication</span></span>

<span data-ttu-id="32c81-183">Alle aanroepen naar de webhook-Api's worden geverifieerd met behulp van het Bearer-token in de autorisatie-header.</span><span class="sxs-lookup"><span data-stu-id="32c81-183">All calls to the Webhook APIs are authenticated using the Bearer token in the Authorization Header.</span></span> <span data-ttu-id="32c81-184">Verkrijg een toegangs token voor toegang `https://api.partnercenter.microsoft.com` .</span><span class="sxs-lookup"><span data-stu-id="32c81-184">Acquire an access token to access `https://api.partnercenter.microsoft.com`.</span></span> <span data-ttu-id="32c81-185">Dit token is hetzelfde token dat wordt gebruikt voor toegang tot de rest van de partner centrum-Api's.</span><span class="sxs-lookup"><span data-stu-id="32c81-185">This token is the same token that is used to access the rest of the Partner Center APIs.</span></span>

### <a name="get-a-list-of-events"></a><span data-ttu-id="32c81-186">Een lijst met gebeurtenissen ophalen</span><span class="sxs-lookup"><span data-stu-id="32c81-186">Get a list of events</span></span>

<span data-ttu-id="32c81-187">Retourneert een lijst met de gebeurtenissen die momenteel worden ondersteund door de webhook-Api's.</span><span class="sxs-lookup"><span data-stu-id="32c81-187">Returns a list of the events that are currently supported by the Webhook APIs.</span></span>

### <a name="resource-url"></a><span data-ttu-id="32c81-188">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-188">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/events`

### <a name="request-example"></a><span data-ttu-id="32c81-189">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-189">Request example</span></span>

```http
GET /webhooks/v1/registration/events
content-type: application/json
authorization: Bearer eyJ0e.......
accept: */*
host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="32c81-190">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-190">Response example</span></span>

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

### <a name="register-to-receive-events"></a><span data-ttu-id="32c81-191">Registreren voor het ontvangen van gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="32c81-191">Register to receive events</span></span>

<span data-ttu-id="32c81-192">Registreert een Tenant om de opgegeven gebeurtenissen te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="32c81-192">Registers a tenant to receive the specified events.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="32c81-193">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-193">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="32c81-194">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-194">Request example</span></span>

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

### <a name="response-example"></a><span data-ttu-id="32c81-195">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-195">Response example</span></span>

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

### <a name="view-a-registration"></a><span data-ttu-id="32c81-196">Een registratie weer geven</span><span class="sxs-lookup"><span data-stu-id="32c81-196">View a registration</span></span>

<span data-ttu-id="32c81-197">Retourneert de gebeurtenis registratie van webhooks voor een Tenant.</span><span class="sxs-lookup"><span data-stu-id="32c81-197">Returns the Webhooks event registration for a tenant.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="32c81-198">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-198">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="32c81-199">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-199">Request example</span></span>

```http
GET /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="32c81-200">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-200">Response example</span></span>

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

### <a name="update-an-event-registration"></a><span data-ttu-id="32c81-201">Een gebeurtenis registratie bijwerken</span><span class="sxs-lookup"><span data-stu-id="32c81-201">Update an event registration</span></span>

<span data-ttu-id="32c81-202">Hiermee wordt een bestaande gebeurtenis registratie bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="32c81-202">Updates an existing event registration.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="32c81-203">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-203">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="32c81-204">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-204">Request example</span></span>

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

### <a name="response-example"></a><span data-ttu-id="32c81-205">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-205">Response example</span></span>

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

### <a name="send-a-test-event-to-validate-your-registration"></a><span data-ttu-id="32c81-206">Een test gebeurtenis verzenden om uw registratie te valideren</span><span class="sxs-lookup"><span data-stu-id="32c81-206">Send a test event to validate your registration</span></span>

<span data-ttu-id="32c81-207">Hiermee wordt een test gebeurtenis gegenereerd om de registratie van webhooks te valideren.</span><span class="sxs-lookup"><span data-stu-id="32c81-207">Generates a test event to validate the Webhooks registration.</span></span> <span data-ttu-id="32c81-208">Deze test is bedoeld om te controleren of u gebeurtenissen van het partner centrum kunt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="32c81-208">This test is intended to validate that you can receive events from Partner Center.</span></span> <span data-ttu-id="32c81-209">De gegevens voor deze gebeurtenissen worden zeven dagen na het maken van de eerste gebeurtenis verwijderd.</span><span class="sxs-lookup"><span data-stu-id="32c81-209">Data for these events will be deleted seven days after the initial event is created.</span></span> <span data-ttu-id="32c81-210">Voordat u een validatie gebeurtenis verzendt, moet u zijn geregistreerd voor de gebeurtenis ' test-created ', met behulp van de registratie-API.</span><span class="sxs-lookup"><span data-stu-id="32c81-210">You must be registered for the "test-created" event, using the registration API, before sending a validation event.</span></span>

>[!NOTE]
><span data-ttu-id="32c81-211">Er geldt een limiet van twee aanvragen per minuut bij het boeken van een validatie gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-211">There is a throttle limit of 2 requests per minute when posting a validation event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="32c81-212">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-212">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents`

### <a name="request-example"></a><span data-ttu-id="32c81-213">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-213">Request example</span></span>

```http
POST /webhooks/v1/registration/validationEvents
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length:
```

### <a name="response-example"></a><span data-ttu-id="32c81-214">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-214">Response example</span></span>

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

### <a name="verify-that-the-event-was-delivered"></a><span data-ttu-id="32c81-215">Controleren of de gebeurtenis is bezorgd</span><span class="sxs-lookup"><span data-stu-id="32c81-215">Verify that the event was delivered</span></span>

<span data-ttu-id="32c81-216">Retourneert de huidige status van de validatie gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-216">Returns the current state of the validation event.</span></span> <span data-ttu-id="32c81-217">Deze verificatie kan nuttig zijn bij het oplossen van problemen met de levering van gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="32c81-217">This verification can be helpful for troubleshooting event delivery issues.</span></span> <span data-ttu-id="32c81-218">Het antwoord bevat een resultaat voor elke poging tot het leveren van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="32c81-218">The Response contains a result for each attempt that is made to deliver the event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="32c81-219">Resource-URL</span><span class="sxs-lookup"><span data-stu-id="32c81-219">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{correlationId}`

### <a name="request-example"></a><span data-ttu-id="32c81-220">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="32c81-220">Request example</span></span>

```http
GET /webhooks/v1/registration/validationEvents/04af2aea-d413-42db-824e-f328001484d1
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="32c81-221">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="32c81-221">Response example</span></span>

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

## <a name="example-for-signature-validation"></a><span data-ttu-id="32c81-222">Voor beeld voor handtekening validatie</span><span class="sxs-lookup"><span data-stu-id="32c81-222">Example for Signature Validation</span></span>

### <a name="sample-callback-controller-signature-aspnet"></a><span data-ttu-id="32c81-223">Voor beeld van een hand tekening voor een call back controller (ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="32c81-223">Sample Callback Controller signature (ASP.NET)</span></span>

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a><span data-ttu-id="32c81-224">Handtekening validatie</span><span class="sxs-lookup"><span data-stu-id="32c81-224">Signature Validation</span></span>

<span data-ttu-id="32c81-225">In het volgende voor beeld ziet u hoe u een autorisatie kenmerk toevoegt aan de controller die retour aanroepen ontvangt van webhook-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="32c81-225">The following example shows how to add an Authorization Attribute to the controller that is receiving callbacks from Webhook events.</span></span>

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
