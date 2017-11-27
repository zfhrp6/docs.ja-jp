---
title: "ICorDebugThread::GetActiveChain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3f104933bc70682a531c0853cfc6eabcd357831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="a2d0d-102">ICorDebugThread::GetActiveChain メソッド</span><span class="sxs-lookup"><span data-stu-id="a2d0d-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="a2d0d-103">ICorDebugThread オブジェクトでアクティブな (最新) スタック チェーンへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d0d-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2d0d-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2d0d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2d0d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="a2d0d-106">[out]スタック チェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d0d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a2d0d-107">Remarks</span></span>  
 <span data-ttu-id="a2d0d-108">`ppChain`パラメーターが現在アクティブなスタック チェーンがない場合は null です。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d0d-109">要件</span><span class="sxs-lookup"><span data-stu-id="a2d0d-109">Requirements</span></span>  
 <span data-ttu-id="a2d0d-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2d0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d0d-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2d0d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2d0d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2d0d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2d0d-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d0d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
