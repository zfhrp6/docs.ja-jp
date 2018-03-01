---
title: ICorDebugValueBreakpoint Interface1
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
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="29701-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="29701-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="29701-103">特定の値へのアクセスを提供する ICorDebugBreakpoint インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="29701-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29701-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="29701-104">Methods</span></span>  
  
|<span data-ttu-id="29701-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="29701-105">Method</span></span>|<span data-ttu-id="29701-106">説明</span><span class="sxs-lookup"><span data-stu-id="29701-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29701-107">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="29701-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="29701-108">ブレークポイントが設定されているオブジェクトの値を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="29701-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29701-109">コメント</span><span class="sxs-lookup"><span data-stu-id="29701-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29701-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="29701-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29701-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="29701-111">Requirements</span></span>  
 <span data-ttu-id="29701-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29701-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29701-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29701-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29701-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29701-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29701-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29701-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29701-116">参照</span><span class="sxs-lookup"><span data-stu-id="29701-116">See Also</span></span>  
 [<span data-ttu-id="29701-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29701-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
