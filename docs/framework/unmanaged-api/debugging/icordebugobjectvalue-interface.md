---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dfde9f212936b1a0d0f5a6e76eafd4a2e62356c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="751d3-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="751d3-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="751d3-103">オブジェクトを格納する値を表す"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="751d3-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="751d3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-104">Methods</span></span>  
  
|<span data-ttu-id="751d3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-105">Method</span></span>|<span data-ttu-id="751d3-106">説明</span><span class="sxs-lookup"><span data-stu-id="751d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="751d3-107">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="751d3-108">共通言語ランタイム (CLR) へのインターフェイス ポインターを取得<xref:System.Type>オブジェクトのこの`ICorDebugObjectValue`参照します。</span><span class="sxs-lookup"><span data-stu-id="751d3-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="751d3-109">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="751d3-110">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="751d3-110">Not implemented.</span></span>|  
|[<span data-ttu-id="751d3-111">GetFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="751d3-112">インターフェイス ポインターを取得、 [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)を表す、指定したクラスの指定したフィールドの値。</span><span class="sxs-lookup"><span data-stu-id="751d3-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="751d3-113">GetManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="751d3-114">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="751d3-114">Obsolete.</span></span> <span data-ttu-id="751d3-115">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="751d3-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="751d3-116">GetVirtualMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="751d3-117">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="751d3-117">Not implemented.</span></span>|  
|[<span data-ttu-id="751d3-118">IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="751d3-119">これによって、オブジェクトが参照されるかどうかを示す値を取得`ICorDebugObjectValue`は値型です。</span><span class="sxs-lookup"><span data-stu-id="751d3-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="751d3-120">SetFromManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="751d3-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="751d3-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="751d3-121">Obsolete.</span></span> <span data-ttu-id="751d3-122">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="751d3-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="751d3-123">コメント</span><span class="sxs-lookup"><span data-stu-id="751d3-123">Remarks</span></span>  
 <span data-ttu-id="751d3-124">`ICorDebugObjectValue`デバッグ中のプロセスの続行まで有効のままです。</span><span class="sxs-lookup"><span data-stu-id="751d3-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="751d3-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="751d3-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="751d3-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="751d3-126">Requirements</span></span>  
 <span data-ttu-id="751d3-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="751d3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="751d3-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="751d3-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="751d3-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="751d3-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="751d3-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="751d3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751d3-131">参照</span><span class="sxs-lookup"><span data-stu-id="751d3-131">See Also</span></span>  
 [<span data-ttu-id="751d3-132">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="751d3-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
