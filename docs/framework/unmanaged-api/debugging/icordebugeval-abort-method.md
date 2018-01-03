---
title: "ICorDebugEval::Abort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.Abort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 064febeec32e5c43b6b73ef2b3a44625f151eb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="17654-102">ICorDebugEval::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="17654-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="17654-103">この ICorDebugEval オブジェクトが現在実行して、計算を中止します。</span><span class="sxs-lookup"><span data-stu-id="17654-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17654-104">構文</span><span class="sxs-lookup"><span data-stu-id="17654-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="17654-105">コメント</span><span class="sxs-lookup"><span data-stu-id="17654-105">Remarks</span></span>  
 <span data-ttu-id="17654-106">評価が入れ子になっており、最新のものではありません、`Abort`メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17654-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17654-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="17654-107">Requirements</span></span>  
 <span data-ttu-id="17654-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="17654-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17654-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17654-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17654-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17654-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17654-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17654-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
