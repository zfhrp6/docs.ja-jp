---
title: ICorDebug::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa79382d597d303d492e3a441c15a422697be279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405968"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="f8cd4-102">ICorDebug::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="f8cd4-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="f8cd4-103">初期化、`ICorDebug`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f8cd4-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8cd4-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8cd4-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8cd4-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f8cd4-105">Remarks</span></span>  
 <span data-ttu-id="f8cd4-106">デバッガーを呼び出す必要があります`Initialize`デバッグを初期化するために時間がサービスの作成時。</span><span class="sxs-lookup"><span data-stu-id="f8cd4-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="f8cd4-107">このメソッドは、他のメソッドの前に呼び出す必要があります`ICorDebug`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="f8cd4-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8cd4-108">要件</span><span class="sxs-lookup"><span data-stu-id="f8cd4-108">Requirements</span></span>  
 <span data-ttu-id="f8cd4-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8cd4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8cd4-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8cd4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8cd4-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8cd4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8cd4-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8cd4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cd4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8cd4-113">See Also</span></span>  
 [<span data-ttu-id="f8cd4-114">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8cd4-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
