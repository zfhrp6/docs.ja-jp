---
title: "ICorDebugProcess::EnumerateAppDomains メソッド"
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
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ba0f554a4ddf52b7c4ced1658055c4370f112ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="f7278-102">ICorDebugProcess::EnumerateAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="f7278-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="f7278-103">このプロセスですべてのアプリケーション ドメインを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f7278-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7278-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7278-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7278-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7278-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="f7278-106">[out]アドレスへのポインター、 [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)はこのプロセスでのアプリケーション ドメインの列挙子。</span><span class="sxs-lookup"><span data-stu-id="f7278-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7278-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f7278-107">Remarks</span></span>  
 <span data-ttu-id="f7278-108">このメソッドは、前に使用できます、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="f7278-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7278-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="f7278-109">Requirements</span></span>  
 <span data-ttu-id="f7278-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7278-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7278-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7278-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7278-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7278-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7278-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7278-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
