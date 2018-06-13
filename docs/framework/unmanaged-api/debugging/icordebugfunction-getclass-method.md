---
title: ICorDebugFunction::GetClass メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184e578efb549a1dc2e9ec1e30a29ff289b68719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411704"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="6c503-102">ICorDebugFunction::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="6c503-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="6c503-103">この関数のメンバーであるクラスを表す ICorDebugClass オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="6c503-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c503-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c503-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c503-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c503-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="6c503-106">[out]アドレスへのポインター、`ICorDebugClass`を表すオブジェクト、クラス、または null の場合、この関数は、クラスのメンバーではない場合。</span><span class="sxs-lookup"><span data-stu-id="6c503-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c503-107">要件</span><span class="sxs-lookup"><span data-stu-id="6c503-107">Requirements</span></span>  
 <span data-ttu-id="6c503-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6c503-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c503-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c503-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c503-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c503-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c503-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c503-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
