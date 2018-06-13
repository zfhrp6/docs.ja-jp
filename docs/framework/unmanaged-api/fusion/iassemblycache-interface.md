---
title: IAssemblyCache インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4302a73f9f077c2e1bf4f66c2b80ab025ae4a62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430584"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="04783-102">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04783-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="04783-103">Fusion テクノロジで使用するためのグローバル アセンブリ キャッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="04783-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04783-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-104">Methods</span></span>  
  
|<span data-ttu-id="04783-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-105">Method</span></span>|<span data-ttu-id="04783-106">説明</span><span class="sxs-lookup"><span data-stu-id="04783-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04783-107">CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="04783-108">新しいへの参照を取得[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="04783-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="04783-109">CreateAssemblyScavenger メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="04783-110">Fusion テクノロジでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="04783-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="04783-111">InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="04783-112">指定したアセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="04783-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="04783-113">QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="04783-114">指定したアセンブリについて、要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="04783-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="04783-115">UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="04783-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="04783-116">指定したアセンブリをグローバル アセンブリ キャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="04783-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04783-117">要件</span><span class="sxs-lookup"><span data-stu-id="04783-117">Requirements</span></span>  
 <span data-ttu-id="04783-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="04783-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04783-119">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="04783-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="04783-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04783-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04783-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="04783-121">See Also</span></span>  
 [<span data-ttu-id="04783-122">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04783-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="04783-123">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="04783-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
