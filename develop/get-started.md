---
title: Aan de slag
description: De Partnercentrum-SDK bevat een beheerde API en een REST API die partners kunnen gebruiken om klant-, abonnements- en ordergegevens te beheren.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b5d05f26d63574ef876519091dc1c33c05f36e25
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548750"
---
# <a name="get-started"></a><span data-ttu-id="1d7e1-103">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="1d7e1-103">Get started</span></span>

<span data-ttu-id="1d7e1-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1d7e1-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1d7e1-105">De Partnercentrum-SDK bevat een beheerde API en een REST API die partners kunnen gebruiken om klant-, abonnements- en ordergegevens te beheren.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-105">The Partner Center SDK includes a managed API and a REST API for partners to use to manage customer, subscription, and order data.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="1d7e1-106">Code ophalen</span><span class="sxs-lookup"><span data-stu-id="1d7e1-106">Get the code</span></span>

[<span data-ttu-id="1d7e1-107">Download de Partnercentrum-SDK</span><span class="sxs-lookup"><span data-stu-id="1d7e1-107">Download the Partner Center SDK</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> <span data-ttu-id="1d7e1-108">API-toegang Partner Center voor indirecte resellers is geen ondersteund scenario.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-108">API access to Partner Center for indirect resellers isn't a supported scenario.</span></span>

## <a name="determine-your-version-of-partner-center"></a><span data-ttu-id="1d7e1-109">Uw versie van de Partner Center</span><span class="sxs-lookup"><span data-stu-id="1d7e1-109">Determine your version of Partner Center</span></span>

<span data-ttu-id="1d7e1-110">Sommige versies van Partner Center hebben niet de volledige SDK beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-110">Some versions of Partner Center do not have the entire SDK available.</span></span> <span data-ttu-id="1d7e1-111">Zie Developing for Partner Center for Microsoft National Cloud (Ontwikkelen voor [Partner Center voor Microsoft National Cloud) voor meer informatie.](developing-for-partner-center-for-microsoft-national-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-111">For more information, see [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span></span>

## <a name="get-the-samples"></a><span data-ttu-id="1d7e1-112">De voorbeelden op te halen</span><span class="sxs-lookup"><span data-stu-id="1d7e1-112">Get the samples</span></span>

<span data-ttu-id="1d7e1-113">Zie voorbeelden voor meer informatie over C#-fragmenten, REST-voorbeelden en de [voorbeeld-app Partner Center voorbeelden.](partner-center-samples.md)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-113">For more information about C# snippets, REST samples, and the sample app, see [Partner Center samples](partner-center-samples.md).</span></span>

## <a name="test-vs-production"></a><span data-ttu-id="1d7e1-114">Testen versus productie</span><span class="sxs-lookup"><span data-stu-id="1d7e1-114">Test vs. production</span></span>

<span data-ttu-id="1d7e1-115">Terwijl u uw code in eerste instantie schrijft en test, moet u uw sandbox-account voor integratie (en de bijbehorende tokens) gebruiken, zodat er niet per ongeluk nieuwe kosten in rekening worden gebracht die uw bedrijf moet betalen.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-115">While you are initially writing and testing your code, you should use your integration sandbox account (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying.</span></span> <span data-ttu-id="1d7e1-116">Zie API-toegang instellen in Partner Center voor meer informatie [over deze testomgeving.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-116">For more information about this testing environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).</span></span>

<span data-ttu-id="1d7e1-117">Wanneer uw oplossing is getest en klaar is voor gebruik in echte klantaccounts, moet u uw tokens bijwerken zodat u een Azure AD-client-app en -geheim gebruikt die overeenkomen met uw primaire Partner Center-account.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-117">When your solution is tested and ready to use on real customer accounts, you'll have to update your tokens so that you're using an Azure AD client app and secret that correspond to your Primary Partner Center account.</span></span>

<span data-ttu-id="1d7e1-118">Zie Testen en fouten opsporen voor tips en suggesties over testen en foutopsporing, [](test-and-debug.md)waaronder meer informatie over Test-in-Production (TiP) en de Integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-118">For tips and suggestions about testing and debugging, including more information about Test-in-Production (TiP) and the Integration Sandbox, see [Test and debug](test-and-debug.md).</span></span>

## <a name="configure-your-authentication"></a><span data-ttu-id="1d7e1-119">Uw verificatie configureren</span><span class="sxs-lookup"><span data-stu-id="1d7e1-119">Configure your authentication</span></span>

<span data-ttu-id="1d7e1-120">Zie Verificatie voor meer informatie over het configureren van Partner Center uw Azure AD Partner Center-verificatie, zodat u de Partner Center [API's kunt gebruiken.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-120">To configure your Azure AD authentication so that you can use the Partner Center APIs, see [Partner Center authentication](partner-center-authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d7e1-121">Microsoft introduceert een veilig, schaalbaar framework voor het authenticeren van CSP-partners (Cloud Solution Provider) en configuratieschermleveranciers (CPV) via de Microsoft Azure MFA-architectuur (Multi-Factor Authentication).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-121">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.</span></span>
<span data-ttu-id="1d7e1-122">Partner Center gebruikt Azure AD voor verificatie en voor het gebruik van de Partner Center API's moet u uw verificatie-instellingen correct configureren.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-122">Partner Center uses Azure AD for authentication, and to use the Partner Center APIs you must configure your authentication settings correctly.</span></span>
>
> <span data-ttu-id="1d7e1-123">Zie Secure Application [Model inschakelen voor meer informatie.](enable-secure-app-model.md)</span><span class="sxs-lookup"><span data-stu-id="1d7e1-123">For more information, see [Enable secure application model](enable-secure-app-model.md).</span></span>

## <a name="get-help"></a><span data-ttu-id="1d7e1-124">Hulp vragen</span><span class="sxs-lookup"><span data-stu-id="1d7e1-124">Get help</span></span>

<span data-ttu-id="1d7e1-125">Partners kunnen ondersteuning krijgen in de [Partnercentrum-SDK Yammer groep](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span><span class="sxs-lookup"><span data-stu-id="1d7e1-125">Partners can get support at the [Partner Center SDK Yammer group](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span></span> <span data-ttu-id="1d7e1-126">Ontwikkelaars kunnen hun MPN-ondersteuningsvoordelen of -voordelen gebruiken om persoonlijkere hulp te Premier Support.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-126">To get more personalized help, developers can use their MPN support benefits or Premier Support.</span></span>

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a><span data-ttu-id="1d7e1-127">Aanmelden voor het Early Adopter-programma voor API en SDK van Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1d7e1-127">Join the Partner Center API and SDK Early Adopter Program</span></span>

<span data-ttu-id="1d7e1-128">Zie Join the Partner Center API and SDK Early Adopter Program (Deelnemen aan de [Partner Center-API en SDK Early Adopter Program)](early-adopter-program.md)voor meer informatie over hoe u met Microsoft kunt samenwerken aan de ontwikkeling van partnerfuncties en -mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="1d7e1-128">To find out how you can collaborate with Microsoft on the development of Partner features and capabilities, see [Join the Partner Center API and SDK Early Adopter Program](early-adopter-program.md).</span></span>
