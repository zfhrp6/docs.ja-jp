---
title: "ICorDebugChain::GetPrevious メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetPrevious
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1203aa4a6e35574c1d026ddc05cac810fed5b78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="a918e-102">ICorDebugChain::GetPrevious メソッド</span><span class="sxs-lookup"><span data-stu-id="a918e-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="a918e-103">スレッドの前のフレーム チェーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="a918e-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a918e-104">構文</span><span class="sxs-lookup"><span data-stu-id="a918e-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a918e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a918e-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="a918e-106">[out]このスレッドのフレームの以前のチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a918e-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="a918e-107">このチェーンの最初のチェーン場合`ppChain`が null です。</span><span class="sxs-lookup"><span data-stu-id="a918e-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a918e-108">要件</span><span class="sxs-lookup"><span data-stu-id="a918e-108">Requirements</span></span>  
 <span data-ttu-id="a918e-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a918e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a918e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a918e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a918e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a918e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a918e-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a918e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
