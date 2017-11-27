---
title: "ICorDebugModule::GetFunctionFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetFunctionFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96e458bc8fdcf37f572c1f45ba9c31d15311c8c6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="4c0c9-102">ICorDebugModule::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="4c0c9-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="4c0c9-103">メタデータ トークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="4c0c9-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="4c0c9-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c0c9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c0c9-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="4c0c9-106">[in]A`mdMethodDef`関数のメタデータを参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="4c0c9-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="4c0c9-107">[out]ICorDebugFunction インターフェイスを表す、オブジェクト、関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4c0c9-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c0c9-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4c0c9-108">Remarks</span></span>  
 <span data-ttu-id="4c0c9-109">`GetFunctionFromToken`メソッドは、値が渡された場合に CORDBG_E_FUNCTION_NOT_IL HRESULT を返します`methodDef`Microsoft intermediate language (MSIL) のメソッドを参照していません。</span><span class="sxs-lookup"><span data-stu-id="4c0c9-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0c9-110">要件</span><span class="sxs-lookup"><span data-stu-id="4c0c9-110">Requirements</span></span>  
 <span data-ttu-id="4c0c9-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c0c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0c9-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c0c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c0c9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c0c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c0c9-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
