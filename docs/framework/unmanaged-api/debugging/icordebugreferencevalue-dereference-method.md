---
title: ICorDebugReferenceValue::Dereference メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a0fd1981e7da5af19cf3a422c6008d373e9ac92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="61dd2-102">ICorDebugReferenceValue::Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="61dd2-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="61dd2-103">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="61dd2-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61dd2-104">構文</span><span class="sxs-lookup"><span data-stu-id="61dd2-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61dd2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61dd2-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="61dd2-106">[out]この ICorDebugReferenceValue オブジェクトが指すオブジェクトを表す ICorDebugValue のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="61dd2-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61dd2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="61dd2-107">Remarks</span></span>  
 <span data-ttu-id="61dd2-108">`ICorDebugValue`オブジェクトが有効では、参照がまだ無効になっている間だけです。</span><span class="sxs-lookup"><span data-stu-id="61dd2-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61dd2-109">要件</span><span class="sxs-lookup"><span data-stu-id="61dd2-109">Requirements</span></span>  
 <span data-ttu-id="61dd2-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="61dd2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61dd2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61dd2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61dd2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61dd2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61dd2-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61dd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
