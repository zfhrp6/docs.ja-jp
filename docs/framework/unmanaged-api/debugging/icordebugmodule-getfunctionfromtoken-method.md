---
title: "ICorDebugModule::GetFunctionFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c449b49333de562cd5ed07f827da6bc295e9c3c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="c1e8e-102">ICorDebugModule::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c1e8e-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="c1e8e-103">メタデータ トークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c1e8e-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e8e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1e8e-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1e8e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1e8e-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="c1e8e-106">[in]A`mdMethodDef`関数のメタデータを参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="c1e8e-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="c1e8e-107">[out]ICorDebugFunction インターフェイスを表す、オブジェクト、関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c1e8e-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1e8e-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c1e8e-108">Remarks</span></span>  
 <span data-ttu-id="c1e8e-109">`GetFunctionFromToken`メソッドは、値が渡された場合に CORDBG_E_FUNCTION_NOT_IL HRESULT を返します`methodDef`Microsoft intermediate language (MSIL) のメソッドを参照していません。</span><span class="sxs-lookup"><span data-stu-id="c1e8e-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1e8e-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="c1e8e-110">Requirements</span></span>  
 <span data-ttu-id="c1e8e-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1e8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e8e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1e8e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1e8e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1e8e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1e8e-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
