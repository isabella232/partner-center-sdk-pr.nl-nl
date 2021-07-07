---
title: Resources voor overeenkomstmetagegevens
description: In de resourceverzameling AgreementMetadata worden overeenkomsttypen beschreven die partners kunnen gebruiken om de acceptatie van klanten te bevestigen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: b930e3691b9d269ddb8d76ae18b6b26a217123c0
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025622"
---
# <a name="agreement-metadata-resources"></a><span data-ttu-id="6ac03-103">Resources voor overeenkomstmetagegevens</span><span class="sxs-lookup"><span data-stu-id="6ac03-103">Agreement metadata resources</span></span>

<span data-ttu-id="6ac03-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="6ac03-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="6ac03-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6ac03-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6ac03-106">De **AgreementMetaData-resource** wordt momenteel alleen Partner Center in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ac03-106">The **AgreementMetaData** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span> 

<span data-ttu-id="6ac03-107">De **verzameling AgreementMetaData** bevat metagegevens over alle typen overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="6ac03-107">The **AgreementMetaData** collection provides metadata about all the agreement types.</span></span> <span data-ttu-id="6ac03-108">Partners kunnen deze verzameling gebruiken om de acceptatie van overeenkomsten door de klant te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="6ac03-108">Partners can use this collection to provide confirmation of customer acceptance of agreements.</span></span> <span data-ttu-id="6ac03-109">De **verzameling AgreementMetaData** retourneert metagegevens voor beide typen overeenkomst (**Microsoft Cloud-overeenkomst** en **Microsoft-klantovereenkomst**).</span><span class="sxs-lookup"><span data-stu-id="6ac03-109">The **AgreementMetaData** collection returns metadata for both agreement types (**Microsoft Cloud Agreement** and **Microsoft Customer Agreement**).</span></span>

## <a name="agreementmetadata"></a><span data-ttu-id="6ac03-110">AgreementMetaData</span><span class="sxs-lookup"><span data-stu-id="6ac03-110">AgreementMetaData</span></span>

<span data-ttu-id="6ac03-111">Geretourneerde overeenkomstmetagegevens bevatten de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="6ac03-111">Agreement metadata returned includes the following properties:</span></span>

| <span data-ttu-id="6ac03-112">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6ac03-112">Property</span></span>      | <span data-ttu-id="6ac03-113">Type</span><span class="sxs-lookup"><span data-stu-id="6ac03-113">Type</span></span>               | <span data-ttu-id="6ac03-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6ac03-114">Description</span></span>                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| <span data-ttu-id="6ac03-115">templateId</span><span class="sxs-lookup"><span data-stu-id="6ac03-115">templateId</span></span>    | <span data-ttu-id="6ac03-116">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6ac03-116">string</span></span>             | <span data-ttu-id="6ac03-117">Unieke id van een overeenkomstsjabloon.</span><span class="sxs-lookup"><span data-stu-id="6ac03-117">Unique identifier of an agreement template.</span></span>                                       |
| <span data-ttu-id="6ac03-118">type</span><span class="sxs-lookup"><span data-stu-id="6ac03-118">type</span></span>          | <span data-ttu-id="6ac03-119">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6ac03-119">string</span></span>             | <span data-ttu-id="6ac03-120">Overeenkomsttype.</span><span class="sxs-lookup"><span data-stu-id="6ac03-120">Agreement type.</span></span> <span data-ttu-id="6ac03-121">Momenteel zijn de ondersteunde **waarden MicrosoftCloudAgreement** **en MicrosoftCustomerAgreement** (preview).</span><span class="sxs-lookup"><span data-stu-id="6ac03-121">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement** (preview).</span></span> |
| <span data-ttu-id="6ac03-122">agreementLink</span><span class="sxs-lookup"><span data-stu-id="6ac03-122">agreementLink</span></span> | <span data-ttu-id="6ac03-123">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6ac03-123">string</span></span>             | <span data-ttu-id="6ac03-124">URL voor de overeenkomstsjabloon.</span><span class="sxs-lookup"><span data-stu-id="6ac03-124">URL for the agreement template.</span></span>                                                    |
