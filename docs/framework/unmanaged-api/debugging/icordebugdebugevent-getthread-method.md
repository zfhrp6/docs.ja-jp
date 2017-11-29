---
title: "ICorDebugDebugEvent::GetThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13b950545c2c8c8b54d24b932351d80280e1dac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="01c0d-102">ICorDebugDebugEvent::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="01c0d-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="01c0d-103">イベントが発生したスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="01c0d-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c0d-104">構文</span><span class="sxs-lookup"><span data-stu-id="01c0d-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01c0d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01c0d-105">Parameters</span></span>  
 <span data-ttu-id="01c0d-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="01c0d-106">ppThread</span></span>  
 <span data-ttu-id="01c0d-107">[out]イベントが発生したスレッドを表す ICorDebugThread オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01c0d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01c0d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="01c0d-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01c0d-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="01c0d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01c0d-110">要件</span><span class="sxs-lookup"><span data-stu-id="01c0d-110">Requirements</span></span>  
 <span data-ttu-id="01c0d-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="01c0d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01c0d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01c0d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01c0d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01c0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01c0d-114">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c0d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c0d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="01c0d-115">See Also</span></span>  
 [<span data-ttu-id="01c0d-116">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01c0d-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="01c0d-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="01c0d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
