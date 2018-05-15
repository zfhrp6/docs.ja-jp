---
title: ICorDebugFrame::GetChain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c020b9f6c074be11e3433939ce6898586123cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="55297-102">ICorDebugFrame::GetChain メソッド</span><span class="sxs-lookup"><span data-stu-id="55297-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="55297-103">このフレームの一部であるチェーンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="55297-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55297-104">構文</span><span class="sxs-lookup"><span data-stu-id="55297-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55297-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55297-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="55297-106">[out]このフレームを含むチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="55297-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55297-107">要件</span><span class="sxs-lookup"><span data-stu-id="55297-107">Requirements</span></span>  
 <span data-ttu-id="55297-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="55297-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55297-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55297-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55297-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55297-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55297-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55297-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
