---
title: "ICorPublish::GetProcess メソッド"
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
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e613b9101e842a584eef4bcbac1bf3de1dba5cd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="96076-102">ICorPublish::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="96076-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="96076-103">取得、 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)を指定した識別子を持つプロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="96076-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96076-104">構文</span><span class="sxs-lookup"><span data-stu-id="96076-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96076-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96076-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="96076-106">[in]プロセスの識別子。</span><span class="sxs-lookup"><span data-stu-id="96076-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="96076-107">[out]アドレスへのポインター、`ICorPublishProcess`プロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="96076-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96076-108">コメント</span><span class="sxs-lookup"><span data-stu-id="96076-108">Remarks</span></span>  
 <span data-ttu-id="96076-109">`GetProcess`プロセスが存在しないか、現在のユーザーがデバッグできるマネージ プロセスがない場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="96076-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96076-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="96076-110">Requirements</span></span>  
 <span data-ttu-id="96076-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96076-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96076-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="96076-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="96076-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96076-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96076-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96076-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96076-115">参照</span><span class="sxs-lookup"><span data-stu-id="96076-115">See Also</span></span>  
 [<span data-ttu-id="96076-116">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96076-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
