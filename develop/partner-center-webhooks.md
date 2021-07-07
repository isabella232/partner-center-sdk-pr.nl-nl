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
# <a name="partner-center-webhooks"></a>Partnercentrum-webhooks

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Met Partner Center webhook-API's kunnen partners zich registreren voor resourcewijzigingsgebeurtenissen. Deze gebeurtenissen worden geleverd in de vorm van HTTP POST's aan de geregistreerde URL van de partner. Als partners een gebeurtenis van Partner Center ontvangen, hosten ze een callback waar Partner Center de gebeurtenis van de resourcewijziging kan plaatsen. De gebeurtenis wordt digitaal ondertekend, zodat de partner kan controleren of deze is verzonden vanuit Partner Center.

Partners kunnen kiezen uit webhookgebeurtenissen, zoals de volgende voorbeelden, die worden ondersteund door Partner Center.

- **Testgebeurtenis ('test gemaakt')**

    Met deze gebeurtenis kunt u uw registratie zelf onboarden en testen door een testgebeurtenis aan te vragen en vervolgens de voortgang ervan bij te houden. U kunt de foutberichten zien die van Microsoft worden ontvangen tijdens het leveren van de gebeurtenis. Deze beperking is alleen van toepassing op gebeurtenissen die zijn gemaakt door een test. Gegevens ouder dan zeven dagen worden verwijderd.

- **Gebeurtenis bijgewerkt abonnement ('abonnement bijgewerkt')**

    Deze gebeurtenis wordt aan het werk gesteld wanneer het abonnement wordt gewijzigd. Deze gebeurtenissen worden gegenereerd wanneer er een interne wijziging is naast wanneer wijzigingen worden aangebracht via de Partner Center API.

    >[!NOTE]
    >Er is een vertraging van maximaal 48 uur tussen het moment waarop een abonnement wordt gewijzigd en het moment waarop de gebeurtenis Abonnement bijgewerkt wordt geactiveerd.

- **Drempelwaarde overschreden gebeurtenis ('usagerecords-thresholdExceeded')**

    Deze gebeurtenis teert wanneer de hoeveelheid Microsoft Azure voor elke klant het gebruiksuitgavenbudget (hun drempelwaarde) overschrijdt. Zie [Een Azure-uitgavenbudget instellen voor uw klanten/partnercentrum/set-an-azure-spending-budget-for-your-customers) voor meer informatie.

- **Door verwijzing gemaakte gebeurtenis ("verwijzing gemaakt")**

    Deze gebeurtenis wordt aangemaakt wanneer de verwijzing wordt gemaakt.

- **Gebeurtenis bijgewerkt door verwijzing ('verwijzing bijgewerkt')**

    Deze gebeurtenis wordt aan de orde gesteld wanneer de verwijzing wordt bijgewerkt.

- **Gebeurtenis gereed voor factuur ('factuur gereed')**

    Deze gebeurtenis wordt verhoogd wanneer de nieuwe factuur gereed is.

Toekomstige webhookgebeurtenissen worden toegevoegd voor resources die wijzigen in het systeem waar de partner geen controle over heeft, en er worden verdere updates aangebracht om deze gebeurtenissen zo dicht mogelijk bij 'realtime' te krijgen. Feedback van partners over welke gebeurtenissen waarde toevoegen aan hun bedrijf, is handig om te bepalen welke nieuwe gebeurtenissen moeten worden toevoegen.

Zie webhookgebeurtenissen voor een volledige Partner Center [webhookgebeurtenissen Partner Center webhookgebeurtenissen.](partner-center-webhook-events.md)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

## <a name="receiving-events-from-partner-center"></a>Gebeurtenissen ontvangen van Partner Center

Als u gebeurtenissen van Partner Center, moet u een openbaar toegankelijk eindpunt beschikbaar maken. Omdat dit eindpunt wordt blootgesteld, moet u controleren of de communicatie afkomstig is van Partner Center. Alle webhookgebeurtenissen die u ontvangt, worden digitaal ondertekend met een certificaat dat is geketend aan microsoft Root. Er wordt ook een koppeling naar het certificaat gegeven dat wordt gebruikt om de gebeurtenis te ondertekenen. Hierdoor kan het certificaat worden vernieuwd zonder dat u uw service opnieuw moet configureren of opnieuw moet configureren. Partner Center zal 10 pogingen doen om de gebeurtenis te leveren. Als de gebeurtenis na tien pogingen nog steeds niet wordt geleverd, wordt deze verplaatst naar een offlinewachtrij en worden er geen verdere pogingen gedaan bij levering.

In het volgende voorbeeld ziet u een gebeurtenis die is gepost vanuit Partner Center.

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
>De autorisatieheader heeft een schema van 'Handtekening'. Dit is een base64 gecodeerde handtekening van de inhoud.

## <a name="how-to-authenticate-the-callback"></a>De callback verifiëren

Volg deze stappen om de callbackgebeurtenis te verifiëren die Partner Center ontvangen:

1. Controleer of de vereiste headers aanwezig zijn (Authorization, x-ms-certificate-url, x-ms-signature-algorithm).

