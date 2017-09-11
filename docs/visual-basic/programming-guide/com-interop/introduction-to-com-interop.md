---
title: "COM 相互運用 (Visual Basic) の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6a50a89db3f24d7e34c1fc683b5f712f3a6992bf
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a><span data-ttu-id="0cf1d-102">COM 相互運用の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cf1d-102">Introduction to COM Interop (Visual Basic)</span></span>
<span data-ttu-id="0cf1d-103">コンポーネント オブジェクト モデル (COM) には、他のコンポーネントやアプリケーションをホストする機能を公開するオブジェクトことができます。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-103">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="0cf1d-104">COM オブジェクトは、基本となる Windows 長年にわたってプログラミングされていますが、共通言語ランタイム (CLR) 用に設計されたアプリケーションでは、多くの利点が提供しています。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-104">While COM objects have been fundamental to Windows programming for many years, applications designed for the common language runtime (CLR) offer many advantages.</span></span>  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<span data-ttu-id="0cf1d-105">アプリケーションが最終的に置き換わります com 開発</span><span class="sxs-lookup"><span data-stu-id="0cf1d-105"> applications will eventually replace those developed with COM.</span></span> <span data-ttu-id="0cf1d-106">それまでは、使用またはを使用して COM オブジェクトを作成する必要があります[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-106">Until then, you may have to use or create COM objects by using [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span> <span data-ttu-id="0cf1d-107">Com 相互運用性または*COM 相互運用機能*への移行中に既存の COM オブジェクトを使用することができます、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]独自のペースでします。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-107">Interoperability with COM, or *COM interop*, enables you to use existing COM objects while transitioning to the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] at your own pace.</span></span>  
  
 <span data-ttu-id="0cf1d-108">使用して、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] COM コンポーネントを作成するには、登録しない COM 相互運用機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-108">By using the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] to create COM components, you can use registration-free COM interop.</span></span> <span data-ttu-id="0cf1d-109">これによって、どの DLL バージョンを有効にすると、1 つ以上のバージョンが、コンピューターにインストールされて、により、エンドユーザーは XCOPY または FTP を使用のコンピューターに適切なディレクトリにアプリケーションをコピーする実行できる場合を制御できます。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-109">This lets you control which DLL version is enabled when more than one version is installed on a computer, and lets end users use XCOPY or FTP to copy your application to an appropriate directory on their computer where it can be run.</span></span> <span data-ttu-id="0cf1d-110">詳細については、次を参照してください。 [Registration-free COM 相互運用機能](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)です。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-110">For more information, see [Registration-Free COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).</span></span>  
  
## <a name="managed-code-and-data"></a><span data-ttu-id="0cf1d-111">マネージ コードとデータ</span><span class="sxs-lookup"><span data-stu-id="0cf1d-111">Managed Code and Data</span></span>  
 <span data-ttu-id="0cf1d-112">用に開発されたコード、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]と呼ばれます*マネージ コード*、CLR によって使用されるメタデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-112">Code developed for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is referred to as *managed code*, and contains metadata that is used by CLR.</span></span> <span data-ttu-id="0cf1d-113">によって使用されるデータ[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションと呼ばれる*管理データ*型の割り当て、メモリを再利用、および実行のチェックなど、ランタイムがデータに関連するタスクを管理するためです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-113">Data used by [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications is called *managed data* because the runtime manages data-related tasks such as allocating and reclaiming memory and performing type checking.</span></span> <span data-ttu-id="0cf1d-114">既定では、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]マネージ コードとデータを使用して、アンマネージ コードと相互運用機能アセンブリを (このページの後半で説明します) を使用して COM オブジェクトのデータにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-114">By default, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] uses managed code and data, but you can access the unmanaged code and data of COM objects using interop assemblies (described later on this page).</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="0cf1d-115">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="0cf1d-115">Assemblies</span></span>  
 <span data-ttu-id="0cf1d-116">アセンブリの主な構成要素とは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-116">An assembly is the primary building block of a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span> <span data-ttu-id="0cf1d-117">これは、ビルド、バージョン管理、および&1; つまたは複数のファイルを含む単一の実装の単位として配置される機能のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-117">It is a collection of functionality that is built, versioned, and deployed as a single implementation unit containing one or more files.</span></span> <span data-ttu-id="0cf1d-118">各アセンブリには、アセンブリ マニフェストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-118">Each assembly contains an assembly manifest.</span></span>  
  
