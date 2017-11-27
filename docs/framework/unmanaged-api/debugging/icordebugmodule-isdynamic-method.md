---
title: "ICorDebugModule::IsDynamic メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsDynamic
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3583749ddb48015b43d45061d3e4cb10e08016b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="dd028-102">ICorDebugModule::IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="dd028-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="dd028-103">このモジュールは動的であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd028-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd028-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd028-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd028-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd028-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="dd028-106">[out]`true`このモジュールは、動的、それ以外の場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="dd028-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd028-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dd028-107">Remarks</span></span>  
 <span data-ttu-id="dd028-108">動的モジュールでは、新しいクラスを追加でき、モジュールが読み込まれた後であっても、既存のクラスを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="dd028-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="dd028-109">[Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)と[icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)クラスが追加または削除されたときにコールバックをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="dd028-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd028-110">要件</span><span class="sxs-lookup"><span data-stu-id="dd028-110">Requirements</span></span>  
 <span data-ttu-id="dd028-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd028-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd028-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd028-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd028-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd028-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd028-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd028-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
