---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512162"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="bc6ab-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="bc6ab-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="bc6ab-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc6ab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc6ab-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc6ab-104">ID</span></span>|<span data-ttu-id="bc6ab-105">3557</span><span class="sxs-lookup"><span data-stu-id="bc6ab-105">3557</span></span>|  
|<span data-ttu-id="bc6ab-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bc6ab-106">Keywords</span></span>|<span data-ttu-id="bc6ab-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="bc6ab-107">WFServices</span></span>|  
|<span data-ttu-id="bc6ab-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bc6ab-108">Level</span></span>|<span data-ttu-id="bc6ab-109">情報</span><span class="sxs-lookup"><span data-stu-id="bc6ab-109">Information</span></span>|  
|<span data-ttu-id="bc6ab-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bc6ab-110">Channel</span></span>|<span data-ttu-id="bc6ab-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bc6ab-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc6ab-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc6ab-112">Description</span></span>  
 <span data-ttu-id="bc6ab-113">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc6ab-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc6ab-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bc6ab-114">Message</span></span>  
 <span data-ttu-id="bc6ab-115">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="bc6ab-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc6ab-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bc6ab-116">Details</span></span>  
  
|<span data-ttu-id="bc6ab-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bc6ab-117">Data Item Name</span></span>|<span data-ttu-id="bc6ab-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bc6ab-118">Data Item Type</span></span>|<span data-ttu-id="bc6ab-119">説明</span><span class="sxs-lookup"><span data-stu-id="bc6ab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc6ab-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="bc6ab-120">TransactionId</span></span>|<span data-ttu-id="bc6ab-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc6ab-121">xs:string</span></span>|<span data-ttu-id="bc6ab-122">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="bc6ab-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="bc6ab-123">例外</span><span class="sxs-lookup"><span data-stu-id="bc6ab-123">Exception</span></span>|<span data-ttu-id="bc6ab-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc6ab-124">xs:string</span></span>|<span data-ttu-id="bc6ab-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="bc6ab-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="bc6ab-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc6ab-126">AppDomain</span></span>|<span data-ttu-id="bc6ab-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc6ab-127">xs:string</span></span>|<span data-ttu-id="bc6ab-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bc6ab-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
