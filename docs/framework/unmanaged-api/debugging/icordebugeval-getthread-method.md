---
title: ICorDebugEval::GetThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e64bc173717c3121d6c2b101f734ee325a0ced53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413762"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="259bd-102">ICorDebugEval::GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="259bd-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="259bd-103">この評価が実行またはが実行スレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="259bd-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="259bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="259bd-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="259bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="259bd-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="259bd-106">[out]スレッドを表す ICorDebugThread オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="259bd-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="259bd-107">要件</span><span class="sxs-lookup"><span data-stu-id="259bd-107">Requirements</span></span>  
 <span data-ttu-id="259bd-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="259bd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="259bd-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="259bd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="259bd-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="259bd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="259bd-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="259bd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
