---
title: ICorPublish::GetProcess メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414bc1bbd3578d0707e35fa70fe196b504af9942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418497"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="582f6-102">ICorPublish::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="582f6-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="582f6-103">取得、 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)を指定した識別子を持つプロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="582f6-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="582f6-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="582f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="582f6-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="582f6-106">[in]プロセスの識別子。</span><span class="sxs-lookup"><span data-stu-id="582f6-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="582f6-107">[out]アドレスへのポインター、`ICorPublishProcess`プロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="582f6-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="582f6-108">コメント</span><span class="sxs-lookup"><span data-stu-id="582f6-108">Remarks</span></span>  
 <span data-ttu-id="582f6-109">`GetProcess` プロセスが存在しないか、現在のユーザーがデバッグできるマネージ プロセスがない場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="582f6-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="582f6-110">要件</span><span class="sxs-lookup"><span data-stu-id="582f6-110">Requirements</span></span>  
 <span data-ttu-id="582f6-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="582f6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="582f6-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="582f6-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="582f6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="582f6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="582f6-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="582f6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582f6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="582f6-115">See Also</span></span>  
 [<span data-ttu-id="582f6-116">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="582f6-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
