---
title: "ICorDebugVariableSymbol::SetValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="13c57-102">ICorDebugVariableSymbol::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="13c57-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="13c57-103">バイト配列の値を変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="13c57-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c57-104">構文</span><span class="sxs-lookup"><span data-stu-id="13c57-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c57-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13c57-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="13c57-106">[in] 値を設定する変数内の開始オフセットです。</span><span class="sxs-lookup"><span data-stu-id="13c57-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="13c57-107">このパラメーターは、オブジェクトのメンバー フィールドに書き込む際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="13c57-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="13c57-108">[in] 新しい値を反映させるためにコンテキストを更新する必要があるスレッドのスレッド ID。</span><span class="sxs-lookup"><span data-stu-id="13c57-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="13c57-109">[in] スレッド コンテキストのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="13c57-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="13c57-110">[in] 値の書き込みに使用されるスレッド コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="13c57-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="13c57-111">[in] `pValue` バッファーのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="13c57-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="13c57-112">[in] 設定する値が含まれるバッファー。</span><span class="sxs-lookup"><span data-stu-id="13c57-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13c57-113">コメント</span><span class="sxs-lookup"><span data-stu-id="13c57-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13c57-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c57-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c57-115">要件</span><span class="sxs-lookup"><span data-stu-id="13c57-115">Requirements</span></span>  
 <span data-ttu-id="13c57-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="13c57-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c57-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13c57-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13c57-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13c57-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13c57-119">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c57-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c57-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="13c57-120">See Also</span></span>  
 [<span data-ttu-id="13c57-121">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13c57-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="13c57-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="13c57-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
