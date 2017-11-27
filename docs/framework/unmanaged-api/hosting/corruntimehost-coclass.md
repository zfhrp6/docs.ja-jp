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
ms.openlocfilehash: 3d7a272aff3a3c7d32042b76d37fdb15c9dcad4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="ad847-102">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="ad847-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="ad847-103">共通言語ランタイムで実行されているアプリケーションを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad847-104">構文</span><span class="sxs-lookup"><span data-stu-id="ad847-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="ad847-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-105">Interfaces</span></span>  
  
|<span data-ttu-id="ad847-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-106">Interface</span></span>|<span data-ttu-id="ad847-107">説明</span><span class="sxs-lookup"><span data-stu-id="ad847-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ad847-108">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="ad847-109">共通言語ランタイム (CLR) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="ad847-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="ad847-111">ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイムを明示的に停止できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="ad847-112">IDebuggerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="ad847-113">デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="ad847-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad847-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="ad847-115">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="ad847-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="ad847-116">"IValidator"</span></span>|<span data-ttu-id="ad847-117">ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad847-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad847-118">要件</span><span class="sxs-lookup"><span data-stu-id="ad847-118">Requirements</span></span>  
 <span data-ttu-id="ad847-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad847-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad847-120">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="ad847-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ad847-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad847-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad847-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad847-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad847-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad847-123">See Also</span></span>  
 [<span data-ttu-id="ad847-124">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="ad847-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
