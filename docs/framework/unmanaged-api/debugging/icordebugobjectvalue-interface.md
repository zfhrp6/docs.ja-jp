---
title: ICorDebugObjectValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ddf3b60ed595aff8bc81d0bb59675fd1db12f7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422414"
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="85c06-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="85c06-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="85c06-103">オブジェクトを格納する値を表す"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="85c06-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85c06-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-104">Methods</span></span>  
  
|<span data-ttu-id="85c06-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-105">Method</span></span>|<span data-ttu-id="85c06-106">説明</span><span class="sxs-lookup"><span data-stu-id="85c06-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85c06-107">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="85c06-108">共通言語ランタイム (CLR) へのインターフェイス ポインターを取得<xref:System.Type>オブジェクトのこの`ICorDebugObjectValue`参照します。</span><span class="sxs-lookup"><span data-stu-id="85c06-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="85c06-109">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="85c06-110">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="85c06-110">Not implemented.</span></span>|  
|[<span data-ttu-id="85c06-111">GetFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="85c06-112">インターフェイス ポインターを取得、 [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)を表す、指定したクラスの指定したフィールドの値。</span><span class="sxs-lookup"><span data-stu-id="85c06-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="85c06-113">GetManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="85c06-114">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="85c06-114">Obsolete.</span></span> <span data-ttu-id="85c06-115">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="85c06-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="85c06-116">GetVirtualMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="85c06-117">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="85c06-117">Not implemented.</span></span>|  
|[<span data-ttu-id="85c06-118">IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="85c06-119">これによって、オブジェクトが参照されるかどうかを示す値を取得`ICorDebugObjectValue`は値型です。</span><span class="sxs-lookup"><span data-stu-id="85c06-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="85c06-120">SetFromManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="85c06-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="85c06-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="85c06-121">Obsolete.</span></span> <span data-ttu-id="85c06-122">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="85c06-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c06-123">コメント</span><span class="sxs-lookup"><span data-stu-id="85c06-123">Remarks</span></span>  
 <span data-ttu-id="85c06-124">`ICorDebugObjectValue`デバッグ中のプロセスの続行まで有効のままです。</span><span class="sxs-lookup"><span data-stu-id="85c06-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85c06-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="85c06-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c06-126">要件</span><span class="sxs-lookup"><span data-stu-id="85c06-126">Requirements</span></span>  
 <span data-ttu-id="85c06-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="85c06-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c06-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85c06-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85c06-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85c06-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85c06-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c06-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c06-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="85c06-131">See Also</span></span>  
 [<span data-ttu-id="85c06-132">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85c06-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
