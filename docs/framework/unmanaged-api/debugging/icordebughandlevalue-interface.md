---
title: ICorDebugHandleValue Interface1
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
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="480cd-102">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="480cd-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="480cd-103">デバッガーにガベージ コレクションのハンドルが作成の参照値を表す ICorDebugReferenceValue のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="480cd-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="480cd-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="480cd-104">Methods</span></span>  
  
|<span data-ttu-id="480cd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="480cd-105">Method</span></span>|<span data-ttu-id="480cd-106">説明</span><span class="sxs-lookup"><span data-stu-id="480cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="480cd-107">Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="480cd-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="480cd-108">これによって参照されるハンドルを解放`ICorDebugHandleValue`せず、インターフェイス ポインターを明示的に解放するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="480cd-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="480cd-109">GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="480cd-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="480cd-110">これによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得`ICorDebugHandleValue`です。</span><span class="sxs-lookup"><span data-stu-id="480cd-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="480cd-111">コメント</span><span class="sxs-lookup"><span data-stu-id="480cd-111">Remarks</span></span>  
 <span data-ttu-id="480cd-112">`ICorDebugReferenceValue`オブジェクトがデバッグ対象のコードの実行の中断によって無効にします。</span><span class="sxs-lookup"><span data-stu-id="480cd-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="480cd-113">`ICorDebugHandleValue`が明示的に解放されるまで、改ページして、継続は、その参照を維持します。</span><span class="sxs-lookup"><span data-stu-id="480cd-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="480cd-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="480cd-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="480cd-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="480cd-115">Requirements</span></span>  
 <span data-ttu-id="480cd-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="480cd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="480cd-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="480cd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="480cd-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="480cd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="480cd-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480cd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480cd-120">参照</span><span class="sxs-lookup"><span data-stu-id="480cd-120">See Also</span></span>  
 [<span data-ttu-id="480cd-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="480cd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
