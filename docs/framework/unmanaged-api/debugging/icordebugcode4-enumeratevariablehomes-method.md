---
title: ICorDebugCode4::EnumerateVariableHomes メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1c8157d5a5e4a1bd52f187de7c1d3bfcc4e66d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410921"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="8ca3f-102">ICorDebugCode4::EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="8ca3f-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="8ca3f-103">ローカル変数と引数を関数内の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ca3f-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca3f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ca3f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ca3f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ca3f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8ca3f-106">アドレスへのポインター、 [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)インターフェイスであるオブジェクトをローカル変数と関数の引数の列挙子。</span><span class="sxs-lookup"><span data-stu-id="8ca3f-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca3f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8ca3f-107">Remarks</span></span>  
 <span data-ttu-id="8ca3f-108">[ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)インターフェイス オブジェクトは、標準的な列挙子を列挙することができます"ICorDebugEnum"インターフェイスから派生した[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8ca3f-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="8ca3f-109">コレクションが複数あります[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)関数は、さまざまなポイントで別の家庭に設置している場合に同じスロットまたは引数のインデックスのオブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="8ca3f-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca3f-110">要件</span><span class="sxs-lookup"><span data-stu-id="8ca3f-110">Requirements</span></span>  
 <span data-ttu-id="8ca3f-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ca3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca3f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ca3f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca3f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ca3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca3f-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca3f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ca3f-115">See Also</span></span>  
 [<span data-ttu-id="8ca3f-116">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ca3f-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [<span data-ttu-id="8ca3f-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ca3f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
