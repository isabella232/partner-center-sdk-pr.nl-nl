---
title: Document bronnen van de overeenkomst
description: De AgreementDocument-resource is een micro soft-overeenkomst document voor preview en down load. Het wordt ondersteund door het partner centrum in de open bare cloud van micro soft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 4805d25b0838bf922b81bebd998810c3f6a809c3
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767604"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a><span data-ttu-id="5bbbb-104">Document bronnen van de overeenkomst die worden ondersteund door het partner centrum in de open bare cloud van micro soft</span><span class="sxs-lookup"><span data-stu-id="5bbbb-104">Agreement document resources supported by Partner Center in the Microsoft public cloud</span></span>

<span data-ttu-id="5bbbb-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="5bbbb-105">**Applies to:**</span></span>

- <span data-ttu-id="5bbbb-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5bbbb-106">Partner Center</span></span>

<span data-ttu-id="5bbbb-107">De **AgreementDocument** -resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-107">The **AgreementDocument** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="5bbbb-108">Deze resource is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="5bbbb-108">This resource not applicable to:</span></span>

- <span data-ttu-id="5bbbb-109">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5bbbb-109">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5bbbb-110">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="5bbbb-110">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5bbbb-111">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5bbbb-111">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5bbbb-112">De resource **AgreementDocument** vertegenwoordigt een micro soft-overeenkomst document dat beschikbaar is voor preview en down load.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-112">The **AgreementDocument** resource represents a Microsoft agreement document that is available for preview and download.</span></span>

## <a name="agreementdocument"></a><span data-ttu-id="5bbbb-113">AgreementDocument</span><span class="sxs-lookup"><span data-stu-id="5bbbb-113">AgreementDocument</span></span>

<span data-ttu-id="5bbbb-114">Een **AgreementDocument** -resource bevat de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="5bbbb-114">An **AgreementDocument** resource includes the following properties:</span></span>

| <span data-ttu-id="5bbbb-115">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5bbbb-115">Property</span></span>       | <span data-ttu-id="5bbbb-116">Type</span><span class="sxs-lookup"><span data-stu-id="5bbbb-116">Type</span></span>   | <span data-ttu-id="5bbbb-117">Description</span><span class="sxs-lookup"><span data-stu-id="5bbbb-117">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5bbbb-118">country</span><span class="sxs-lookup"><span data-stu-id="5bbbb-118">country</span></span> | <span data-ttu-id="5bbbb-119">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bbbb-119">string</span></span> | <span data-ttu-id="5bbbb-120">Het land of de markt waarop dit document van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-120">The country or market to which this document applies.</span></span> |
| <span data-ttu-id="5bbbb-121">language</span><span class="sxs-lookup"><span data-stu-id="5bbbb-121">language</span></span> | <span data-ttu-id="5bbbb-122">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bbbb-122">string</span></span> | <span data-ttu-id="5bbbb-123">De taal waarin dit document is gelokaliseerd.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-123">The language in which this document is localized.</span></span> |
| <span data-ttu-id="5bbbb-124">displayUri</span><span class="sxs-lookup"><span data-stu-id="5bbbb-124">displayUri</span></span> | <span data-ttu-id="5bbbb-125">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bbbb-125">string</span></span> | <span data-ttu-id="5bbbb-126">Een koppeling om een voor beeld van het overeenkomst document in een browser te bekijken.</span><span class="sxs-lookup"><span data-stu-id="5bbbb-126">A link to preview the agreement document in a browser.</span></span>  |
| <span data-ttu-id="5bbbb-127">downloadUri</span><span class="sxs-lookup"><span data-stu-id="5bbbb-127">downloadUri</span></span> |<span data-ttu-id="5bbbb-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bbbb-128">string</span></span> | <span data-ttu-id="5bbbb-129">Een koppeling voor het downloaden van het overeenkomst document (in micro soft Word-indeling).</span><span class="sxs-lookup"><span data-stu-id="5bbbb-129">A link to download the agreement document (in Microsoft Word format).</span></span> |
