---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49b36b907df514873815ac28565c5796d997c191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="c070d-102">ICorDebugAppDomain3::GetCachedWinRTTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="c070d-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="c070d-103">キャッシュされたすべての列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。</span><span class="sxs-lookup"><span data-stu-id="c070d-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c070d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c070d-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c070d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c070d-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="c070d-106">[out]ポインター、 [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)インターフェイス オブジェクトの管理対象の形式を列挙できる[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメインで現在読み込まれている型。</span><span class="sxs-lookup"><span data-stu-id="c070d-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c070d-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="c070d-107">Requirements</span></span>  
 <span data-ttu-id="c070d-108">**プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c070d-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="c070d-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c070d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c070d-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c070d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c070d-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c070d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c070d-112">参照</span><span class="sxs-lookup"><span data-stu-id="c070d-112">See Also</span></span>  
 [<span data-ttu-id="c070d-113">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c070d-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
