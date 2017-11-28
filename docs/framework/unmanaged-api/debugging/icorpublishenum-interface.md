---
title: "ICorPublishEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7034945824e439b42134f8ea3c13bfaf73dbb649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="d0bdf-102">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0bdf-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="d0bdf-103">プロセスとアプリケーション ドメインに関する情報の発行で使用される列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0bdf-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-104">Methods</span></span>  
  
|<span data-ttu-id="d0bdf-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-105">Method</span></span>|<span data-ttu-id="d0bdf-106">説明</span><span class="sxs-lookup"><span data-stu-id="d0bdf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0bdf-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="d0bdf-108">このコピーを作成`ICorPublishEnum`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="d0bdf-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="d0bdf-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="d0bdf-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="d0bdf-112">列挙体の先頭へのカーソルを移動します。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="d0bdf-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="d0bdf-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="d0bdf-114">列挙体の指定数の項目でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0bdf-115">コメント</span><span class="sxs-lookup"><span data-stu-id="d0bdf-115">Remarks</span></span>  
 <span data-ttu-id="d0bdf-116">次の列挙子から派生して`ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="d0bdf-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="d0bdf-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="d0bdf-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="d0bdf-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="d0bdf-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="d0bdf-119">要件</span><span class="sxs-lookup"><span data-stu-id="d0bdf-119">Requirements</span></span>  
 <span data-ttu-id="d0bdf-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d0bdf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0bdf-121">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d0bdf-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d0bdf-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0bdf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0bdf-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0bdf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bdf-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0bdf-124">See Also</span></span>  
 [<span data-ttu-id="d0bdf-125">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="d0bdf-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="d0bdf-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0bdf-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
