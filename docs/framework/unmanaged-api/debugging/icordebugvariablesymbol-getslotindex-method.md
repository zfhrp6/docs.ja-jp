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
ms.openlocfilehash: d632bc792152afcfc94b51235dc0699fb3efc245
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="1bf2f-102">ICorDebugVariableSymbol::GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="1bf2f-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="1bf2f-103">ローカル変数のマネージ スロット インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf2f-104">構文</span><span class="sxs-lookup"><span data-stu-id="1bf2f-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bf2f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1bf2f-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="1bf2f-106">[out] ローカル変数のスロット インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bf2f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1bf2f-107">Return Value</span></span>  
 <span data-ttu-id="1bf2f-108">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-108">`S_OK` if successful.</span></span> <span data-ttu-id="1bf2f-109">変数が関数引数の場合は `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bf2f-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1bf2f-110">Remarks</span></span>  
 <span data-ttu-id="1bf2f-111">ローカル変数のマネージ スロット インデックスを使用すると、変数のメタデータ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bf2f-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf2f-113">要件</span><span class="sxs-lookup"><span data-stu-id="1bf2f-113">Requirements</span></span>  
 <span data-ttu-id="1bf2f-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bf2f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bf2f-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bf2f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bf2f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bf2f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bf2f-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bf2f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf2f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bf2f-118">See Also</span></span>  
 [<span data-ttu-id="1bf2f-119">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bf2f-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="1bf2f-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bf2f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
