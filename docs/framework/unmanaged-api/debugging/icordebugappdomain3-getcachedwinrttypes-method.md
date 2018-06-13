---
title: ICorDebugAppDomain3::GetCachedWinRTTypes メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 782a6cf70aa3e3446d8da3160712d57245afe176
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405526"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="7e772-102">ICorDebugAppDomain3::GetCachedWinRTTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="7e772-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="7e772-103">キャッシュされたすべての列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。</span><span class="sxs-lookup"><span data-stu-id="7e772-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e772-104">構文</span><span class="sxs-lookup"><span data-stu-id="7e772-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e772-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e772-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="7e772-106">[out]ポインター、 [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)インターフェイス オブジェクトの管理対象の形式を列挙できる[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメインで現在読み込まれている型。</span><span class="sxs-lookup"><span data-stu-id="7e772-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e772-107">要件</span><span class="sxs-lookup"><span data-stu-id="7e772-107">Requirements</span></span>  
 <span data-ttu-id="7e772-108">**プラットフォーム:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e772-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="7e772-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e772-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e772-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e772-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e772-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e772-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e772-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e772-112">See Also</span></span>  
 [<span data-ttu-id="7e772-113">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e772-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
