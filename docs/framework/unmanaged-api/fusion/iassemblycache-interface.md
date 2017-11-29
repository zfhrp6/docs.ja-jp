---
title: "IAssemblyCache インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="8661d-102">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8661d-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="8661d-103">Fusion テクノロジで使用するためのグローバル アセンブリ キャッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="8661d-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8661d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-104">Methods</span></span>  
  
|<span data-ttu-id="8661d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-105">Method</span></span>|<span data-ttu-id="8661d-106">説明</span><span class="sxs-lookup"><span data-stu-id="8661d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8661d-107">CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="8661d-108">新しいへの参照を取得[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="8661d-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="8661d-109">CreateAssemblyScavenger メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="8661d-110">Fusion テクノロジでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="8661d-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="8661d-111">InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="8661d-112">指定したアセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="8661d-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="8661d-113">QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="8661d-114">指定したアセンブリについて、要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="8661d-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="8661d-115">UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="8661d-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="8661d-116">指定したアセンブリをグローバル アセンブリ キャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="8661d-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8661d-117">要件</span><span class="sxs-lookup"><span data-stu-id="8661d-117">Requirements</span></span>  
 <span data-ttu-id="8661d-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8661d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8661d-119">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8661d-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8661d-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8661d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8661d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8661d-121">See Also</span></span>  
 [<span data-ttu-id="8661d-122">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8661d-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="8661d-123">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="8661d-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
