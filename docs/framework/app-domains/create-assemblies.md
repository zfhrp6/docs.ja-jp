---
title: "アセンブリの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 583c448bd939cd4d1d16bff372afff4172dcf985
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-assemblies"></a><span data-ttu-id="872af-102">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="872af-102">Creating Assemblies</span></span>
<span data-ttu-id="872af-103">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] などの IDE を使用して単一ファイルまたはマルチファイルのアセンブリを作成したり、[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] から提供されるコンパイラやツールを作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="872af-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="872af-104">最も単純なアセンブリは、単純な名前を持ち、単一のアプリケーション ドメインに読み込まれる単一のファイルです。</span><span class="sxs-lookup"><span data-stu-id="872af-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="872af-105">このアセンブリはアプリケーション ディレクトリの外部にある他のアセンブリからは参照できず、バージョン チェックが行われません。</span><span class="sxs-lookup"><span data-stu-id="872af-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="872af-106">アセンブリで構成されるアプリケーションをアンインストールするには、アプリケーションが存在するディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="872af-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="872af-107">多くの開発者は、このような機能を含むアセンブリがあれば、アプリケーションを展開できます。</span><span class="sxs-lookup"><span data-stu-id="872af-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="872af-108">マルチファイル アセンブリは、複数のコード モジュールおよびリソース ファイルから作成できます。</span><span class="sxs-lookup"><span data-stu-id="872af-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="872af-109">複数のアプリケーションで共有できるアセンブリも作成できます。</span><span class="sxs-lookup"><span data-stu-id="872af-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="872af-110">共有アセンブリは厳密な名前を持つ必要があり、グローバル アセンブリ キャッシュに展開することができます。</span><span class="sxs-lookup"><span data-stu-id="872af-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="872af-111">コード モジュールとリソースをアセンブリにグループ化する場合、次のような要因に応じていくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="872af-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="872af-112">バージョン管理</span><span class="sxs-lookup"><span data-stu-id="872af-112">Versioning</span></span>  
  
     <span data-ttu-id="872af-113">同じバージョン情報が含まれている必要があるグループ モジュール。</span><span class="sxs-lookup"><span data-stu-id="872af-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="872af-114">配置</span><span class="sxs-lookup"><span data-stu-id="872af-114">Deployment</span></span>  
  
     <span data-ttu-id="872af-115">展開のモデルをサポートするグループ コードのモジュールおよびリソース。</span><span class="sxs-lookup"><span data-stu-id="872af-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="872af-116">再利用</span><span class="sxs-lookup"><span data-stu-id="872af-116">Reuse</span></span>  
  
     <span data-ttu-id="872af-117">いくつかの目的のために論理的に同時に使用できる場合はグループ モジュール。</span><span class="sxs-lookup"><span data-stu-id="872af-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="872af-118">たとえば、プログラムのメンテナンスで頻繁に使用される型とクラスで構成されるアセンブリは同じアセンブリに配置することができます。</span><span class="sxs-lookup"><span data-stu-id="872af-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="872af-119">さらに、複数のアプリケーションで共有する予定の型をアセンブリにグループ化し、そのアセンブリを厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="872af-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="872af-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="872af-120">Security</span></span>  
  
     <span data-ttu-id="872af-121">同じセキュリティ アクセス許可が必要な型を含むグループ モジュール。</span><span class="sxs-lookup"><span data-stu-id="872af-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="872af-122">スコープ</span><span class="sxs-lookup"><span data-stu-id="872af-122">Scoping</span></span>  
  
     <span data-ttu-id="872af-123">参照可能範囲を同じアセンブリに制限する必要がある型で構成されるグループ モジュール。</span><span class="sxs-lookup"><span data-stu-id="872af-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="872af-124">アンマネージ COM アプリケーションで使用できる共通言語ランタイム アセンブリを作成する際は、特別な考慮事項を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="872af-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="872af-125">アンマネージ コードの使用の詳細については、「[COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="872af-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872af-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="872af-126">See Also</span></span>  
 <span data-ttu-id="872af-127">[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="872af-127">[Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md) </span></span>  
 <span data-ttu-id="872af-128">[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md) </span><span class="sxs-lookup"><span data-stu-id="872af-128">[Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md) </span></span>  
 <span data-ttu-id="872af-129">[方法: シングルファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="872af-129">[How to: Build a Single-File Assembly](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md) </span></span>  
 <span data-ttu-id="872af-130">[方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="872af-130">[How to: Build a Multifile Assembly](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span></span>  
 <span data-ttu-id="872af-131">[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="872af-131">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="872af-132">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="872af-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)

