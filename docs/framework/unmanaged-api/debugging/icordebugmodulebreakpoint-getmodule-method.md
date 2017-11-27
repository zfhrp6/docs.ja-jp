---
title: "ICorDebugModuleBreakpoint::GetModule メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint.GetModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: afdd16cbdb2b33ad0806fbce1dab5e6d7130fb0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="17d36-102">ICorDebugModuleBreakpoint::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="17d36-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="17d36-103">"ICorDebugModule"このブレークポイントが設定されているモジュールを参照するには、インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="17d36-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d36-104">構文</span><span class="sxs-lookup"><span data-stu-id="17d36-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17d36-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17d36-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="17d36-106">[out]アドレスへのポインター、`ICorDebugModule`ブレークポイントが設定されているモジュールを参照するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="17d36-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d36-107">要件</span><span class="sxs-lookup"><span data-stu-id="17d36-107">Requirements</span></span>  
 <span data-ttu-id="17d36-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="17d36-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d36-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17d36-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17d36-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d36-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d36-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d36-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d36-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="17d36-112">See Also</span></span>  
 
