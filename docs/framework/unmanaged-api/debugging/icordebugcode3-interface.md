---
title: "ICorDebugCode3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a89bc2b516f87a4deb7ccb794b5ae0352d6a8efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="0ebfb-102">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ebfb-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="0ebfb-103">マネージ戻り値に関する情報を提供するには、"ICorDebugCode"と"ICorDebugCode2"機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0ebfb-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ebfb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0ebfb-104">Methods</span></span>  
  
|<span data-ttu-id="0ebfb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0ebfb-105">Method</span></span>|<span data-ttu-id="0ebfb-106">説明</span><span class="sxs-lookup"><span data-stu-id="0ebfb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ebfb-107">GetReturnValueLiveOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="0ebfb-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="0ebfb-108">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0ebfb-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebfb-109">コメント</span><span class="sxs-lookup"><span data-stu-id="0ebfb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ebfb-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0ebfb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebfb-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="0ebfb-111">Requirements</span></span>  
 <span data-ttu-id="0ebfb-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ebfb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebfb-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ebfb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebfb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebfb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebfb-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebfb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebfb-116">参照</span><span class="sxs-lookup"><span data-stu-id="0ebfb-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="0ebfb-117">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ebfb-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="0ebfb-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ebfb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
