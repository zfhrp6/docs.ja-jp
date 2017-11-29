---
title: ICorDebugHandleValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="e07f0-102">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="e07f0-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="e07f0-103">デバッガーにガベージ コレクションのハンドルが作成の参照値を表す ICorDebugReferenceValue のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="e07f0-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e07f0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e07f0-104">Methods</span></span>  
  
|<span data-ttu-id="e07f0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e07f0-105">Method</span></span>|<span data-ttu-id="e07f0-106">説明</span><span class="sxs-lookup"><span data-stu-id="e07f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e07f0-107">Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="e07f0-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="e07f0-108">これによって参照されるハンドルを解放`ICorDebugHandleValue`せず、インターフェイス ポインターを明示的に解放するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e07f0-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="e07f0-109">GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="e07f0-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="e07f0-110">これによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得`ICorDebugHandleValue`です。</span><span class="sxs-lookup"><span data-stu-id="e07f0-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e07f0-111">コメント</span><span class="sxs-lookup"><span data-stu-id="e07f0-111">Remarks</span></span>  
 <span data-ttu-id="e07f0-112">`ICorDebugReferenceValue`オブジェクトがデバッグ対象のコードの実行の中断によって無効にします。</span><span class="sxs-lookup"><span data-stu-id="e07f0-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="e07f0-113">`ICorDebugHandleValue`が明示的に解放されるまで、改ページして、継続は、その参照を維持します。</span><span class="sxs-lookup"><span data-stu-id="e07f0-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e07f0-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e07f0-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07f0-115">要件</span><span class="sxs-lookup"><span data-stu-id="e07f0-115">Requirements</span></span>  
 <span data-ttu-id="e07f0-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e07f0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07f0-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e07f0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e07f0-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e07f0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e07f0-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07f0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07f0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e07f0-120">See Also</span></span>  
 [<span data-ttu-id="e07f0-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e07f0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
