---
title: ICorDebugBreakpoint::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61aece9dd506d6e4af8718e45cc772d120a7d579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="7509e-102">ICorDebugBreakpoint::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="7509e-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="7509e-103">示す値を取得するかどうかこの`ICorDebugBreakpoint`がアクティブです。</span><span class="sxs-lookup"><span data-stu-id="7509e-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7509e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7509e-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7509e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7509e-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="7509e-106">[out]`true`このブレークポイントがアクティブ、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="7509e-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7509e-107">要件</span><span class="sxs-lookup"><span data-stu-id="7509e-107">Requirements</span></span>  
 <span data-ttu-id="7509e-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7509e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7509e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7509e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7509e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7509e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7509e-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7509e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
