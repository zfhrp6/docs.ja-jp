---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510381"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="47638-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="47638-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="47638-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="47638-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47638-104">ID</span><span class="sxs-lookup"><span data-stu-id="47638-104">ID</span></span>|<span data-ttu-id="47638-105">1012</span><span class="sxs-lookup"><span data-stu-id="47638-105">1012</span></span>|  
|<span data-ttu-id="47638-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="47638-106">Keywords</span></span>|<span data-ttu-id="47638-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="47638-107">WFRuntime</span></span>|  
|<span data-ttu-id="47638-108">レベル</span><span class="sxs-lookup"><span data-stu-id="47638-108">Level</span></span>|<span data-ttu-id="47638-109">詳細</span><span class="sxs-lookup"><span data-stu-id="47638-109">Verbose</span></span>|  
|<span data-ttu-id="47638-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="47638-110">Channel</span></span>|<span data-ttu-id="47638-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="47638-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47638-112">説明</span><span class="sxs-lookup"><span data-stu-id="47638-112">Description</span></span>  
 <span data-ttu-id="47638-113">ExecuteActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="47638-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47638-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="47638-114">Message</span></span>  
 <span data-ttu-id="47638-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="47638-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47638-116">詳細</span><span class="sxs-lookup"><span data-stu-id="47638-116">Details</span></span>  
  
|<span data-ttu-id="47638-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="47638-117">Data Item Name</span></span>|<span data-ttu-id="47638-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="47638-118">Data Item Type</span></span>|<span data-ttu-id="47638-119">説明</span><span class="sxs-lookup"><span data-stu-id="47638-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47638-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="47638-120">Activity</span></span>|<span data-ttu-id="47638-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="47638-121">xs:string</span></span>|<span data-ttu-id="47638-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="47638-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="47638-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="47638-123">DisplayName</span></span>|<span data-ttu-id="47638-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="47638-124">xs:string</span></span>|<span data-ttu-id="47638-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="47638-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="47638-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="47638-126">InstanceId</span></span>|<span data-ttu-id="47638-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="47638-127">xs:string</span></span>|<span data-ttu-id="47638-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="47638-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="47638-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="47638-129">AppDomain</span></span>|<span data-ttu-id="47638-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="47638-130">xs:string</span></span>|<span data-ttu-id="47638-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="47638-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
