---
title: "ICorDebugFrame::GetFunction メソッド"
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
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d48ac730f22459a71b126126a7418e73805c7e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="5940b-102">ICorDebugFrame::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="5940b-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="5940b-103">このスタック フレームに関連付けられているコードを含む関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5940b-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5940b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5940b-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5940b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5940b-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="5940b-106">[out]このスタック フレームに関連付けられているコードを含む関数を表す ICorDebugFunction オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5940b-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5940b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="5940b-107">Remarks</span></span>  
 <span data-ttu-id="5940b-108">`GetFunction`フレームは、特定の関数に関連付けられていない場合、メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5940b-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5940b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="5940b-109">Requirements</span></span>  
 <span data-ttu-id="5940b-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5940b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5940b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5940b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5940b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5940b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5940b-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5940b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
