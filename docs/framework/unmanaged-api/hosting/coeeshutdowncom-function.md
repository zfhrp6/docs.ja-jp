---
title: "CoEEShutDownCOM 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="6388d-102">CoEEShutDownCOM 関数</span><span class="sxs-lookup"><span data-stu-id="6388d-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="6388d-103">共通言語ランタイム (CLR) の内部ランタイム呼び出し可能ラッパー (RCW) を保持しているすべてのインターフェイス ポインターを解放するを強制します。</span><span class="sxs-lookup"><span data-stu-id="6388d-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="6388d-104">RCW のすべてのキャッシュを解放する効果があります。</span><span class="sxs-lookup"><span data-stu-id="6388d-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="6388d-105">このグローバル関数は非推奨、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6388d-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6388d-106">代わりに、特定のランタイムのエントリ ポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6388d-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6388d-107">構文</span><span class="sxs-lookup"><span data-stu-id="6388d-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6388d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="6388d-108">Remarks</span></span>  
 <span data-ttu-id="6388d-109">`CoEEShutDownCOM`関数は、最初のすべてのコンテキストでは、他のすべてのキャッシュにあるすべての Rcw を解放し、セットアップで既存の任意の終了処理通知を削除します。</span><span class="sxs-lookup"><span data-stu-id="6388d-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="6388d-110">DLL のアンロードは行われません。</span><span class="sxs-lookup"><span data-stu-id="6388d-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6388d-111">この関数では、プロセスに読み込まれているすべてのランタイムに影響します。</span><span class="sxs-lookup"><span data-stu-id="6388d-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="6388d-112">以降で、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、この関数に影響する特定のランタイムのエントリ ポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6388d-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="6388d-113">エントリ ポイントを取得する、 [iclrruntimeinfo::getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド"CoEEShutDownCOM"を指定します。</span><span class="sxs-lookup"><span data-stu-id="6388d-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6388d-114">要件</span><span class="sxs-lookup"><span data-stu-id="6388d-114">Requirements</span></span>  
 <span data-ttu-id="6388d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6388d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6388d-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6388d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6388d-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6388d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6388d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6388d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6388d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6388d-119">See Also</span></span>  
 [<span data-ttu-id="6388d-120">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6388d-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
