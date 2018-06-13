---
title: IcorDebugVariableHome::GetLiveRange メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f9c586a9e95fc2e57c4956601f6dce2b988159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423066"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="b43f8-102">IcorDebugVariableHome::GetLiveRange メソッド</span><span class="sxs-lookup"><span data-stu-id="b43f8-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="b43f8-103">この変数がアクティブ、ネイティブな範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="b43f8-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="b43f8-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b43f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b43f8-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="b43f8-106">[out]これで、変数が最初ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="b43f8-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="b43f8-107">[out]直後に、変数はポイント最後ライブ論理オフセット。</span><span class="sxs-lookup"><span data-stu-id="b43f8-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43f8-108">要件</span><span class="sxs-lookup"><span data-stu-id="b43f8-108">Requirements</span></span>  
 <span data-ttu-id="b43f8-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43f8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43f8-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b43f8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b43f8-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43f8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43f8-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43f8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43f8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b43f8-113">See Also</span></span>  
 [<span data-ttu-id="b43f8-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b43f8-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
