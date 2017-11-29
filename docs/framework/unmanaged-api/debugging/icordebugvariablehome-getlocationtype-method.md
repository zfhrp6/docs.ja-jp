---
title: "ICorDebugVariableHome::GetLocationType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a600f26440e29a60d776be8679d7a298d77434f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="6bcae-102">ICorDebugVariableHome::GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="6bcae-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="6bcae-103">変数のネイティブの場所の種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="6bcae-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bcae-104">構文</span><span class="sxs-lookup"><span data-stu-id="6bcae-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bcae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bcae-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="6bcae-106">[out]変数のネイティブの場所の種類へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6bcae-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="6bcae-107">参照してください、 [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)詳細情報を列挙します。</span><span class="sxs-lookup"><span data-stu-id="6bcae-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bcae-108">要件</span><span class="sxs-lookup"><span data-stu-id="6bcae-108">Requirements</span></span>  
 <span data-ttu-id="6bcae-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bcae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcae-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bcae-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bcae-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bcae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bcae-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcae-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bcae-113">See Also</span></span>  
 [<span data-ttu-id="6bcae-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bcae-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="6bcae-115">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="6bcae-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
