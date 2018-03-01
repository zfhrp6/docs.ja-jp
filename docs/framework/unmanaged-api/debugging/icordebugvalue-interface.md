---
title: ICorDebugValue Interface1
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
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="71cad-102">ICorDebugValue Interface1</span><span class="sxs-lookup"><span data-stu-id="71cad-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="71cad-103">デバッグ中のプロセス内の値を表します。</span><span class="sxs-lookup"><span data-stu-id="71cad-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="71cad-104">値には、読み取り/書き込み値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="71cad-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71cad-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-105">Methods</span></span>  
  
|<span data-ttu-id="71cad-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-106">Method</span></span>|<span data-ttu-id="71cad-107">説明</span><span class="sxs-lookup"><span data-stu-id="71cad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71cad-108">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="71cad-109">このメソッドは現在実装されていません。</span><span class="sxs-lookup"><span data-stu-id="71cad-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="71cad-110">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="71cad-111">このアドレスを取得`ICorDebugValue`オブジェクトで、デバッグされている処理を行っています。</span><span class="sxs-lookup"><span data-stu-id="71cad-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="71cad-112">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="71cad-113">サイズを取得します (バイト単位) のこの`ICorDebugValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="71cad-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="71cad-114">GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="71cad-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="71cad-115">これのプリミティブ型を取得`ICorDebugValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="71cad-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71cad-116">コメント</span><span class="sxs-lookup"><span data-stu-id="71cad-116">Remarks</span></span>  
 <span data-ttu-id="71cad-117">一般が返される値オブジェクトの所有権が渡されます。</span><span class="sxs-lookup"><span data-stu-id="71cad-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="71cad-118">受信者は、オブジェクトが終了したときに、オブジェクトからの参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="71cad-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="71cad-119">ここで、値を取得した、に応じて値のままになる有効なプロセスが再開されます。</span><span class="sxs-lookup"><span data-stu-id="71cad-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="71cad-120">そのため、一般に、値はならない保持の呼び出しで、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="71cad-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71cad-121">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="71cad-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71cad-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="71cad-122">Requirements</span></span>  
 <span data-ttu-id="71cad-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71cad-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71cad-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71cad-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71cad-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71cad-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71cad-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71cad-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71cad-127">参照</span><span class="sxs-lookup"><span data-stu-id="71cad-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="71cad-128">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71cad-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="71cad-129">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71cad-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
