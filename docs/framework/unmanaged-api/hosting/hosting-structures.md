---
title: "ホスト構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e59353272856525b7d72f322694d15a42ab7b32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-structures"></a><span data-ttu-id="449f3-102">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-102">Hosting Structures</span></span>
<span data-ttu-id="449f3-103">このセクションでは、ホスト API で使用されるアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="449f3-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="449f3-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="449f3-104">In This Section</span></span>  
 [<span data-ttu-id="449f3-105">AssemblyBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="449f3-106">参照アセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="449f3-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="449f3-107">BucketParameters 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="449f3-108">現在の例外イベントに関連付けられているイベントと、パラメーターの型名を格納します。</span><span class="sxs-lookup"><span data-stu-id="449f3-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="449f3-109">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="449f3-110">共通言語ランタイム (CLR) のガベージ コレクションのメカニズムについての統計情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="449f3-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="449f3-111">COR_GC_THREAD_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="449f3-112">ガベージ コレクションに関連するスレッドごとの統計情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="449f3-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="449f3-113">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="449f3-114">エラー報告でのカスタムのダンプに追加する項目を示します。</span><span class="sxs-lookup"><span data-stu-id="449f3-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="449f3-115">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="449f3-116">詳細について説明、`Event_MDAFired`マネージ デバッグ アシスタント (MDA) の作成をトリガーするイベントです。</span><span class="sxs-lookup"><span data-stu-id="449f3-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="449f3-117">ModuleBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="449f3-118">参照されるモジュールとそれを含むアセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="449f3-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="449f3-119">StackOverflowInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="449f3-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="449f3-120">スローされた例外をオーバーフローが原因でオーバーフローが発生しましたが、情報の種類を格納します。</span><span class="sxs-lookup"><span data-stu-id="449f3-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="449f3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="449f3-121">Related Sections</span></span>  
 [<span data-ttu-id="449f3-122">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="449f3-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="449f3-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="449f3-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="449f3-124">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="449f3-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="449f3-125">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="449f3-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