2. Download het certificaat dat wordt gebruikt om de inhoud te ondertekenen (x-ms-certificate-url).

3. Controleer de certificaatketen.

4. Controleer de organisatie van het certificaat.

5. Lees de inhoud met UTF8-codering in een buffer.

6. Maak een RSA Crypto Provider.

7. Controleer of de gegevens overeenkomt met wat is ondertekend met het opgegeven hash-algoritme (bijvoorbeeld SHA256).

8. Als de verificatie is geslaagd, verwerkt u het bericht.

> [!NOTE]
> Standaard wordt het handtekening-token verzonden in een Autorisatie-header. Als u **SignatureTokenToMsSignatureHeader** in uw registratie in uw registratie in stelt op true, wordt het handtekeningtoken in plaats daarvan verzonden in de x-ms-signature-header.

## <a name="event-model"></a>Gebeurtenismodel

In de volgende tabel worden de eigenschappen van een Partner Center beschreven.

### <a name="properties"></a>Eigenschappen

| Naam                      | Beschrijving                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| **Gebeurtenisnaam**             | De naam van de gebeurtenis. In de vorm {resource}-{action}. Bijvoorbeeld 'test-created'.  |
| **ResourceUri**           | De URI van de resource die is gewijzigd.                                                 |
| **Resourcename**          | De naam van de resource die is gewijzigd.                                                |
| **AuditUrl**              | Optioneel. De URI van de controlerecord.                                                |
| **ResourceChangeUtcDate** | De datum en tijd, in UTC-indeling, waarop de resource is gewijzigd.                  |

### <a name="sample"></a>Voorbeeld

In het volgende voorbeeld ziet u de structuur van een Partner Center gebeurtenis.

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a>Webhook-API's

### <a name="authentication"></a>Verificatie

Alle aanroepen naar de Webhook-API's worden geverifieerd met behulp van het Bearer-token in de autorisatieheader. Een toegangs token verkrijgen voor toegang `https://api.partnercenter.microsoft.com` tot . Dit token is hetzelfde token dat wordt gebruikt voor toegang tot de rest van de Partner Center API's.

### <a name="get-a-list-of-events"></a>Een lijst met gebeurtenissen op halen

Retourneert een lijst met de gebeurtenissen die momenteel worden ondersteund door de Webhook-API's.

### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/events`

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET /webhooks/v1/registration/events
content-type: application/json
authorization: Bearer eyJ0e.......
accept: */*
host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a>Voorbeeld van antwoord

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

### <a name="register-to-receive-events"></a>Registreren om gebeurtenissen te ontvangen

Registreert een tenant voor het ontvangen van de opgegeven gebeurtenissen.

#### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Voorbeeld van aanvraag

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

### <a name="response-example"></a>Voorbeeld van antwoord

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

### <a name="view-a-registration"></a>Een registratie weergeven

Retourneert de webhooksgebeurtenisregistratie voor een tenant.

#### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a>Voorbeeld van antwoord

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

### <a name="update-an-event-registration"></a>Een gebeurtenisregistratie bijwerken

Werkt een bestaande gebeurtenisregistratie bij.

#### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Voorbeeld van aanvraag

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

### <a name="response-example"></a>Voorbeeld van antwoord

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

### <a name="send-a-test-event-to-validate-your-registration"></a>Een testgebeurtenis verzenden om uw registratie te valideren

Genereert een testgebeurtenis om de webhooksregistratie te valideren. Deze test is bedoeld om te controleren of u gebeurtenissen kunt ontvangen van Partner Center. Gegevens voor deze gebeurtenissen worden zeven dagen na het maken van de eerste gebeurtenis verwijderd. U moet zijn geregistreerd voor de gebeurtenis 'test gemaakt' met behulp van de registratie-API voordat u een validatiegebeurtenis verstuurt.

>[!NOTE]
>Er is een vertragingslimiet van 2 aanvragen per minuut bij het plaatsen van een validatiegebeurtenis.

#### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents`

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST /webhooks/v1/registration/validationEvents
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length:
```

### <a name="response-example"></a>Voorbeeld van antwoord

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

### <a name="verify-that-the-event-was-delivered"></a>Controleren of de gebeurtenis is geleverd

Retourneert de huidige status van de validatiegebeurtenis. Deze verificatie kan handig zijn voor het oplossen van problemen met de levering van gebeurtenissen. Het antwoord bevat een resultaat voor elke poging om de gebeurtenis te leveren.

#### <a name="resource-url"></a>Resource-URL

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{correlationId}`

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET /webhooks/v1/registration/validationEvents/04af2aea-d413-42db-824e-f328001484d1
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a>Voorbeeld van antwoord

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

## <a name="example-for-signature-validation"></a>Voorbeeld voor handtekeningvalidatie

### <a name="sample-callback-controller-signature-aspnet"></a>Voorbeeld van callback-controllerhandtekening (ASP.NET)

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a>Handtekeningvalidatie

In het volgende voorbeeld ziet u hoe u een autorisatiekenmerk toevoegt aan de controller die callbacks van webhookgebeurtenissen ontvangt.

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
