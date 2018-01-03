---
title: "ICorDebugBoxValue::GetObject メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBoxValue.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e71da40af57d00e4651c094ddad9c86fc6fe636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="964a0-102">ICorDebugBoxValue::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="964a0-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="964a0-103">ボックス化された値を取得します。</span><span class="sxs-lookup"><span data-stu-id="964a0-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="964a0-104">構文</span><span class="sxs-lookup"><span data-stu-id="964a0-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="964a0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="964a0-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="964a0-106">[out]ボックス化された値を表す ICorDebugObjectValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="964a0-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="964a0-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="964a0-107">Requirements</span></span>  
 <span data-ttu-id="964a0-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="964a0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="964a0-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="964a0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="964a0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="964a0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="964a0-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964a0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
