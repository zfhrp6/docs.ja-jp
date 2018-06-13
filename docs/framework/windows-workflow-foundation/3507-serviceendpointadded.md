---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: c787a1a5af752a3d08e2049cfa0b600b7739e56c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512061"
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="a4ed5-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="a4ed5-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="a4ed5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a4ed5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4ed5-104">ID</span><span class="sxs-lookup"><span data-stu-id="a4ed5-104">ID</span></span>|<span data-ttu-id="a4ed5-105">3507</span><span class="sxs-lookup"><span data-stu-id="a4ed5-105">3507</span></span>|  
|<span data-ttu-id="a4ed5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a4ed5-106">Keywords</span></span>|<span data-ttu-id="a4ed5-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a4ed5-107">WFServices</span></span>|  
|<span data-ttu-id="a4ed5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a4ed5-108">Level</span></span>|<span data-ttu-id="a4ed5-109">情報</span><span class="sxs-lookup"><span data-stu-id="a4ed5-109">Information</span></span>|  
|<span data-ttu-id="a4ed5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a4ed5-110">Channel</span></span>|<span data-ttu-id="a4ed5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a4ed5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4ed5-112">説明</span><span class="sxs-lookup"><span data-stu-id="a4ed5-112">Description</span></span>  
 <span data-ttu-id="a4ed5-113">サービス エンドポイントが追加されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4ed5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a4ed5-114">Message</span></span>  
 <span data-ttu-id="a4ed5-115">アドレス '%1'、バインド '%2'、コントラクト '%3' のサービス エンドポイントが追加されました。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4ed5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="a4ed5-116">Details</span></span>  
  
|<span data-ttu-id="a4ed5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a4ed5-117">Data Item Name</span></span>|<span data-ttu-id="a4ed5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a4ed5-118">Data Item Type</span></span>|<span data-ttu-id="a4ed5-119">説明</span><span class="sxs-lookup"><span data-stu-id="a4ed5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4ed5-120">Address</span><span class="sxs-lookup"><span data-stu-id="a4ed5-120">Address</span></span>|<span data-ttu-id="a4ed5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4ed5-121">xs:string</span></span>|<span data-ttu-id="a4ed5-122">エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="a4ed5-123">バインディング</span><span class="sxs-lookup"><span data-stu-id="a4ed5-123">Binding</span></span>|<span data-ttu-id="a4ed5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4ed5-124">xs:string</span></span>|<span data-ttu-id="a4ed5-125">エンドポイントのバインド。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="a4ed5-126">コントラクト</span><span class="sxs-lookup"><span data-stu-id="a4ed5-126">Contract</span></span>|<span data-ttu-id="a4ed5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4ed5-127">xs:string</span></span>|<span data-ttu-id="a4ed5-128">エンドポイントのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="a4ed5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4ed5-129">AppDomain</span></span>|<span data-ttu-id="a4ed5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4ed5-130">xs:string</span></span>|<span data-ttu-id="a4ed5-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a4ed5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
