---
title: ICorPublish インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65daa8d783210426136860d95dd5782e21de33a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421533"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="3bae5-102">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bae5-102">ICorPublish Interface</span></span>
<span data-ttu-id="3bae5-103">これらのプロセスでアプリケーション ドメインに関する情報とプロセスに関する情報を公開するための一般的なインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3bae5-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bae5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bae5-104">Methods</span></span>  
  
|<span data-ttu-id="3bae5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bae5-105">Method</span></span>|<span data-ttu-id="3bae5-106">説明</span><span class="sxs-lookup"><span data-stu-id="3bae5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bae5-107">EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="3bae5-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="3bae5-108">取得、 [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)インスタンスをこのコンピューターで実行されている管理対象プロセスを含むです。</span><span class="sxs-lookup"><span data-stu-id="3bae5-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="3bae5-109">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="3bae5-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="3bae5-110">取得、 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)を指定した識別子を持つプロセスを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3bae5-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bae5-111">要件</span><span class="sxs-lookup"><span data-stu-id="3bae5-111">Requirements</span></span>  
 <span data-ttu-id="3bae5-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3bae5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bae5-113">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3bae5-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3bae5-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bae5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bae5-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bae5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bae5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bae5-116">See Also</span></span>  
 [<span data-ttu-id="3bae5-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bae5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3bae5-118">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="3bae5-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
