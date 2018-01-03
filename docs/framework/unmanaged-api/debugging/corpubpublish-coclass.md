---
title: "CorpubPublish コクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="a26bb-102">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="a26bb-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="a26bb-103">アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="a26bb-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="a26bb-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-105">Interfaces</span></span>  
  
|<span data-ttu-id="a26bb-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-106">Interface</span></span>|<span data-ttu-id="a26bb-107">説明</span><span class="sxs-lookup"><span data-stu-id="a26bb-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a26bb-108">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="a26bb-109">これらのプロセスのプロセスとのアプリケーション ドメインに関する情報を公開するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="a26bb-110">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="a26bb-111">表していると、プロセス内のアプリケーション ドメインに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="a26bb-112">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="a26bb-113">現在プロセス内に存在するアプリケーション ドメインのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="a26bb-114">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="a26bb-115">コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="a26bb-116">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a26bb-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="a26bb-117">コンピューターで実行されているプロセスのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a26bb-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a26bb-118">コメント</span><span class="sxs-lookup"><span data-stu-id="a26bb-118">Remarks</span></span>  
 <span data-ttu-id="a26bb-119">一般的な発行シナリオには、開発者がアプリケーション ドメイン内のコンピューターで実行されているマネージ コードをデバッグする場合が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a26bb-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="a26bb-120">ホスティング環境では、プロセス内で 1 つ以上のアプリケーション ドメインが実行されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a26bb-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="a26bb-121">すべてのコンピューターで実行されているプロセスを一覧表示するグラフィカル ユーザー インターフェイスまたはその他の手段を使用して、特定のプロセスを選択して、開発者と思います。</span><span class="sxs-lookup"><span data-stu-id="a26bb-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="a26bb-122">一覧には、すべてのマネージ コードを実行しているプロセス内でアプリケーション ドメインを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a26bb-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="a26bb-123">開発者は、特定のアプリケーション ドメインを識別し、そのドメインにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a26bb-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26bb-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="a26bb-124">Requirements</span></span>  
 <span data-ttu-id="a26bb-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a26bb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26bb-126">**ヘッダー:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="a26bb-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="a26bb-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a26bb-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a26bb-128">**.NET framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26bb-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26bb-129">参照</span><span class="sxs-lookup"><span data-stu-id="a26bb-129">See Also</span></span>  
 [<span data-ttu-id="a26bb-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a26bb-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
