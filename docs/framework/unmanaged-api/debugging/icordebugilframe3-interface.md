---
title: "ICorDebugILFrame3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame3
api_location: mscordbi.dll
api_type: COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe6affcf82a16a4fd51a5e5a4bf33b247dae0688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="b64f9-102">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b64f9-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="b64f9-103">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b64f9-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="b64f9-104">`ICorDebugILFrame3`ICorDebugILFrame および ICorDebugILFrame2 インターフェイスの論理的な拡張です。</span><span class="sxs-lookup"><span data-stu-id="b64f9-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b64f9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b64f9-105">Methods</span></span>  
  
|<span data-ttu-id="b64f9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b64f9-106">Method</span></span>|<span data-ttu-id="b64f9-107">説明</span><span class="sxs-lookup"><span data-stu-id="b64f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b64f9-108">GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="b64f9-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="b64f9-109">関数の戻り値をカプセル化する ICorDebugValue オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b64f9-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b64f9-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b64f9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b64f9-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b64f9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64f9-112">要件</span><span class="sxs-lookup"><span data-stu-id="b64f9-112">Requirements</span></span>  
 <span data-ttu-id="b64f9-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b64f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64f9-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b64f9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b64f9-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b64f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b64f9-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64f9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b64f9-117">See Also</span></span>  
 [<span data-ttu-id="b64f9-118">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b64f9-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="b64f9-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b64f9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
