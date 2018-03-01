---
title: "IcorDebugVariableHome::GetLiveRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bb86921be3398e6e9653838c1aec6b40ca86469
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="c92ef-102">IcorDebugVariableHome::GetLiveRange メソッド</span><span class="sxs-lookup"><span data-stu-id="c92ef-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="c92ef-103">この変数がアクティブ、ネイティブな範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="c92ef-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="c92ef-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c92ef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c92ef-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="c92ef-106">[out]これで、変数が最初ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="c92ef-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="c92ef-107">[out]直後に、変数はポイント最後ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="c92ef-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c92ef-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="c92ef-108">Requirements</span></span>  
 <span data-ttu-id="c92ef-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c92ef-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c92ef-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c92ef-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c92ef-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c92ef-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c92ef-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c92ef-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92ef-113">参照</span><span class="sxs-lookup"><span data-stu-id="c92ef-113">See Also</span></span>  
 [<span data-ttu-id="c92ef-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c92ef-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
