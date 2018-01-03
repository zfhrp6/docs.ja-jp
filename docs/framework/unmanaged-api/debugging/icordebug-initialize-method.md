---
title: "ICorDebug::Initialize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Initialize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dff8e5472879bfffb0489f113e9d88527569fa1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="cd36b-102">ICorDebug::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="cd36b-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="cd36b-103">初期化、`ICorDebug`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cd36b-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd36b-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd36b-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd36b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="cd36b-105">Remarks</span></span>  
 <span data-ttu-id="cd36b-106">デバッガーを呼び出す必要があります`Initialize`デバッグを初期化するために時間がサービスの作成時。</span><span class="sxs-lookup"><span data-stu-id="cd36b-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="cd36b-107">このメソッドは、他のメソッドの前に呼び出す必要があります`ICorDebug`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="cd36b-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd36b-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="cd36b-108">Requirements</span></span>  
 <span data-ttu-id="cd36b-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd36b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd36b-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd36b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd36b-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd36b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd36b-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd36b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd36b-113">参照</span><span class="sxs-lookup"><span data-stu-id="cd36b-113">See Also</span></span>  
 [<span data-ttu-id="cd36b-114">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd36b-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
