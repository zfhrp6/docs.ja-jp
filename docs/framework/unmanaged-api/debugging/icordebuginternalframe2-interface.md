---
title: ICorDebugInternalFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4082c4204b85aba97651419db15ba8eb4c3d54e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415163"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="131a7-102">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="131a7-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="131a7-103">スタックのアドレスや ICorDebugFrame オブジェクトとの関連の位置など、内部フレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="131a7-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="131a7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="131a7-104">Methods</span></span>  
  
|<span data-ttu-id="131a7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="131a7-105">Method</span></span>|<span data-ttu-id="131a7-106">説明</span><span class="sxs-lookup"><span data-stu-id="131a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="131a7-107">GetFrameAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="131a7-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="131a7-108">内部フレームのスタック アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="131a7-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="131a7-109">IsCloserToLeaf メソッド</span><span class="sxs-lookup"><span data-stu-id="131a7-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="131a7-110">チェックするかどうか、`this`内部フレームは、指定した ICorDebugFrame オブジェクトよりも、リーフに近づきます。</span><span class="sxs-lookup"><span data-stu-id="131a7-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="131a7-111">コメント</span><span class="sxs-lookup"><span data-stu-id="131a7-111">Remarks</span></span>  
 <span data-ttu-id="131a7-112">このインターフェイスは、ICorDebugInternalFrame インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="131a7-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="131a7-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="131a7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131a7-114">要件</span><span class="sxs-lookup"><span data-stu-id="131a7-114">Requirements</span></span>  
 <span data-ttu-id="131a7-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="131a7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131a7-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="131a7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="131a7-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="131a7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="131a7-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131a7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131a7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="131a7-119">See Also</span></span>  
 [<span data-ttu-id="131a7-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="131a7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="131a7-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="131a7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
