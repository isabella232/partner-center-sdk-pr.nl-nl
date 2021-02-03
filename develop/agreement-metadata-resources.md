---
title: Resources van de overeenkomst met meta gegevens
description: De resource verzameling AgreementMetadata beschrijft overeenkomst typen die partners kunnen gebruiken om de acceptatie van klanten te bevestigen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 36ba2aa2f78552dc9a835168b5bbd5b6a3ce47f3
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767207"
---
# <a name="agreement-metadata-resources"></a><span data-ttu-id="36922-103">Resources van de overeenkomst met meta gegevens</span><span class="sxs-lookup"><span data-stu-id="36922-103">Agreement metadata resources</span></span>

<span data-ttu-id="36922-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="36922-104">**Applies to:**</span></span>

- <span data-ttu-id="36922-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="36922-105">Partner Center</span></span>

<span data-ttu-id="36922-106">De **AgreementMetaData** -resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="36922-106">The **AgreementMetaData** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="36922-107">Deze resource is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="36922-107">This resource isn't applicable to:</span></span>

- <span data-ttu-id="36922-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="36922-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="36922-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="36922-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="36922-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="36922-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="36922-111">De **AgreementMetaData** -verzameling bevat meta gegevens over alle typen overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="36922-111">The **AgreementMetaData** collection provides metadata about all the agreement types.</span></span> <span data-ttu-id="36922-112">Partners kunnen deze verzameling gebruiken om een bevestiging van de acceptatie van de klant op te geven.</span><span class="sxs-lookup"><span data-stu-id="36922-112">Partners can use this collection to provide confirmation of customer acceptance of agreements.</span></span> <span data-ttu-id="36922-113">De **AgreementMetaData** -verzameling retourneert meta gegevens voor beide overeenkomst typen (**Microsoft Cloud overeenkomst** en **micro soft Customer Agreement**).</span><span class="sxs-lookup"><span data-stu-id="36922-113">The **AgreementMetaData** collection returns metadata for both agreement types (**Microsoft Cloud Agreement** and **Microsoft Customer Agreement**).</span></span>

## <a name="agreementmetadata"></a><span data-ttu-id="36922-114">AgreementMetaData</span><span class="sxs-lookup"><span data-stu-id="36922-114">AgreementMetaData</span></span>

<span data-ttu-id="36922-115">De geretourneerde meta gegevens van de overeenkomst bevatten de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="36922-115">Agreement metadata returned includes the following properties:</span></span>

| <span data-ttu-id="36922-116">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="36922-116">Property</span></span>      | <span data-ttu-id="36922-117">Type</span><span class="sxs-lookup"><span data-stu-id="36922-117">Type</span></span>               | <span data-ttu-id="36922-118">Description</span><span class="sxs-lookup"><span data-stu-id="36922-118">Description</span></span>                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| <span data-ttu-id="36922-119">Ontbrekende templateid</span><span class="sxs-lookup"><span data-stu-id="36922-119">templateId</span></span>    | <span data-ttu-id="36922-120">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="36922-120">string</span></span>             | <span data-ttu-id="36922-121">De unieke id van een overeenkomst sjabloon.</span><span class="sxs-lookup"><span data-stu-id="36922-121">Unique identifier of an agreement template.</span></span>                                       |
| <span data-ttu-id="36922-122">type</span><span class="sxs-lookup"><span data-stu-id="36922-122">type</span></span>          | <span data-ttu-id="36922-123">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="36922-123">string</span></span>             | <span data-ttu-id="36922-124">Type overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="36922-124">Agreement type.</span></span> <span data-ttu-id="36922-125">Op dit moment worden de volgende waarden ondersteund: **MicrosoftCloudAgreement** en **MicrosoftCustomerAgreement** (preview).</span><span class="sxs-lookup"><span data-stu-id="36922-125">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement** (preview).</span></span> |
| <span data-ttu-id="36922-126">agreementLink</span><span class="sxs-lookup"><span data-stu-id="36922-126">agreementLink</span></span> | <span data-ttu-id="36922-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="36922-127">string</span></span>             | <span data-ttu-id="36922-128">URL voor de overeenkomst sjabloon.</span><span class="sxs-lookup"><span data-stu-id="36922-128">URL for the agreement template.</span></span>                                                    |
