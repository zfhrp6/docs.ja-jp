---
title: "ICorPublishProcess::GetProcessID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetProcessID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a048255e075b01f4c3c7635038b22ab581032524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="050cb-102">ICorPublishProcess::GetProcessID メソッド</span><span class="sxs-lookup"><span data-stu-id="050cb-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="050cb-103">このプロセスのオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="050cb-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="050cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="050cb-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="050cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="050cb-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="050cb-106">[out]これで表されるプロセスの id へのポインター [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="050cb-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="050cb-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="050cb-107">Requirements</span></span>  
 <span data-ttu-id="050cb-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="050cb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="050cb-109">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="050cb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="050cb-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="050cb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="050cb-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="050cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050cb-112">参照</span><span class="sxs-lookup"><span data-stu-id="050cb-112">See Also</span></span>  
 [<span data-ttu-id="050cb-113">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="050cb-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
