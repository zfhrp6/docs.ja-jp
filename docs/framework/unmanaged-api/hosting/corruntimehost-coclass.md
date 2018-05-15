---
title: CorRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9b9b8a728932caa085bba1665dc97faf02be8fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="84f27-102">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="84f27-102">CorRuntimeHost Coclass</span></span>
<span data-ttu-id="84f27-103">共通言語ランタイムで実行されているアプリケーションを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-103">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f27-104">構文</span><span class="sxs-lookup"><span data-stu-id="84f27-104">Syntax</span></span>  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="84f27-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f27-105">Interfaces</span></span>  
  
|<span data-ttu-id="84f27-106">Interface</span><span class="sxs-lookup"><span data-stu-id="84f27-106">Interface</span></span>|<span data-ttu-id="84f27-107">説明</span><span class="sxs-lookup"><span data-stu-id="84f27-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="84f27-108">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f27-108">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|<span data-ttu-id="84f27-109">共通言語ランタイム (CLR) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-109">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="84f27-110">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f27-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|<span data-ttu-id="84f27-111">ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイムを明示的に停止できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-111">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="84f27-112">IDebuggerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f27-112">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|<span data-ttu-id="84f27-113">デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-113">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="84f27-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84f27-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|<span data-ttu-id="84f27-115">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-115">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="84f27-116">"IValidator"</span><span class="sxs-lookup"><span data-stu-id="84f27-116">"IValidator"</span></span>|<span data-ttu-id="84f27-117">ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84f27-117">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84f27-118">要件</span><span class="sxs-lookup"><span data-stu-id="84f27-118">Requirements</span></span>  
 <span data-ttu-id="84f27-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="84f27-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f27-120">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="84f27-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="84f27-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="84f27-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84f27-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f27-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f27-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="84f27-123">See Also</span></span>  
 [<span data-ttu-id="84f27-124">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="84f27-124">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
