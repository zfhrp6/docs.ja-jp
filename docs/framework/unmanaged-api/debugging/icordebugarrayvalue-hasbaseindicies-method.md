---
title: ICorDebugArrayValue::HasBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 574df434360dfab644a4c937dac46ebc3871a53a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399508"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="33b4d-102">ICorDebugArrayValue::HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="33b4d-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="33b4d-103">この配列のディメンションに 0 以外の基本のインデックスが設定されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="33b4d-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="33b4d-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33b4d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33b4d-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="33b4d-106">[out]ブール値へのポインター`true`場合この 1 つまたは複数のディメンション`ICorDebugArrayValue`オブジェクト ベースのインデックス 0 ではないのです。 それ以外の場合、ブール値は`false`します。</span><span class="sxs-lookup"><span data-stu-id="33b4d-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b4d-107">要件</span><span class="sxs-lookup"><span data-stu-id="33b4d-107">Requirements</span></span>  
 <span data-ttu-id="33b4d-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="33b4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33b4d-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33b4d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33b4d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33b4d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33b4d-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33b4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
