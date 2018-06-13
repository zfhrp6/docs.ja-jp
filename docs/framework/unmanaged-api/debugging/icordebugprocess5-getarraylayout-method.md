---
title: ICorDebugProcess5::GetArrayLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e96dccdd2836eebb08e88fe09dda531cd62baeee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420002"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="d1003-102">ICorDebugProcess5::GetArrayLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="d1003-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="d1003-103">配列型のレイアウトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d1003-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1003-104">構文</span><span class="sxs-lookup"><span data-stu-id="d1003-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1003-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1003-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d1003-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)レイアウトを持つが必要な配列を指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="d1003-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="d1003-107">[out]ポインター、 [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)メモリ内の配列のレイアウトに関する情報を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="d1003-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1003-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d1003-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1003-109">要件</span><span class="sxs-lookup"><span data-stu-id="d1003-109">Requirements</span></span>  
 <span data-ttu-id="d1003-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1003-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1003-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1003-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1003-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1003-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1003-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1003-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1003-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1003-114">See Also</span></span>  
 [<span data-ttu-id="d1003-115">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1003-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d1003-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1003-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
