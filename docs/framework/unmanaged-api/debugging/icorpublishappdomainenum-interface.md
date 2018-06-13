---
title: ICorPublishAppDomainEnum インターフェイス
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610f62274aea88c1d5f9bbe1456685aa1d3bca68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423742"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="336a5-102">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="336a5-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="336a5-103">サブクラス、 [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)のコレクションを走査するメソッドを提供するインターフェイス[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)現在プロセス内に存在するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="336a5-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="336a5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="336a5-104">Methods</span></span>  
  
|<span data-ttu-id="336a5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="336a5-105">Method</span></span>|<span data-ttu-id="336a5-106">説明</span><span class="sxs-lookup"><span data-stu-id="336a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="336a5-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="336a5-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="336a5-108">指定した数を取得`ICorPublishAppDomain`コレクションの現在位置からのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="336a5-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336a5-109">コメント</span><span class="sxs-lookup"><span data-stu-id="336a5-109">Remarks</span></span>  
 <span data-ttu-id="336a5-110">`ICorPublishAppDomainEnum`インターフェイス抽象、インターフェイスのメソッドを実装[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="336a5-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336a5-111">要件</span><span class="sxs-lookup"><span data-stu-id="336a5-111">Requirements</span></span>  
 <span data-ttu-id="336a5-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="336a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336a5-113">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="336a5-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="336a5-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="336a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="336a5-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336a5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="336a5-116">See Also</span></span>  
 [<span data-ttu-id="336a5-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="336a5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="336a5-118">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="336a5-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
