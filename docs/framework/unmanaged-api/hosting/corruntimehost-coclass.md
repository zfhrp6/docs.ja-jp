---
title: "CorRuntimeHost コクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="fe9d8-102">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="fe9d8-103">共通言語ランタイムで実行されているアプリケーションを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe9d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe9d8-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fe9d8-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-105">Interfaces</span></span>  
  
|<span data-ttu-id="fe9d8-106">Interface</span><span class="sxs-lookup"><span data-stu-id="fe9d8-106">Interface</span></span>|<span data-ttu-id="fe9d8-107">説明</span><span class="sxs-lookup"><span data-stu-id="fe9d8-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fe9d8-108">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="fe9d8-109">共通言語ランタイム (CLR) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="fe9d8-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="fe9d8-111">ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイムを明示的に停止できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="fe9d8-112">IDebuggerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="fe9d8-113">デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="fe9d8-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="fe9d8-115">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="fe9d8-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="fe9d8-116">"IValidator"</span></span>|<span data-ttu-id="fe9d8-117">ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe9d8-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="fe9d8-118">Requirements</span></span>  
 <span data-ttu-id="fe9d8-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe9d8-120">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="fe9d8-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fe9d8-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe9d8-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe9d8-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9d8-123">参照</span><span class="sxs-lookup"><span data-stu-id="fe9d8-123">See Also</span></span>  
 [<span data-ttu-id="fe9d8-124">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="fe9d8-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
