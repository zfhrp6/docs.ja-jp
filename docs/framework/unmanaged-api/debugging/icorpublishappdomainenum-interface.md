---
title: "ICorPublishAppDomainEnum インターフェイス"
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
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f84a93053744f059eb3fdd06e2fb69e098e24ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="73cc1-102">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73cc1-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="73cc1-103">サブクラス、 [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)のコレクションを走査するメソッドを提供するインターフェイス[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)現在プロセス内に存在するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="73cc1-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73cc1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="73cc1-104">Methods</span></span>  
  
|<span data-ttu-id="73cc1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="73cc1-105">Method</span></span>|<span data-ttu-id="73cc1-106">説明</span><span class="sxs-lookup"><span data-stu-id="73cc1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73cc1-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="73cc1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="73cc1-108">指定した数を取得`ICorPublishAppDomain`コレクションの現在位置からのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="73cc1-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73cc1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="73cc1-109">Remarks</span></span>  
 <span data-ttu-id="73cc1-110">`ICorPublishAppDomainEnum`インターフェイス抽象、インターフェイスのメソッドを実装[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="73cc1-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73cc1-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="73cc1-111">Requirements</span></span>  
 <span data-ttu-id="73cc1-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73cc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73cc1-113">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="73cc1-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="73cc1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73cc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73cc1-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cc1-116">参照</span><span class="sxs-lookup"><span data-stu-id="73cc1-116">See Also</span></span>  
 [<span data-ttu-id="73cc1-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73cc1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="73cc1-118">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="73cc1-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
