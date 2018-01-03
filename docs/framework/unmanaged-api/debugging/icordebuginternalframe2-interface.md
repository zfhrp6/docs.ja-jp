---
title: "ICorDebugInternalFrame2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d87303fbe95804b458a42ed43b65f29233814977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="9ef5b-102">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef5b-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="9ef5b-103">スタックのアドレスや ICorDebugFrame オブジェクトとの関連の位置など、内部フレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ef5b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ef5b-104">Methods</span></span>  
  
|<span data-ttu-id="9ef5b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ef5b-105">Method</span></span>|<span data-ttu-id="9ef5b-106">説明</span><span class="sxs-lookup"><span data-stu-id="9ef5b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ef5b-107">GetFrameAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="9ef5b-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="9ef5b-108">内部フレームのスタック アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="9ef5b-109">IsCloserToLeaf メソッド</span><span class="sxs-lookup"><span data-stu-id="9ef5b-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="9ef5b-110">チェックするかどうか、`this`内部フレームは、指定した ICorDebugFrame オブジェクトよりも、リーフに近づきます。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ef5b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="9ef5b-111">Remarks</span></span>  
 <span data-ttu-id="9ef5b-112">このインターフェイスは、ICorDebugInternalFrame インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ef5b-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef5b-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ef5b-114">Requirements</span></span>  
 <span data-ttu-id="9ef5b-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef5b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef5b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ef5b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ef5b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef5b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef5b-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef5b-119">参照</span><span class="sxs-lookup"><span data-stu-id="9ef5b-119">See Also</span></span>  
 [<span data-ttu-id="9ef5b-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef5b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9ef5b-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9ef5b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
