---
title: "Fusion インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1742025bed977dfd377a78db42df42c1bc43966
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-interfaces"></a><span data-ttu-id="b7a52-102">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-102">Fusion Interfaces</span></span>
<span data-ttu-id="b7a52-103">このセクションでは、アプリケーションのリソースのプロパティにアクセスして、アプリケーションのリソースの正しいバージョンを見つけるために fusion API が使用するアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7a52-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b7a52-104">In This Section</span></span>  
 [<span data-ttu-id="b7a52-105">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="b7a52-106">メソッドを生成し、アプリケーションの id と参照キーの比較を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="b7a52-107">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="b7a52-108">グローバル アセンブリ キャッシュの表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b7a52-109">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="b7a52-110">グローバル アセンブリ キャッシュ内の 1 つのアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b7a52-111">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="b7a52-112">配列の列挙子を表す`IAssemblyName`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b7a52-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="b7a52-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="b7a52-114">記述するおよびアセンブリの一意の id を使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="b7a52-115">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="b7a52-116">現在のスコープで、アプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b7a52-117">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="b7a52-118">現在のスコープで、アプリケーションを定義するコードの一意のシグネチャを表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b7a52-119">IEnumDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="b7a52-120">コレクションの列挙子の役割を果たす`IDefinitionIdentity`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b7a52-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="b7a52-121">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="b7a52-122">現在のスコープ内のコード オブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="b7a52-123">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="b7a52-124">コレクションの列挙子の役割を果たす`IReferenceIdentity`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b7a52-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="b7a52-125">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="b7a52-126">コード オブジェクトの id キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="b7a52-127">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="b7a52-128">グローバル アセンブリ キャッシュにインストールされている参照先アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b7a52-129">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="b7a52-130">グローバル アセンブリ キャッシュにインストールされている項目を表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b7a52-131">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="b7a52-132">現在のスコープ内のアプリケーションの一意識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b7a52-133">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7a52-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="b7a52-134">コード オブジェクトの一意のシグネチャへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="b7a52-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b7a52-135">参照</span><span class="sxs-lookup"><span data-stu-id="b7a52-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="b7a52-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7a52-136">Related Sections</span></span>  
 [<span data-ttu-id="b7a52-137">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b7a52-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="b7a52-138">Fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="b7a52-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="b7a52-139">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="b7a52-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
