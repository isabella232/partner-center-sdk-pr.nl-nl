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
# <a name="partner-center-webhooks"></a>Partnercentrum-webhooks

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Met de webhook-Api's van partner Center kunnen partners zich registreren voor bron wijzigings gebeurtenissen. Deze gebeurtenissen worden in de vorm van HTTP-berichten verzonden naar de geregistreerde URL van de partner. Als u een gebeurtenis van het partner centrum wilt ontvangen, hosten partners een call back waarbij het partner centrum de wijzigings gebeurtenis van de resource kan posten. De gebeurtenis wordt digitaal ondertekend, zodat de partner kan controleren of deze is verzonden vanuit het partner centrum.

Partners kunnen een keuze maken uit webhook-gebeurtenissen, zoals de volgende voor beelden, die worden ondersteund door het partner centrum.

- **Test gebeurtenis ("test-created")**

    Met deze gebeurtenis kunt u zelf onboards en uw registratie testen door een test gebeurtenis aan te vragen en de voortgang op te sporen. U kunt de fout berichten bekijken die van micro soft worden ontvangen tijdens het leveren van de gebeurtenis. Deze beperking is alleen van toepassing op gebeurtenissen die zijn gemaakt met een test. Gegevens die ouder zijn dan zeven dagen worden verwijderd.

- **Bijgewerkte gebeurtenis van abonnement (abonnement-bijgewerkt)**

    Deze gebeurtenis treedt op wanneer het abonnement wordt gewijzigd. Deze gebeurtenissen worden gegenereerd wanneer er een interne wijziging in aanvulling is op wanneer wijzigingen worden aangebracht via de partner centrum-API.

    >[!NOTE]
    >Er is een vertraging van Maxi maal 48 uur tussen het tijdstip waarop een abonnement wijzigt en wanneer de gebeurtenis bijgewerkt abonnement wordt geactiveerd.

- **Gebeurtenis drempelwaarde overschreden ("usagerecords-thresholdExceeded")**

    Deze gebeurtenis treedt op wanneer de hoeveelheid Microsoft Azure gebruik voor een klant groter is dan het bestedings budget van het gebruik (de drempel waarde). Zie voor meer informatie [een Azure-uitgaven budget instellen voor uw klanten/Partner-Center/set-a-Azure-besteding-budget-voor-uw klanten).

- **Gebeurtenis voor het maken van een referral (' verwijzing-gemaakt ')**

    Deze gebeurtenis treedt op wanneer de verwijzing wordt gemaakt.

- **De gebeurtenis Referral update (' verwijzing-bijgewerkt ')**

    Deze gebeurtenis treedt op wanneer de verwijzing wordt bijgewerkt.

- **Factuur gereed gebeurtenis ("factuur gereed")**

    Deze gebeurtenis treedt op wanneer de nieuwe factuur gereed is.

Toekomstige webhook-gebeurtenissen worden toegevoegd voor resources die veranderen in het systeem waarvan de partner niet in beheer is, en er worden verdere updates uitgevoerd om deze gebeurtenissen zo snel mogelijk op te halen. Feedback van partners over welke gebeurtenissen een waarde toevoegen aan hun bedrijf is handig om te bepalen welke nieuwe gebeurtenissen moeten worden toegevoegd.

Zie [Partner Center-gebeurtenissen voor webhooks](partner-center-webhook-events.md)voor een volledige lijst van webhook-gebeurtenissen die worden ondersteund door het partner centrum.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

## <a name="receiving-events-from-partner-center"></a>Gebeurtenissen ontvangen van het partner centrum

Als u gebeurtenissen van het partner centrum wilt ontvangen, moet u een openbaar toegankelijk eind punt zichtbaar maken. Omdat dit eind punt wordt weer gegeven, moet u controleren of de communicatie van het partner centrum is. Alle webhook-gebeurtenissen die u ontvangt, worden digitaal ondertekend met een certificaat dat is gekoppeld aan de micro soft root. Er wordt ook een koppeling weer gegeven naar het certificaat dat wordt gebruikt om de gebeurtenis te ondertekenen. Hierdoor kan het certificaat worden vernieuwd zonder dat u uw service opnieuw hoeft te implementeren of opnieuw te configureren. Het partner centrum maakt 10 pogingen om de gebeurtenis te leveren. Als de gebeurtenis na 10 pogingen nog niet is bezorgd, wordt deze naar een offline wachtrij verplaatst en worden er geen nieuwe pogingen gedaan bij de levering.

In het volgende voor beeld ziet u een gebeurtenis die is gepost vanuit het partner centrum.

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
>De autorisatie-header heeft het schema hand tekening. Dit is een met base64 gecodeerde hand tekening van de inhoud.

