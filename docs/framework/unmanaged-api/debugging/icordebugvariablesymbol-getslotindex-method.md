---
title: "ICorDebugVariableSymbol::GetSlotIndex メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb84e529768e0be44883511bb89703a4c3199df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="f7313-102">ICorDebugVariableSymbol::GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="f7313-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="f7313-103">ローカル変数のマネージ スロット インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f7313-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7313-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7313-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7313-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7313-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="f7313-106">[out] ローカル変数のスロット インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7313-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7313-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f7313-107">Return Value</span></span>  
 <span data-ttu-id="f7313-108">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f7313-108">`S_OK` if successful.</span></span> <span data-ttu-id="f7313-109">変数が関数引数の場合は `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="f7313-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7313-110">コメント</span><span class="sxs-lookup"><span data-stu-id="f7313-110">Remarks</span></span>  
 <span data-ttu-id="f7313-111">ローカル変数のマネージ スロット インデックスを使用すると、変数のメタデータ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f7313-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7313-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7313-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7313-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="f7313-113">Requirements</span></span>  
 <span data-ttu-id="f7313-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7313-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7313-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7313-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7313-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7313-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7313-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7313-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7313-118">参照</span><span class="sxs-lookup"><span data-stu-id="f7313-118">See Also</span></span>  
 [<span data-ttu-id="f7313-119">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7313-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="f7313-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7313-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
