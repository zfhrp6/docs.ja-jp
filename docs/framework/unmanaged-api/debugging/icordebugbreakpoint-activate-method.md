---
title: "ICorDebugBreakpoint::Activate メソッド"
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
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ef0880c40cb09b836938f253447f5ffeaaec207b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="cfa37-102">ICorDebugBreakpoint::Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="cfa37-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="cfa37-103">これのアクティブな状態を設定`ICorDebugBreakpoint`です。</span><span class="sxs-lookup"><span data-stu-id="cfa37-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa37-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfa37-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfa37-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfa37-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="cfa37-106">[in]この値を設定`true`としてアクティブになった状態を指定するそれ以外の場合、この値を設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="cfa37-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa37-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="cfa37-107">Requirements</span></span>  
 <span data-ttu-id="cfa37-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cfa37-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa37-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfa37-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfa37-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfa37-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfa37-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa37-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