## <a name="how-to-authenticate-the-callback"></a>De call back verifiëren

Voer de volgende stappen uit om de retour aanroep gebeurtenis te verifiëren die is ontvangen van het partner centrum:

1. Controleer of de vereiste headers aanwezig zijn (autorisatie, x-MS-Certificate-URL, x-MS-Signature-algoritme).

2. Down load het certificaat dat wordt gebruikt om de inhoud te ondertekenen (x-MS-Certificate-URL).

3. Controleer de certificaat keten.

4. Controleer de organisatie van het certificaat.

5. Lees de inhoud met UTF8-code ring in een buffer.

6. Maak een RSA crypto-provider.

7. Controleer of de gegevens overeenkomen met wat is ondertekend met het opgegeven hash-algoritme (bijvoorbeeld SHA256).

8. Als de verificatie slaagt, verwerkt u het bericht.

> [!NOTE]
> Het handtekening token wordt standaard verzonden in een autorisatie-header. Als u in uw registratie **SignatureTokenToMsSignatureHeader** instelt op True, wordt het handtekening token in plaats daarvan in de x-MS-Signature-header verzonden.

## <a name="event-model"></a>Gebeurtenis model

In de volgende tabel worden de eigenschappen van een partner centrum-gebeurtenis beschreven.

### <a name="properties"></a>Eigenschappen

| Naam                      | Beschrijving                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| **Gebeurtenisnaam**             | De naam van de gebeurtenis. In de vorm {Resource}-{Action}. Bijvoorbeeld ' test-created '.  |
| **ResourceUri**           | De URI van de resource die is gewijzigd.                                                 |
| **ResourceName**          | De naam van de resource die is gewijzigd.                                                |
| **AuditUrl**              | Optioneel. De URI van de controle record.                                                |
| **ResourceChangeUtcDate** | De datum en tijd, in UTC-notatie, wanneer de resource is gewijzigd.                  |

### <a name="sample"></a>Voorbeeld

In het volgende voor beeld ziet u de structuur van een partner centrum gebeurtenis.

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a>Webhook-Api's

### <a name="authentication"></a>Verificatie

Alle aanroepen naar de webhook-Api's worden geverifieerd met behulp van het Bearer-token in de autorisatie-header. Verkrijg een toegangs token voor toegang `https://api.partnercenter.microsoft.com` . Dit token is hetzelfde token dat wordt gebruikt voor toegang tot de rest van de partner centrum-Api's.

### <a name="get-a-list-of-events"></a>Een lijst met gebeurtenissen ophalen

Retourneert een lijst met de gebeurtenissen die momenteel worden ondersteund door de webhook-Api's.

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

### <a name="register-to-receive-events"></a>Registreren voor het ontvangen van gebeurtenissen

Registreert een Tenant om de opgegeven gebeurtenissen te ontvangen.

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

### <a name="view-a-registration"></a>Een registratie weer geven

Retourneert de gebeurtenis registratie van webhooks voor een Tenant.

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

### <a name="update-an-event-registration"></a>Een gebeurtenis registratie bijwerken

Hiermee wordt een bestaande gebeurtenis registratie bijgewerkt.

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

### <a name="send-a-test-event-to-validate-your-registration"></a>Een test gebeurtenis verzenden om uw registratie te valideren

Hiermee wordt een test gebeurtenis gegenereerd om de registratie van webhooks te valideren. Deze test is bedoeld om te controleren of u gebeurtenissen van het partner centrum kunt ontvangen. De gegevens voor deze gebeurtenissen worden zeven dagen na het maken van de eerste gebeurtenis verwijderd. Voordat u een validatie gebeurtenis verzendt, moet u zijn geregistreerd voor de gebeurtenis ' test-created ', met behulp van de registratie-API.

>[!NOTE]
>Er geldt een limiet van twee aanvragen per minuut bij het boeken van een validatie gebeurtenis.

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

### <a name="verify-that-the-event-was-delivered"></a>Controleren of de gebeurtenis is bezorgd

Retourneert de huidige status van de validatie gebeurtenis. Deze verificatie kan nuttig zijn bij het oplossen van problemen met de levering van gebeurtenissen. Het antwoord bevat een resultaat voor elke poging tot het leveren van de gebeurtenis.

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

## <a name="example-for-signature-validation"></a>Voor beeld voor handtekening validatie

### <a name="sample-callback-controller-signature-aspnet"></a>Voor beeld van een hand tekening voor een call back controller (ASP.NET)

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a>Handtekening validatie

In het volgende voor beeld ziet u hoe u een autorisatie kenmerk toevoegt aan de controller die retour aanroepen ontvangt van webhook-gebeurtenissen.

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
