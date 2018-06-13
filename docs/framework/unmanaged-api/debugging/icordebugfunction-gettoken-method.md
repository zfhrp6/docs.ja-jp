---
title: ICorDebugFunction::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acfb8910df6e20bf55ed33fdbb9b1c30d22f4684
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412053"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="145fc-102">ICorDebugFunction::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="145fc-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="145fc-103">この関数のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="145fc-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="145fc-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="145fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="145fc-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="145fc-106">[out]ポインター、`mdMethodDef`この関数のメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="145fc-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="145fc-107">要件</span><span class="sxs-lookup"><span data-stu-id="145fc-107">Requirements</span></span>  
 <span data-ttu-id="145fc-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="145fc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145fc-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="145fc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="145fc-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="145fc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="145fc-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="145fc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
