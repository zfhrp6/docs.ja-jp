---
title: ICorDebugVariableSymbol::GetSlotIndex メソッド
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420623"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="87fab-102">ICorDebugVariableSymbol::GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="87fab-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="87fab-103">ローカル変数のマネージ スロット インデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="87fab-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87fab-104">構文</span><span class="sxs-lookup"><span data-stu-id="87fab-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87fab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87fab-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="87fab-106">[out] ローカル変数のスロット インデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="87fab-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87fab-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="87fab-107">Return Value</span></span>  
 <span data-ttu-id="87fab-108">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="87fab-108">`S_OK` if successful.</span></span> <span data-ttu-id="87fab-109">変数が関数引数の場合は `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="87fab-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87fab-110">コメント</span><span class="sxs-lookup"><span data-stu-id="87fab-110">Remarks</span></span>  
 <span data-ttu-id="87fab-111">ローカル変数のマネージ スロット インデックスを使用すると、変数のメタデータ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="87fab-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87fab-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="87fab-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87fab-113">要件</span><span class="sxs-lookup"><span data-stu-id="87fab-113">Requirements</span></span>  
 <span data-ttu-id="87fab-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87fab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87fab-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87fab-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87fab-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87fab-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87fab-117">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87fab-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fab-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="87fab-118">See Also</span></span>  
 [<span data-ttu-id="87fab-119">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87fab-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="87fab-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87fab-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
