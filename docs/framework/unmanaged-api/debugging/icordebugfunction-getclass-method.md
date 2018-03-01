---
title: "ICorDebugFunction::GetClass メソッド"
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
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4607b5c71311eeccc9df778a45ca30a305b90aa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="fb79e-102">ICorDebugFunction::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="fb79e-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="fb79e-103">この関数のメンバーであるクラスを表す ICorDebugClass オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="fb79e-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb79e-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb79e-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb79e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb79e-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="fb79e-106">[out]アドレスへのポインター、`ICorDebugClass`を表すオブジェクト、クラス、または null の場合、この関数は、クラスのメンバーではない場合。</span><span class="sxs-lookup"><span data-stu-id="fb79e-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb79e-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="fb79e-107">Requirements</span></span>  
 <span data-ttu-id="fb79e-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb79e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb79e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb79e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb79e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb79e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb79e-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb79e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
