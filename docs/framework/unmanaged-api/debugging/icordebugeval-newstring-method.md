---
title: "ICorDebugEval::NewString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cc45d766801391fcd157c39357058be17759f8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="1c647-102">ICorDebugEval::NewString メソッド</span><span class="sxs-lookup"><span data-stu-id="1c647-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="1c647-103">指定した内容を持つ新しい文字列インスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1c647-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c647-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c647-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c647-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c647-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="1c647-106">[in]文字列の内容へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1c647-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c647-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1c647-107">Remarks</span></span>  
 <span data-ttu-id="1c647-108">文字列は常に、現在のスレッドが実行しているアプリケーション ドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="1c647-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c647-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="1c647-109">Requirements</span></span>  
 <span data-ttu-id="1c647-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c647-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c647-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c647-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c647-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c647-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c647-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c647-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
