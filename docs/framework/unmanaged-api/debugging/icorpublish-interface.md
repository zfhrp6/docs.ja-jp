---
title: "ICorPublish インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7769d26d65a97ea8d1b109e0098eae7e7d51ed10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="5af5f-102">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5af5f-102">ICorPublish Interface</span></span>
<span data-ttu-id="5af5f-103">これらのプロセスでアプリケーション ドメインに関する情報とプロセスに関する情報を公開するための一般的なインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="5af5f-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5af5f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5af5f-104">Methods</span></span>  
  
|<span data-ttu-id="5af5f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5af5f-105">Method</span></span>|<span data-ttu-id="5af5f-106">説明</span><span class="sxs-lookup"><span data-stu-id="5af5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5af5f-107">EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="5af5f-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="5af5f-108">取得、 [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)インスタンスをこのコンピューターで実行されている管理対象プロセスを含むです。</span><span class="sxs-lookup"><span data-stu-id="5af5f-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="5af5f-109">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="5af5f-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="5af5f-110">取得、 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)を指定した識別子を持つプロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="5af5f-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5af5f-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="5af5f-111">Requirements</span></span>  
 <span data-ttu-id="5af5f-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5af5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5af5f-113">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5af5f-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5af5f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5af5f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5af5f-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5af5f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af5f-116">参照</span><span class="sxs-lookup"><span data-stu-id="5af5f-116">See Also</span></span>  
 [<span data-ttu-id="5af5f-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5af5f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5af5f-118">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="5af5f-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
