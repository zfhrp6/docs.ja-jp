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
ms.openlocfilehash: a53597067d14c5b3dc1f8829b8ea0a0df07de25a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="debdc-102">ICorDebugEval::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="debdc-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="debdc-103">この ICorDebugEval オブジェクトが現在実行して、計算を中止します。</span><span class="sxs-lookup"><span data-stu-id="debdc-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="debdc-104">構文</span><span class="sxs-lookup"><span data-stu-id="debdc-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="debdc-105">コメント</span><span class="sxs-lookup"><span data-stu-id="debdc-105">Remarks</span></span>  
 <span data-ttu-id="debdc-106">評価が入れ子になっており、最新のものではありません、`Abort`メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="debdc-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="debdc-107">要件</span><span class="sxs-lookup"><span data-stu-id="debdc-107">Requirements</span></span>  
 <span data-ttu-id="debdc-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="debdc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="debdc-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="debdc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="debdc-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="debdc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="debdc-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="debdc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
