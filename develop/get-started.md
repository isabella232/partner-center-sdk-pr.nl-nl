---
title: Aan de slag
description: De partner centrum-SDK bevat een beheerde API en een REST API voor partners die moeten worden gebruikt voor het beheren van gegevens van klanten, abonnementen en orders.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9c2af1e11dbda19489a27e37c7f3de8ede90fd1c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767280"
---
# <a name="get-started"></a><span data-ttu-id="8857a-103">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="8857a-103">Get started</span></span>

<span data-ttu-id="8857a-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="8857a-104">**Applies To**</span></span>

- <span data-ttu-id="8857a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="8857a-105">Partner Center</span></span>
- <span data-ttu-id="8857a-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="8857a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="8857a-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="8857a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8857a-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8857a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8857a-109">De partner centrum-SDK bevat een beheerde API en een REST API voor partners die moeten worden gebruikt voor het beheren van gegevens van klanten, abonnementen en orders.</span><span class="sxs-lookup"><span data-stu-id="8857a-109">The Partner Center SDK includes a managed API and a REST API for partners to use to manage customer, subscription, and order data.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="8857a-110">Code ophalen</span><span class="sxs-lookup"><span data-stu-id="8857a-110">Get the code</span></span>

[<span data-ttu-id="8857a-111">De Partner Center-SDK downloaden</span><span class="sxs-lookup"><span data-stu-id="8857a-111">Download the Partner Center SDK</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> <span data-ttu-id="8857a-112">API-toegang tot het partner centrum voor indirecte wederverkopers is geen ondersteund scenario.</span><span class="sxs-lookup"><span data-stu-id="8857a-112">API access to Partner Center for indirect resellers isn't a supported scenario.</span></span>

## <a name="determine-your-version-of-partner-center"></a><span data-ttu-id="8857a-113">Uw versie van partner centrum bepalen</span><span class="sxs-lookup"><span data-stu-id="8857a-113">Determine your version of Partner Center</span></span>

<span data-ttu-id="8857a-114">Voor sommige versies van partner Center is de volledige SDK niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="8857a-114">Some versions of Partner Center do not have the entire SDK available.</span></span> <span data-ttu-id="8857a-115">Zie [ontwikkelen voor Partner Center voor micro soft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8857a-115">For more information, see [Developing for Partner Center for Microsoft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md).</span></span>

## <a name="get-the-samples"></a><span data-ttu-id="8857a-116">De voor beelden ophalen</span><span class="sxs-lookup"><span data-stu-id="8857a-116">Get the samples</span></span>

<span data-ttu-id="8857a-117">Zie voor meer informatie over C#-fragmenten, REST-voor beelden en de voor beeld-app [Partner Center](partner-center-samples.md)-voor beelden.</span><span class="sxs-lookup"><span data-stu-id="8857a-117">For more information about C# snippets, REST samples, and the sample app, see [Partner Center samples](partner-center-samples.md).</span></span>

## <a name="test-vs-production"></a><span data-ttu-id="8857a-118">Testen versus productie</span><span class="sxs-lookup"><span data-stu-id="8857a-118">Test vs. production</span></span>

<span data-ttu-id="8857a-119">Terwijl u uw code voor het eerst schrijft en test, moet u uw account voor de integratie sandbox (en de bijbehorende tokens) gebruiken, zodat u niet per ongeluk nieuwe kosten maakt die uw bedrijf verantwoordelijk is voor de betaling.</span><span class="sxs-lookup"><span data-stu-id="8857a-119">While you are initially writing and testing your code, you should use your integration sandbox account (and the corresponding tokens) so that you don't accidentally incur new charges that your company is responsible for paying.</span></span> <span data-ttu-id="8857a-120">Zie [API-toegang instellen in Partner Center](set-up-api-access-in-partner-center.md)voor meer informatie over deze test omgeving.</span><span class="sxs-lookup"><span data-stu-id="8857a-120">For more information about this testing environment, see [Set up API access in Partner Center](set-up-api-access-in-partner-center.md).</span></span>

<span data-ttu-id="8857a-121">Wanneer uw oplossing is getest en gereed is voor gebruik op echte klant accounts, moet u uw tokens bijwerken zodat u een Azure AD-client-app en een geheim gebruikt dat overeenkomt met uw primaire partner centrum-account.</span><span class="sxs-lookup"><span data-stu-id="8857a-121">When your solution is tested and ready to use on real customer accounts, you'll have to update your tokens so that you're using an Azure AD client app and secret that correspond to your Primary Partner Center account.</span></span>

<span data-ttu-id="8857a-122">Voor tips en suggesties over testen en fout opsporing, met inbegrip van meer informatie over test-in-productie (TiP) en de integratie sandbox, Zie [testen en fouten opsporen](test-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="8857a-122">For tips and suggestions about testing and debugging, including more information about Test-in-Production (TiP) and the Integration Sandbox, see [Test and debug](test-and-debug.md).</span></span>

## <a name="configure-your-authentication"></a><span data-ttu-id="8857a-123">Uw authenticatie configureren</span><span class="sxs-lookup"><span data-stu-id="8857a-123">Configure your authentication</span></span>

<span data-ttu-id="8857a-124">Zie [Partner Center-verificatie](partner-center-authentication.md)voor meer informatie over het configureren van uw Azure AD-verificatie zodat u de partner centrum-api's kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8857a-124">To configure your Azure AD authentication so that you can use the Partner Center APIs, see [Partner Center authentication](partner-center-authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8857a-125">Micro soft introduceert een veilig, schaalbaar Framework voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van configuratie schermen (CPV) via de Microsoft Azure multi-factor Authentication-architectuur (MFA).</span><span class="sxs-lookup"><span data-stu-id="8857a-125">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.</span></span>
<span data-ttu-id="8857a-126">Het partner centrum gebruikt Azure AD voor verificatie en voor het gebruik van de Api's van het partner centrum moet u uw verificatie-instellingen op de juiste wijze configureren.</span><span class="sxs-lookup"><span data-stu-id="8857a-126">Partner Center uses Azure AD for authentication, and to use the Partner Center APIs you must configure your authentication settings correctly.</span></span>
>
> <span data-ttu-id="8857a-127">Zie [Enable Secure Application model](enable-secure-app-model.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8857a-127">For more information, see [Enable secure application model](enable-secure-app-model.md).</span></span>

## <a name="get-help"></a><span data-ttu-id="8857a-128">Hulp vragen</span><span class="sxs-lookup"><span data-stu-id="8857a-128">Get help</span></span>

<span data-ttu-id="8857a-129">Partners kunnen ondersteuning krijgen via de [Partner Center SDK Yammer-groep](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span><span class="sxs-lookup"><span data-stu-id="8857a-129">Partners can get support at the [Partner Center SDK Yammer group](https://go.microsoft.com/fwlink/p/?LinkID=717360).</span></span> <span data-ttu-id="8857a-130">Ontwikkel aars kunnen hun MPN-ondersteunings voordelen of-Premier Support gebruiken om meer persoonlijke hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="8857a-130">To get more personalized help, developers can use their MPN support benefits or Premier Support.</span></span>

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a><span data-ttu-id="8857a-131">Aanmelden voor het Early Adopter-programma voor API en SDK van Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="8857a-131">Join the Partner Center API and SDK Early Adopter Program</span></span>

<span data-ttu-id="8857a-132">Zie voor meer informatie over hoe u kunt samen werken met micro soft aan de hand van de functies en mogelijkheden van [de partner de Partner Center API en SDK Early passer Program](early-adopter-program.md).</span><span class="sxs-lookup"><span data-stu-id="8857a-132">To find out how you can collaborate with Microsoft on the development of Partner features and capabilities, see [Join the Partner Center API and SDK Early Adopter Program](early-adopter-program.md).</span></span>
