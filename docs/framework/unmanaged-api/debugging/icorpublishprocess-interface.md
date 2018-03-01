---
title: "ICorPublishProcess インターフェイス"
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
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="ae5ef-102">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae5ef-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="ae5ef-103">表示するプロセスについての情報にアクセスするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae5ef-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-104">Methods</span></span>  
  
|<span data-ttu-id="ae5ef-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-105">Method</span></span>|<span data-ttu-id="ae5ef-106">説明</span><span class="sxs-lookup"><span data-stu-id="ae5ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae5ef-107">EnumAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="ae5ef-108">取得、 [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)これによって参照されるプロセス内のアプリケーション ドメインを含むインスタンス`ICorPublishProcess`です。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5ef-109">GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="ae5ef-110">これによって参照されるプロセスの実行可能ファイルの完全なパスを取得`ICorPublishProcess`です。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5ef-111">GetProcessID メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="ae5ef-112">これによって参照されるプロセスのオペレーティング システムの識別子を取得`ICorPublishProcess`です。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5ef-113">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5ef-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="ae5ef-114">これによって、プロセスが参照されるかどうかを示す値を取得`ICorPublishProcess`はマネージ コードを実行する呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae5ef-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="ae5ef-115">Requirements</span></span>  
 <span data-ttu-id="ae5ef-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae5ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5ef-117">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ae5ef-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ae5ef-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae5ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae5ef-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5ef-120">参照</span><span class="sxs-lookup"><span data-stu-id="ae5ef-120">See Also</span></span>  
 [<span data-ttu-id="ae5ef-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae5ef-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ae5ef-122">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="ae5ef-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
