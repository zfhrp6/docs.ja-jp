---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="a6384-102">ICorDebugDataTarget2::CreateVirtualUnwinder メソッド</span><span class="sxs-lookup"><span data-stu-id="a6384-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="a6384-103">初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。</span><span class="sxs-lookup"><span data-stu-id="a6384-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6384-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6384-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6384-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6384-105">Parameters</span></span>  
 <span data-ttu-id="a6384-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="a6384-106">nativeThreadID</span></span>  
 <span data-ttu-id="a6384-107">[入力] スタックをアンワインドするスレッドのネイティブ スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="a6384-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="a6384-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="a6384-108">contextFlags</span></span>  
 <span data-ttu-id="a6384-109">[入力] コンテキストのどの部分が `initialContext` で定義されるかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="a6384-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="a6384-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="a6384-110">cbContext</span></span>  
 <span data-ttu-id="a6384-111">[入力] `initialContext` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a6384-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="a6384-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="a6384-112">initialContext</span></span>  
 <span data-ttu-id="a6384-113">[入力] コンテキストのデータ。</span><span class="sxs-lookup"><span data-stu-id="a6384-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="a6384-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="a6384-114">ppUnwinder</span></span>  
 <span data-ttu-id="a6384-115">[出力] ICorDebugVirtualUnwinder インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6384-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6384-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="a6384-116">Return Value</span></span>  
 <span data-ttu-id="a6384-117">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="a6384-117">`S_OK` if successful.</span></span> <span data-ttu-id="a6384-118">それ以外の `HRESULT` は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="a6384-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="a6384-119">失敗した`HRESULT`mscordbi によって受信された致命的と見なされ、により[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)を返すメソッド`CORDBG_E_DATA_TARGET_ERROR`です。</span><span class="sxs-lookup"><span data-stu-id="a6384-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6384-120">コメント</span><span class="sxs-lookup"><span data-stu-id="a6384-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6384-121">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6384-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6384-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="a6384-122">Requirements</span></span>  
 <span data-ttu-id="a6384-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6384-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6384-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6384-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6384-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6384-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6384-126">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6384-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6384-127">参照</span><span class="sxs-lookup"><span data-stu-id="a6384-127">See Also</span></span>  
 [<span data-ttu-id="a6384-128">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6384-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="a6384-129">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6384-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
