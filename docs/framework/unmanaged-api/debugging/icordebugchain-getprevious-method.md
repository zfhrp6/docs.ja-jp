---
title: ICorDebugChain::GetPrevious メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c0545440ed63ba914229249080ec9f6be8eb2b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402254"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="3d39c-102">ICorDebugChain::GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="3d39c-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="3d39c-103">スレッドの前のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="3d39c-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d39c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d39c-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d39c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d39c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="3d39c-106">[out]このスレッドのフレームの以前のチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d39c-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="3d39c-107">このチェーンの最初のチェーン場合`ppChain`が null です。</span><span class="sxs-lookup"><span data-stu-id="3d39c-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d39c-108">要件</span><span class="sxs-lookup"><span data-stu-id="3d39c-108">Requirements</span></span>  
 <span data-ttu-id="3d39c-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d39c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d39c-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d39c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d39c-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d39c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d39c-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d39c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
