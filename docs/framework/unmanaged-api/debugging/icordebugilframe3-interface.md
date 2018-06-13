---
title: ICorDebugILFrame3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be45022701f72e15e83b7ca28cd110ef58c809b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415598"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="d5f89-102">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5f89-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="d5f89-103">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5f89-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="d5f89-104">`ICorDebugILFrame3` ICorDebugILFrame および ICorDebugILFrame2 インターフェイスの論理的な拡張です。</span><span class="sxs-lookup"><span data-stu-id="d5f89-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5f89-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5f89-105">Methods</span></span>  
  
|<span data-ttu-id="d5f89-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5f89-106">Method</span></span>|<span data-ttu-id="d5f89-107">説明</span><span class="sxs-lookup"><span data-stu-id="d5f89-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5f89-108">GetReturnValueForILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="d5f89-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="d5f89-109">関数の戻り値をカプセル化する ICorDebugValue オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5f89-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5f89-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d5f89-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f89-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d5f89-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5f89-112">要件</span><span class="sxs-lookup"><span data-stu-id="d5f89-112">Requirements</span></span>  
 <span data-ttu-id="d5f89-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5f89-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f89-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5f89-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5f89-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5f89-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5f89-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5f89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f89-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5f89-117">See Also</span></span>  
 [<span data-ttu-id="d5f89-118">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5f89-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="d5f89-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5f89-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
