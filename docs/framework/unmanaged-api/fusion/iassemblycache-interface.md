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
ms.workload: dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="73b56-102">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73b56-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="73b56-103">Fusion テクノロジで使用するためのグローバル アセンブリ キャッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="73b56-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73b56-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-104">Methods</span></span>  
  
|<span data-ttu-id="73b56-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-105">Method</span></span>|<span data-ttu-id="73b56-106">説明</span><span class="sxs-lookup"><span data-stu-id="73b56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73b56-107">CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="73b56-108">新しいへの参照を取得[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="73b56-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="73b56-109">CreateAssemblyScavenger メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="73b56-110">Fusion テクノロジでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="73b56-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="73b56-111">InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="73b56-112">指定したアセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="73b56-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="73b56-113">QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="73b56-114">指定したアセンブリについて、要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="73b56-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="73b56-115">UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="73b56-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="73b56-116">指定したアセンブリをグローバル アセンブリ キャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="73b56-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73b56-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="73b56-117">Requirements</span></span>  
 <span data-ttu-id="73b56-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73b56-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b56-119">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="73b56-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="73b56-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73b56-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b56-121">参照</span><span class="sxs-lookup"><span data-stu-id="73b56-121">See Also</span></span>  
 [<span data-ttu-id="73b56-122">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73b56-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="73b56-123">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="73b56-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