## <a name="type-libraries-and-assembly-manifests"></a><span data-ttu-id="0cf1d-119">タイプ ライブラリとアセンブリのマニフェスト</span><span class="sxs-lookup"><span data-stu-id="0cf1d-119">Type Libraries and Assembly Manifests</span></span>  
 <span data-ttu-id="0cf1d-120">タイプ ライブラリでは、メンバー名やデータ型など、COM オブジェクトの特性について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-120">Type libraries describe characteristics of COM objects, such as member names and data types.</span></span> <span data-ttu-id="0cf1d-121">アセンブリのマニフェストの同じ機能を実行する[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-121">Assembly manifests perform the same function for [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications.</span></span> <span data-ttu-id="0cf1d-122">次の情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-122">They include information about the following:</span></span>  
  
-   <span data-ttu-id="0cf1d-123">アセンブリの id、バージョン、カルチャ、およびデジタル署名します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-123">Assembly identity, version, culture, and digital signature.</span></span>  
  
-   <span data-ttu-id="0cf1d-124">アセンブリの実装を構成するファイルです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-124">Files that make up the assembly implementation.</span></span>  
  
-   <span data-ttu-id="0cf1d-125">型と、アセンブリを構成するリソースです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-125">Types and resources that make up the assembly.</span></span> <span data-ttu-id="0cf1d-126">これには、アセンブリからエクスポートされるものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-126">This includes those that are exported from it.</span></span>  
  
-   <span data-ttu-id="0cf1d-127">他のアセンブリに依存関係をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-127">Compile-time dependencies on other assemblies.</span></span>  
  
-   <span data-ttu-id="0cf1d-128">アセンブリを正しく実行するために必要なアクセス許可です。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-128">Permissions required for the assembly to run correctly.</span></span>  
  
 <span data-ttu-id="0cf1d-129">アセンブリおよびアセンブリのマニフェストの詳細については、次を参照してください。[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-129">For more information about assemblies and assembly manifests, see [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
### <a name="importing-and-exporting-type-libraries"></a><span data-ttu-id="0cf1d-130">インポートおよびタイプ ライブラリをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-130">Importing and Exporting Type Libraries</span></span>  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="0cf1d-131">タイプ ライブラリから情報をインポートできる Tlbimp ユーティリティが含まれています、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-131"> contains a utility, Tlbimp, that lets you import information from a type library into a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span> <span data-ttu-id="0cf1d-132">Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-132">You can generate type libraries from assemblies by using the Tlbexp utility.</span></span>  
  
 <span data-ttu-id="0cf1d-133">Tlbimp と Tlbexp については、次を参照してください。 [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)と[Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-133">For information about Tlbimp and Tlbexp, see [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) and [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="0cf1d-134">相互運用機能アセンブリ</span><span class="sxs-lookup"><span data-stu-id="0cf1d-134">Interop Assemblies</span></span>  
 <span data-ttu-id="0cf1d-135">相互運用機能アセンブリは[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]ブリッジ マネージ リソースとアンマネージ間するアセンブリ コードに、それと等価に COM オブジェクト メンバーのマッピング[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]メンバーを管理します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-135">Interop assemblies are [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies that bridge between managed and unmanaged code, mapping COM object members to equivalent [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] managed members.</span></span> <span data-ttu-id="0cf1d-136">によって作成された相互運用機能アセンブリ[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]の相互運用マーシャ リングなどの COM オブジェクトの使用の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-136">Interop assemblies created by [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] handle many of the details of working with COM objects, such as interoperability marshaling.</span></span>  
  
## <a name="interoperability-marshaling"></a><span data-ttu-id="0cf1d-137">相互運用マーシャ リング</span><span class="sxs-lookup"><span data-stu-id="0cf1d-137">Interoperability Marshaling</span></span>  
 <span data-ttu-id="0cf1d-138">すべて[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションを使用するプログラミング言語に関係なく、オブジェクトの相互運用性を有効にする一般的な種類のセットを共有します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-138">All [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] applications share a set of common types that enable interoperability of objects, regardless of the programming language that is used.</span></span> <span data-ttu-id="0cf1d-139">パラメーターと COM オブジェクトの戻り値もマネージ コードで使用されるものとは異なるデータ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-139">The parameters and return values of COM objects sometimes use data types that differ from those used in managed code.</span></span> <span data-ttu-id="0cf1d-140">*相互運用マーシャ リング*パッケージ パラメーターと戻り値を等価のデータ型のプロセスは、COM オブジェクトとの間を移動します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-140">*Interoperability marshaling* is the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="0cf1d-141">詳細については、次を参照してください。[相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)します。</span><span class="sxs-lookup"><span data-stu-id="0cf1d-141">For more information, see [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf1d-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf1d-142">See Also</span></span>  
 <span data-ttu-id="0cf1d-143">[COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-143">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="0cf1d-144"> [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-144"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="0cf1d-145"> [アンマネージ コードとの相互運用](https://msdn.microsoft.com/library/sd10k43k) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-145"> [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k) </span></span>  
<span data-ttu-id="0cf1d-146"> [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-146"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="0cf1d-147"> [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-147"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="0cf1d-148"> [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-148"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="0cf1d-149"> [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-149"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="0cf1d-150"> [相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a) </span><span class="sxs-lookup"><span data-stu-id="0cf1d-150"> [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a) </span></span>  
<span data-ttu-id="0cf1d-151"> [登録を必要としない COM 相互運用機能](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)</span><span class="sxs-lookup"><span data-stu-id="0cf1d-151"> [Registration-Free COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)</span></span>
