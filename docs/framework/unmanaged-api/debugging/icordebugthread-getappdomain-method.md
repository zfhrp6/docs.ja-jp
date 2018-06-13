---
title: ICorDebugThread::GetAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51878f0334afe52608b60ca540e49c86fded148e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418046"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="e2a71-102">ICorDebugThread::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e2a71-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="e2a71-103">この ICorDebugThread を現在実行しているアプリケーション ドメインへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e2a71-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a71-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2a71-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2a71-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2a71-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="e2a71-106">[out]現在このスレッドが実行しているアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2a71-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a71-107">要件</span><span class="sxs-lookup"><span data-stu-id="e2a71-107">Requirements</span></span>  
 <span data-ttu-id="e2a71-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2a71-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a71-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2a71-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2a71-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2a71-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2a71-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
