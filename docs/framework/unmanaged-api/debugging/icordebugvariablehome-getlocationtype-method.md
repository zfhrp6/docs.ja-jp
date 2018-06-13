---
title: ICorDebugVariableHome::GetLocationType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c04fa944f2a3da9b6548ada36443d5dda4725f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421130"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="9b251-102">ICorDebugVariableHome::GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="9b251-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="9b251-103">変数のネイティブの場所の種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b251-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b251-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b251-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b251-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b251-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="9b251-106">[out]変数のネイティブの場所の種類へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b251-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="9b251-107">参照してください、 [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)詳細情報を列挙します。</span><span class="sxs-lookup"><span data-stu-id="9b251-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b251-108">要件</span><span class="sxs-lookup"><span data-stu-id="9b251-108">Requirements</span></span>  
 <span data-ttu-id="9b251-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b251-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b251-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b251-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b251-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b251-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b251-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b251-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b251-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b251-113">See Also</span></span>  
 [<span data-ttu-id="9b251-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b251-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="9b251-115">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="9b251-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
