---
title: ICorDebugReferenceValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422332"
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="5ffa7-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="5ffa7-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="5ffa7-103">オブジェクトへの参照である値を管理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="5ffa7-104">(つまり、このインターフェイスはポインターを管理する方法を提供します。)このインターフェイスは、"ICorDebugValue"を実装します。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ffa7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-105">Methods</span></span>  
  
|<span data-ttu-id="5ffa7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-106">Method</span></span>|<span data-ttu-id="5ffa7-107">説明</span><span class="sxs-lookup"><span data-stu-id="5ffa7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ffa7-108">Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="5ffa7-109">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="5ffa7-110">DereferenceStrong メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="5ffa7-111">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-111">Not implemented.</span></span> <span data-ttu-id="5ffa7-112">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="5ffa7-113">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="5ffa7-114">参照先オブジェクトの現在のメモリ アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="5ffa7-115">IsNull メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="5ffa7-116">示す値を取得するかどうかこの`ICorDebugReferenceValue`、null 値をその場合は、`ICorDebugReferenceValue`がオブジェクトを指していません。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="5ffa7-117">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="5ffa7-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="5ffa7-118">現在のメモリ アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-118">Sets the current memory address.</span></span> <span data-ttu-id="5ffa7-119">つまり、このメソッドはこの設定`ICorDebugReferenceValue`にオブジェクトをポイントします。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ffa7-120">コメント</span><span class="sxs-lookup"><span data-stu-id="5ffa7-120">Remarks</span></span>  
 <span data-ttu-id="5ffa7-121">共通言語ランタイム (CLR) は、デバッグ対象のプロセスが続行されたときに、オブジェクトのガベージ コレクションを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="5ffa7-122">ガベージ コレクションは、メモリ内の周囲オブジェクトを移動可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="5ffa7-123">`ICorDebugReferenceValue`はいずれかの連携して、ガベージ コレクションを使用して、ガベージ コレクションの後の情報が更新されるか、ガベージ コレクションの前に暗黙的に無効化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="5ffa7-124">`ICorDebugReferenceValue`デバッグ対象のプロセスが続行されてした後にオブジェクトが暗黙的に検証されたにする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="5ffa7-125">明示的に解放されるか公開されるまでは、派生"ICorDebugHandleValue"は無効化されません。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ffa7-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffa7-127">要件</span><span class="sxs-lookup"><span data-stu-id="5ffa7-127">Requirements</span></span>  
 <span data-ttu-id="5ffa7-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ffa7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffa7-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ffa7-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ffa7-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ffa7-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ffa7-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffa7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffa7-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ffa7-132">See Also</span></span>  
    
    
 [<span data-ttu-id="5ffa7-133">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ffa7-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
