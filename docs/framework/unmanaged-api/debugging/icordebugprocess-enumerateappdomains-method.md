---
title: "ICorDebugProcess::EnumerateAppDomains メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.EnumerateAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5233dd80750afb82a2e2a8e9675867f6decfa8f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="bf3d9-102">ICorDebugProcess::EnumerateAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="bf3d9-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="bf3d9-103">このプロセスですべてのアプリケーション ドメインを列挙します。</span><span class="sxs-lookup"><span data-stu-id="bf3d9-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf3d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf3d9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf3d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf3d9-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="bf3d9-106">[out]アドレスへのポインター、 [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)はこのプロセスでのアプリケーション ドメインの列挙子。</span><span class="sxs-lookup"><span data-stu-id="bf3d9-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf3d9-107">コメント</span><span class="sxs-lookup"><span data-stu-id="bf3d9-107">Remarks</span></span>  
 <span data-ttu-id="bf3d9-108">このメソッドは、前に使用できます、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="bf3d9-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf3d9-109">要件</span><span class="sxs-lookup"><span data-stu-id="bf3d9-109">Requirements</span></span>  
 <span data-ttu-id="bf3d9-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf3d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf3d9-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf3d9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf3d9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf3d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf3d9-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
