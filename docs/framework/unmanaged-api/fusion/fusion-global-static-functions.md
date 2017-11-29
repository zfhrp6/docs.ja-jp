---
title: "Fusion グローバル静的関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38462833e3b0ccd56265b02d9a1bc9f37ac12f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="27f34-102">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="27f34-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="27f34-103">このセクションでは、fusion API が使用されるアンマネージ グローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="27f34-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27f34-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27f34-104">In This Section</span></span>  
 [<span data-ttu-id="27f34-105">ClearDownloadCache 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="27f34-106">ダウンロードされたアセンブリのグローバル アセンブリ キャッシュをクリアします。</span><span class="sxs-lookup"><span data-stu-id="27f34-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="27f34-107">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="27f34-108">それらが等しいかどうかを決定する 2 つのアセンブリ id を比較します。</span><span class="sxs-lookup"><span data-stu-id="27f34-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="27f34-109">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="27f34-110">内部使用のみ。</span><span class="sxs-lookup"><span data-stu-id="27f34-110">Internal only.</span></span> <span data-ttu-id="27f34-111">(この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。</span><span class="sxs-lookup"><span data-stu-id="27f34-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="27f34-112">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="27f34-113">新しいへのポインターを取得[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)をグローバル アセンブリ キャッシュを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="27f34-114">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="27f34-115">ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)を指定したアセンブリ内に存在するオブジェクトの一覧を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="27f34-116">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="27f34-117">ポインターを取得、 [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)を指定した名前を持つアセンブリの一意の id を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="27f34-118">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="27f34-119">指定したファイルの履歴のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="27f34-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="27f34-120">CreateInstallReferenceEnum 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="27f34-121">ポインターを取得、 [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)を指定したアセンブリへのアプリケーションの参照の一覧を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="27f34-122">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="27f34-123">ポインターを取得、 [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)アプリケーション id と参照のキーを管理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="27f34-124">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="27f34-125">ポインターを取得、`IUnknown`指定したオブジェクト`IID`のアセンブリにある指定したファイル パス。</span><span class="sxs-lookup"><span data-stu-id="27f34-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="27f34-126">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="27f34-127">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="27f34-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="27f34-128">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="27f34-129">アプリケーション履歴ディレクトリのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="27f34-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="27f34-130">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="27f34-131">ポインターを取得、 [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)コード オブジェクトのキーを管理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27f34-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="27f34-132">IsFrameworkAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="27f34-133">指定したアセンブリが管理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="27f34-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="27f34-134">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="27f34-135">共通言語ランタイムのダウンロード キャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="27f34-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="27f34-136">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="27f34-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="27f34-137">アセンブリのポリシー適用後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="27f34-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27f34-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="27f34-138">Related Sections</span></span>  
 [<span data-ttu-id="27f34-139">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27f34-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="27f34-140">Fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="27f34-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="27f34-141">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="27f34-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="27f34-142">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="27f34-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
