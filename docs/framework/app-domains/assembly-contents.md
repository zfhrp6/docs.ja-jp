---
title: "アセンブリの内容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a0af2a90d4951b72f8c5100affd6d78ac7f31ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-contents"></a><span data-ttu-id="f0f46-102">アセンブリの内容</span><span class="sxs-lookup"><span data-stu-id="f0f46-102">Assembly Contents</span></span>
<span data-ttu-id="f0f46-103">一般に、静的アセンブリは次の 4 つの要素から構成されます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="f0f46-104">アセンブリ メタデータを保持する[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f46-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="f0f46-105">型メタデータ。</span><span class="sxs-lookup"><span data-stu-id="f0f46-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="f0f46-106">型を実装する MSIL (Microsoft Intermediate Language) コード。</span><span class="sxs-lookup"><span data-stu-id="f0f46-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="f0f46-107">一連のリソース。</span><span class="sxs-lookup"><span data-stu-id="f0f46-107">A set of resources.</span></span>  
  
 <span data-ttu-id="f0f46-108">このうち必須なのはアセンブリ マニフェストだけですが、アセンブリになんらかの機能を与えるには、型またはリソースのいずれかが必要になります。</span><span class="sxs-lookup"><span data-stu-id="f0f46-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="f0f46-109">アセンブリのこれらの要素は、いくつかの方法でグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="f0f46-110">1 つの方法として、次の図に示すように、すべての要素を 1 つの物理ファイルにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="f0f46-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="f0f46-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="f0f46-112">シングルファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="f0f46-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="f0f46-113">別の方法として、1 つのアセンブリの要素を複数のファイルに分けることもできます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="f0f46-114">この操作には、コンパイル済みコードのモジュール (.netmodule)、リソース (.bmp ファイルや .jpg ファイルなど)、アプリケーションで必要なその他のファイルなどを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="f0f46-115">複数の言語で記述されたモジュールを組み合わせたり、使用頻度の低い型を必要なときにだけダウンロードされるモジュールに配置することでアプリケーションのダウンロードを最適化したりする場合は、マルチファイル アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0f46-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="f0f46-116">あるアプリケーションの開発において、特定のユーティリティ コードを独立したモジュールに配置し、サイズの大きいリソース ファイル (ここでは .bmp イメージ) を元のファイルに残しておく例を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="f0f46-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="f0f46-117">.NET Framework では、ファイルが参照される場合にだけそのファイルがダウンロードされます。参照頻度の低いコードをアプリケーションとは別のファイルに保存することで、コードのダウンロードが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="f0f46-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="f0f46-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="f0f46-119">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="f0f46-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0f46-120">マルチファイル アセンブリを構成する各ファイルは、ファイル システムによって物理的にリンクされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f0f46-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="f0f46-121">これらのファイルはアセンブリ マニフェストによってリンクされ、共通言語ランタイムがこれらのファイルをまとめて管理します。</span><span class="sxs-lookup"><span data-stu-id="f0f46-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="f0f46-122">この例では、MyAssembly.dll に含まれるアセンブリ マニフェストに記述されているように、3 つのファイルがすべて 1 つのアセンブリに属しています。</span><span class="sxs-lookup"><span data-stu-id="f0f46-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="f0f46-123">ファイル システムにとっては、これらは 3 つの独立したファイルです。</span><span class="sxs-lookup"><span data-stu-id="f0f46-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="f0f46-124">Util.netmodule というファイルは、アセンブリ情報を含んでいないため、モジュールとしてコンパイルされています。</span><span class="sxs-lookup"><span data-stu-id="f0f46-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="f0f46-125">アセンブリの作成時に、アセンブリ マニフェストが MyAssembly.dll に追加され、その Util.netmodule および Graphic.bmp との関係が示されます。</span><span class="sxs-lookup"><span data-stu-id="f0f46-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="f0f46-126">ソース コードをデザインするときは、作成するアプリケーションの機能を 1 つのファイルにまとめるのか複数のファイルに分割するのか、分割する場合は機能をどのように分けるのかを明確に決める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f46-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="f0f46-127">.NET Framework コードをデザインする場合も同様に、機能を 1 つのアセンブリにまとめるのか複数のアセンブリに分割するのか、分割する場合は機能をどのように分割するのかを決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0f46-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f46-128">参照</span><span class="sxs-lookup"><span data-stu-id="f0f46-128">See Also</span></span>  
 [<span data-ttu-id="f0f46-129">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="f0f46-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="f0f46-130">アセンブリ マニフェスト</span><span class="sxs-lookup"><span data-stu-id="f0f46-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)  
 [<span data-ttu-id="f0f46-131">アセンブリのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f0f46-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
