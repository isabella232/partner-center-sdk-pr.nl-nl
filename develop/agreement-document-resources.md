---
title: Resources voor overeenkomstdocument
description: De AgreementDocument-resource is een Microsoft-overeenkomstdocument voor preview en download. Dit wordt ondersteund door Partner Center in de openbare cloud van Microsoft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 1a81da4f75594f241669db831125bd437872561c
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025663"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a><span data-ttu-id="430a3-104">Documentbronnen voor overeenkomst die worden ondersteund door Partner Center in de openbare Cloud van Microsoft</span><span class="sxs-lookup"><span data-stu-id="430a3-104">Agreement document resources supported by Partner Center in the Microsoft public cloud</span></span>

<span data-ttu-id="430a3-105">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="430a3-105">**Applies to**: Partner Center</span></span>

<span data-ttu-id="430a3-106">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="430a3-106">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="430a3-107">De **AgreementDocument-resource** wordt momenteel alleen Partner Center in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="430a3-107">The **AgreementDocument** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="430a3-108">De **AgreementDocument-resource** vertegenwoordigt een Microsoft-overeenkomstdocument dat beschikbaar is als preview en download.</span><span class="sxs-lookup"><span data-stu-id="430a3-108">The **AgreementDocument** resource represents a Microsoft agreement document that is available for preview and download.</span></span>

## <a name="agreementdocument"></a><span data-ttu-id="430a3-109">AgreementDocument</span><span class="sxs-lookup"><span data-stu-id="430a3-109">AgreementDocument</span></span>

<span data-ttu-id="430a3-110">Een **AgreementDocument-resource** bevat de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="430a3-110">An **AgreementDocument** resource includes the following properties:</span></span>

| <span data-ttu-id="430a3-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="430a3-111">Property</span></span>       | <span data-ttu-id="430a3-112">Type</span><span class="sxs-lookup"><span data-stu-id="430a3-112">Type</span></span>   | <span data-ttu-id="430a3-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="430a3-113">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="430a3-114">country</span><span class="sxs-lookup"><span data-stu-id="430a3-114">country</span></span> | <span data-ttu-id="430a3-115">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="430a3-115">string</span></span> | <span data-ttu-id="430a3-116">Het land of de markt waarop dit document van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="430a3-116">The country or market to which this document applies.</span></span> |
| <span data-ttu-id="430a3-117">language</span><span class="sxs-lookup"><span data-stu-id="430a3-117">language</span></span> | <span data-ttu-id="430a3-118">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="430a3-118">string</span></span> | <span data-ttu-id="430a3-119">De taal waarin dit document is gelokaliseerd.</span><span class="sxs-lookup"><span data-stu-id="430a3-119">The language in which this document is localized.</span></span> |
| <span data-ttu-id="430a3-120">displayUri</span><span class="sxs-lookup"><span data-stu-id="430a3-120">displayUri</span></span> | <span data-ttu-id="430a3-121">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="430a3-121">string</span></span> | <span data-ttu-id="430a3-122">Een koppeling naar een voorbeeld van het overeenkomstdocument in een browser.</span><span class="sxs-lookup"><span data-stu-id="430a3-122">A link to preview the agreement document in a browser.</span></span>  |
| <span data-ttu-id="430a3-123">downloadUri</span><span class="sxs-lookup"><span data-stu-id="430a3-123">downloadUri</span></span> |<span data-ttu-id="430a3-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="430a3-124">string</span></span> | <span data-ttu-id="430a3-125">Een koppeling om het overeenkomstdocument te downloaden (in Microsoft Word indeling).</span><span class="sxs-lookup"><span data-stu-id="430a3-125">A link to download the agreement document (in Microsoft Word format).</span></span> |
