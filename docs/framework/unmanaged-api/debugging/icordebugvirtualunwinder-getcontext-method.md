---
title: ICorDebugVirtualUnwinder::GetContext メソッド
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d034016c7470cbf134cb142db9f98d82d0c59d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="0eab2-102">ICorDebugVirtualUnwinder::GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="0eab2-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="0eab2-103">このアンワインダーの現在のコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="0eab2-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eab2-104">構文</span><span class="sxs-lookup"><span data-stu-id="0eab2-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0eab2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0eab2-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="0eab2-106">[in] \(WinNT.h で定義されている) コンテキストのどの部分を返すかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="0eab2-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="0eab2-107">[in] `contextBuf` のバイト数。</span><span class="sxs-lookup"><span data-stu-id="0eab2-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0eab2-108">[out] `contextBuf` に実際に書き込まれたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0eab2-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="0eab2-109">[out] このアンワインダーの現在のコンテキストが格納されているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="0eab2-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eab2-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0eab2-110">Return Value</span></span>  
 <span data-ttu-id="0eab2-111">mscordbi によって受信された失敗を示す HRESULT 値は致命的と見なされ、ICorDebug API によって `CORDBG_E_DATA_TARGET_ERROR` が返されます。</span><span class="sxs-lookup"><span data-stu-id="0eab2-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eab2-112">コメント</span><span class="sxs-lookup"><span data-stu-id="0eab2-112">Remarks</span></span>  
 <span data-ttu-id="0eab2-113">初期値を設定する、`contextBuf`呼び出すことによって返されるコンテキスト バッファーへの引数、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0eab2-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eab2-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab2-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="0eab2-115">アンワインドではレジスタのサブセット (例: 不揮発性レジスタのみ) だけが復元されるため、コンテキストが、実際のメソッド呼び出し時点でのレジスタの状態と正確には一致しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="0eab2-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eab2-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="0eab2-116">Requirements</span></span>  
 <span data-ttu-id="0eab2-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0eab2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eab2-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0eab2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0eab2-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0eab2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eab2-120">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eab2-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eab2-121">参照</span><span class="sxs-lookup"><span data-stu-id="0eab2-121">See Also</span></span>  
 [<span data-ttu-id="0eab2-122">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0eab2-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="0eab2-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0eab2-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
