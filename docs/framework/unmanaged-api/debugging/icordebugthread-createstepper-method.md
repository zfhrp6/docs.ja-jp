---
title: ICorDebugThread::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 626f313c41c85e08901648f429d99c829ba35e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419001"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="d6e74-102">ICorDebugThread::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="d6e74-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="d6e74-103">この ICorDebugThread のアクティブなフレームをステップ実行できるようにする ICorDebugStepper オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6e74-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e74-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6e74-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6e74-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6e74-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="d6e74-106">[out]アドレスへのポインター、`ICorDebugStepper`このスレッドのアクティブなフレームをステップ実行できるようにするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d6e74-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6e74-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d6e74-107">Remarks</span></span>  
 <span data-ttu-id="d6e74-108">アンマネージ コードに、アクティブなフレームがあります。</span><span class="sxs-lookup"><span data-stu-id="d6e74-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="d6e74-109">`ICorDebugStepper`インターフェイスを使用して、実際のステップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6e74-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e74-110">要件</span><span class="sxs-lookup"><span data-stu-id="d6e74-110">Requirements</span></span>  
 <span data-ttu-id="d6e74-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6e74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e74-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6e74-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6e74-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6e74-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6e74-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
