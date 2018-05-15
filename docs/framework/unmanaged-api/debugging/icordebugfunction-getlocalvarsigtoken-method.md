---
title: ICorDebugFunction::GetLocalVarSigToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a09741ed778436f1cb35d094885bd3effa813a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="0274e-102">ICorDebugFunction::GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0274e-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="0274e-103">この ICorDebugFunction インスタンスで表される関数の場合は、ローカル変数シグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0274e-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0274e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0274e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0274e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0274e-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="0274e-106">[out]ポインター、 `mdSignature` 、この関数の場合は、ローカル変数シグネチャのトークンまたは`mdSignatureNil`、この関数には、ローカル変数があるない場合。</span><span class="sxs-lookup"><span data-stu-id="0274e-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0274e-107">要件</span><span class="sxs-lookup"><span data-stu-id="0274e-107">Requirements</span></span>  
 <span data-ttu-id="0274e-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0274e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0274e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0274e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0274e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0274e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0274e-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0274e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
