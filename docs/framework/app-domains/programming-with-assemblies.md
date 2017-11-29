---
title: "アセンブリを使用したプログラミング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="35feb-102">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="35feb-102">Programming with Assemblies</span></span>
<span data-ttu-id="35feb-103">アセンブリは .NET Framework の構成要素であり、配置、バージョン管理、再利用、アクティブ化のスコープの指定、およびセキュリティ アクセス許可の基本単位となります。</span><span class="sxs-lookup"><span data-stu-id="35feb-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="35feb-104">共通言語ランタイムは、型の実装に関して必要な情報をアセンブリから取得します。</span><span class="sxs-lookup"><span data-stu-id="35feb-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="35feb-105">アセンブリは、相互に連携して 1 つの論理的な機能単位を形成するように構築された型やリソースの集合です。</span><span class="sxs-lookup"><span data-stu-id="35feb-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="35feb-106">共通言語ランタイムにとって、型はアセンブリのコンテキストの外部には存在しません。</span><span class="sxs-lookup"><span data-stu-id="35feb-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="35feb-107">このセクションでは、モジュールを作成する方法、モジュールからアセンブリを作成する方法、キー ペアを作成して厳密な名前でアセンブリに署名する方法、およびグローバル アセンブリ キャッシュにアセンブリをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="35feb-108">さらに、[MSIL 逆アセンブラー (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使ってアセンブリ マニフェストの情報を表示する方法も説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35feb-109">.NET Framework Version 2.0 以降では、現在読み込まれているランタイムよりもバージョン番号が新しい .NET Framework のバージョンでコンパイルされたアセンブリは、ランタイムに読み込まれないようになりました。</span><span class="sxs-lookup"><span data-stu-id="35feb-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="35feb-110">これはメジャー コンポーネントとマイナー コンポーネントの組み合わせたバージョン番号に適用されます。</span><span class="sxs-lookup"><span data-stu-id="35feb-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35feb-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="35feb-111">In This Section</span></span>  
 [<span data-ttu-id="35feb-112">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="35feb-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="35feb-113">単一ファイル アセンブリおよびマルチファイル アセンブリの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="35feb-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="35feb-114">アセンブリ名</span><span class="sxs-lookup"><span data-stu-id="35feb-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="35feb-115">アセンブリの名前付けの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="35feb-116">方法: アセンブリの完全修飾名を特定する</span><span class="sxs-lookup"><span data-stu-id="35feb-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="35feb-117">アセンブリの完全修飾名を特定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="35feb-118">イントラネット アプリケーションの完全信頼での実行</span><span class="sxs-lookup"><span data-stu-id="35feb-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="35feb-119">イントラネット共有上の完全に信頼されたアセンブリに対して従来のセキュリティ ポリシーを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="35feb-120">アセンブリの場所</span><span class="sxs-lookup"><span data-stu-id="35feb-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="35feb-121">アセンブリを配置する場所の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="35feb-122">方法: シングルファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="35feb-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="35feb-123">シングルファイル アセンブリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="35feb-124">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="35feb-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="35feb-125">マルチファイル アセンブリを作成する理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="35feb-126">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="35feb-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="35feb-127">マルチファイル アセンブリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="35feb-128">アセンブリ属性の設定</span><span class="sxs-lookup"><span data-stu-id="35feb-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="35feb-129">アセンブリの属性とその設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="35feb-130">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="35feb-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="35feb-131">厳密な名前でアセンブリに署名する方法と理由について説明します。方法に関するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="35feb-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="35feb-132">アセンブリへの遅延署名</span><span class="sxs-lookup"><span data-stu-id="35feb-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="35feb-133">アセンブリに遅延署名する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="35feb-134">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="35feb-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="35feb-135">アセンブリをグローバル アセンブリ キャッシュに追加する方法と理由について説明します。方法に関するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="35feb-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="35feb-136">方法: アセンブリの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="35feb-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="35feb-137">MSIL 逆アセンブラー (Ildasm.exe) を使ってアセンブリの内容を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="35feb-138">共通言語ランタイムでの型の転送</span><span class="sxs-lookup"><span data-stu-id="35feb-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="35feb-139">型の転送を使うことで、既存のアプリケーションを壊さずに異なるアセンブリに型を移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35feb-140">参照</span><span class="sxs-lookup"><span data-stu-id="35feb-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="35feb-141">アセンブリを表す .NET Framework クラス。</span><span class="sxs-lookup"><span data-stu-id="35feb-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35feb-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="35feb-142">Related Sections</span></span>  
 [<span data-ttu-id="35feb-143">方法: アセンブリから型およびメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="35feb-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="35feb-144">プログラムでアセンブリから型およびその他の情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="35feb-145">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="35feb-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="35feb-146">共通言語ランタイムのアセンブリの概念的な概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="35feb-147">アセンブリのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="35feb-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="35feb-148">アセンブリのバインディング、および <xref:System.Reflection.AssemblyVersionAttribute> 属性と <xref:System.Reflection.AssemblyInformationalVersionAttribute> 属性の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="35feb-149">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="35feb-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="35feb-150">ランタイムがバインド要求を満たすために使うアセンブリを決定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="35feb-151">リフレクション</span><span class="sxs-lookup"><span data-stu-id="35feb-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="35feb-152">**Reflection** クラスを使用して、アセンブリに関する情報を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="35feb-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
