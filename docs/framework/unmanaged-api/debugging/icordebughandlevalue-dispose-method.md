---
title: ICorDebugHandleValue::Dispose メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9114799b87d39333ff9da66429dc1ea99ec2131c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413431"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="b8dc1-102">ICorDebugHandleValue::Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="b8dc1-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="b8dc1-103">インターフェイス ポインターを明示的に解放せずにこの ICorDebugHandleValue オブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="b8dc1-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8dc1-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8dc1-104">Syntax</span></span>  
  
```  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="b8dc1-105">要件</span><span class="sxs-lookup"><span data-stu-id="b8dc1-105">Requirements</span></span>  
 <span data-ttu-id="b8dc1-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8dc1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8dc1-107">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8dc1-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8dc1-108">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8dc1-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8dc1-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8dc1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
