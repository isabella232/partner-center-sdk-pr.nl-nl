---
title: De status van direct ondertekenen (direct accepteren) van een klant overeenkomst.
description: De resource DirectSignedCustomerAgreementStatus vertegenwoordigt de status van de directe ondertekening (directe acceptatie) van een klant overeenkomst.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 9c4fd12ac3319057f3c4034aa0c8d93dcda726c6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767193"
---
# <a name="direct-signing-direct-acceptance-status-of-a-customer-agreement"></a><span data-ttu-id="6472b-103">Status van direct ondertekenen (direct geaccepteerd) van een klant overeenkomst</span><span class="sxs-lookup"><span data-stu-id="6472b-103">Direct signing (direct acceptance) status of a customer agreement</span></span>

<span data-ttu-id="6472b-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="6472b-104">**Applies to:**</span></span>

- <span data-ttu-id="6472b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6472b-105">Partner Center</span></span>

<span data-ttu-id="6472b-106">De **DirectSignedCustomerAgreementStatus** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="6472b-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="6472b-107">Deze resource is *niet van toepassing* op:</span><span class="sxs-lookup"><span data-stu-id="6472b-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="6472b-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6472b-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6472b-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6472b-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6472b-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6472b-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6472b-111">De **DirectSignedCustomerAgreementStatus** -resource vertegenwoordigt de status van de directe acceptatie van een klant overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="6472b-111">The **DirectSignedCustomerAgreementStatus** resource represents the status of the direct acceptance of a customer agreement.</span></span>

## <a name="directsignedcustomeragreementstatus"></a><span data-ttu-id="6472b-112">DirectSignedCustomerAgreementStatus</span><span class="sxs-lookup"><span data-stu-id="6472b-112">DirectSignedCustomerAgreementStatus</span></span>

<span data-ttu-id="6472b-113">Een **DirectSignedCustomerAgreementStatus** -resource bevat de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="6472b-113">A **DirectSignedCustomerAgreementStatus** resource includes the following properties:</span></span>

| <span data-ttu-id="6472b-114">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6472b-114">Property</span></span>       | <span data-ttu-id="6472b-115">Type</span><span class="sxs-lookup"><span data-stu-id="6472b-115">Type</span></span>   | <span data-ttu-id="6472b-116">Description</span><span class="sxs-lookup"><span data-stu-id="6472b-116">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6472b-117">isSigned</span><span class="sxs-lookup"><span data-stu-id="6472b-117">isSigned</span></span> | <span data-ttu-id="6472b-118">booleaans</span><span class="sxs-lookup"><span data-stu-id="6472b-118">boolean</span></span> | <span data-ttu-id="6472b-119">Hiermee wordt aangegeven of de klant overeenkomst rechtstreeks is ondertekend (geaccepteerd) door de klant.</span><span class="sxs-lookup"><span data-stu-id="6472b-119">Indicates if the customer agreement has been directly signed (accepted) by the customer.</span></span> |
