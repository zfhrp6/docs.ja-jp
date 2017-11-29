---
title: "IcorDebugVariableHome::GetLiveRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLiveRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8554bf2667f3542b3164b60eaed998087fe175d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="21862-102">IcorDebugVariableHome::GetLiveRange メソッド</span><span class="sxs-lookup"><span data-stu-id="21862-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="21862-103">この変数がアクティブ、ネイティブな範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="21862-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21862-104">構文</span><span class="sxs-lookup"><span data-stu-id="21862-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21862-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21862-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="21862-106">[out]これで、変数が最初ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="21862-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="21862-107">[out]直後に、変数はポイント最後ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="21862-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21862-108">要件</span><span class="sxs-lookup"><span data-stu-id="21862-108">Requirements</span></span>  
 <span data-ttu-id="21862-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="21862-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21862-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21862-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21862-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21862-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21862-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21862-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21862-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="21862-113">See Also</span></span>  
 [<span data-ttu-id="21862-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21862-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
