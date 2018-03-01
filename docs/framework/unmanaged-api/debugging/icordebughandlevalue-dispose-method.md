---
title: "ICorDebugHandleValue::Dispose メソッド"
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
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9128189cd1eedeebf348f55500f1db37fc34d29f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="73a49-102">ICorDebugHandleValue::Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="73a49-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="73a49-103">インターフェイス ポインターを明示的に解放せずにこの ICorDebugHandleValue オブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="73a49-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a49-104">構文</span><span class="sxs-lookup"><span data-stu-id="73a49-104">Syntax</span></span>  
  
```  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="73a49-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="73a49-105">Requirements</span></span>  
 <span data-ttu-id="73a49-106">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73a49-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a49-107">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73a49-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73a49-108">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73a49-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73a49-109">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a49-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
