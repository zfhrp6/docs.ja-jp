---
title: "ICorPublishProcess::IsManaged メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 622781a6c1ad5d5efa3bb2d5227c4f5b845bf94e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="29447-102">ICorPublishProcess::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="29447-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="29447-103">これによって、プロセスが参照されるかどうかを示す値を取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)がマネージ コードを認識します。</span><span class="sxs-lookup"><span data-stu-id="29447-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29447-104">構文</span><span class="sxs-lookup"><span data-stu-id="29447-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29447-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29447-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="29447-106">[out]プロセスにマネージ コードがあるかどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="29447-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="29447-107">値が`true`場合は、プロセスにマネージ コードです。 それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="29447-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29447-108">コメント</span><span class="sxs-lookup"><span data-stu-id="29447-108">Remarks</span></span>  
 <span data-ttu-id="29447-109">現在のバージョンから`ICorPublishProcess`がマネージ コード、プロセスにのみアクセスできるように`IsManaged`は常に返します`true`です。</span><span class="sxs-lookup"><span data-stu-id="29447-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29447-110">要件</span><span class="sxs-lookup"><span data-stu-id="29447-110">Requirements</span></span>  
 <span data-ttu-id="29447-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29447-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29447-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="29447-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29447-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29447-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29447-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29447-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29447-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="29447-115">See Also</span></span>  
 [<span data-ttu-id="29447-116">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29447-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
