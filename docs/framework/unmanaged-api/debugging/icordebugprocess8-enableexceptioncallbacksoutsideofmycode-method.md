---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f13236c865f9a57d77ebf83ab48e010f06ef08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="a49c1-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド</span><span class="sxs-lookup"><span data-stu-id="a49c1-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="a49c1-103">[[!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="a49c1-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="a49c1-104">有効または無効に特定の種類の[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外コールバック。</span><span class="sxs-lookup"><span data-stu-id="a49c1-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="a49c1-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a49c1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a49c1-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="a49c1-107">[入力]</span><span class="sxs-lookup"><span data-stu-id="a49c1-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a49c1-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a49c1-108">Remarks</span></span>  
 <span data-ttu-id="a49c1-109">`enableExceptionsOutsideOfJMC` の値が `false` の場合:</span><span class="sxs-lookup"><span data-stu-id="a49c1-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="a49c1-110">DEBUG_EXCEPTION_FIRST_CHANCE 例外のコールバックでは、デバッガーにされません。</span><span class="sxs-lookup"><span data-stu-id="a49c1-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="a49c1-111">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外は、例外がユーザー コードにエスケープしない場合に、デバッガーにコールバックでは発生しません (つまり、例外の発生から例外ハンドラーへのパスを持たない JustMyCode または JMC とマークされているメソッド)。</span><span class="sxs-lookup"><span data-stu-id="a49c1-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="a49c1-112">`enableExceptionsOutsideOfJMC` の既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a49c1-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a49c1-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="a49c1-113">Requirements</span></span>  
 <span data-ttu-id="a49c1-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a49c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a49c1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a49c1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a49c1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a49c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a49c1-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a49c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49c1-118">参照</span><span class="sxs-lookup"><span data-stu-id="a49c1-118">See Also</span></span>  
 [<span data-ttu-id="a49c1-119">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a49c1-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="a49c1-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a49c1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
