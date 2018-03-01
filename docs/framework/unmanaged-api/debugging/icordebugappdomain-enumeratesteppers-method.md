---
title: "ICorDebugAppDomain::EnumerateSteppers メソッド"
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
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b410eabee546307488449e577d9e102ac6a210b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="a76c7-102">ICorDebugAppDomain::EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="a76c7-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="a76c7-103">アプリケーション ドメイン内のすべてのアクティブ ステッパの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a76c7-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a76c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="a76c7-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a76c7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a76c7-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="a76c7-106">[out]アプリケーション ドメイン内のすべてのアクティブなステッパの列挙子である ICorDebugStepperEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a76c7-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a76c7-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="a76c7-107">Requirements</span></span>  
 <span data-ttu-id="a76c7-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a76c7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a76c7-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a76c7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a76c7-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a76c7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a76c7-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a76c7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
