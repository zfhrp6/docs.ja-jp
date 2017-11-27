---
title: "COM 相互運用機能によるデータのマーシャリング"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="0b54b-102">COM 相互運用機能によるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="0b54b-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="0b54b-103">COM 相互運用は、マネージ コードから COM オブジェクトを使用すること、およびマネージ オブジェクトを COM に公開することの、両方の操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="0b54b-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="0b54b-104">COM との間でデータをマーシャリングする操作のサポートは広範で、ほとんどの場合、正しいマーシャリング動作が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0b54b-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="0b54b-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、以下の COM 相互運用ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0b54b-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="0b54b-106">[タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)、これは COM タイプ ライブラリを相互運用アセンブリに変換します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="0b54b-107">このアセンブリから、相互運用マーシャリング サービスは、マネージ メモリとアンマネージ メモリ間のデータ マーシャリングを実行するラッパーを生成します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="0b54b-108">[タイプ ライブラリ エクスポーター (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、これは COM タイプ ライブラリをアセンブリから生成して、メソッド呼び出しの際にマーシャリングを実行するラッパーを生成します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="0b54b-109">次のセクションでは、ことができます (または必要があります) を指定すると追加の型情報では、マーシャラーは、相互運用ラッパーをカスタマイズするためのプロセスを説明するトピックへリンクします。</span><span class="sxs-lookup"><span data-stu-id="0b54b-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b54b-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0b54b-110">In This Section</span></span>  
<span data-ttu-id="0b54b-111">[方法: 手動でラッパーを作成します。](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="0b54b-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="0b54b-112">マネージ ソース コードで COM ラッパーを手動で作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="0b54b-113">方法: マネージ コード DCOM を WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="0b54b-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="0b54b-114">最も安全なソリューションのマネージ DCOM コードを WCF に移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b54b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b54b-115">Related Sections</span></span>  
 <span data-ttu-id="0b54b-116">[COM のデータ型](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-116">[COM Data Types](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-117">対応するマネージとアンマネージのデータ型を提供します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="0b54b-118">[COM 呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-119">使用してデータ型を明示的にマーシャ リングする方法について説明します、<xref:System.Runtime.InteropServices.MarshalAsAttribute>デザイン時の属性です。</span><span class="sxs-lookup"><span data-stu-id="0b54b-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="0b54b-120">[ランタイム呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-121">相互運用アセンブリで型のマーシャリング動作を調整する方法、および COM 型を手動で定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="0b54b-122">[高度な COM 相互運用性](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-122">[Advanced COM Interoperability](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-123">.NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="0b54b-124">[アセンブリからタイプ ライブラリへの変換の要約](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-125">アセンブリからタイプ ライブラリにエクスポート変換するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="0b54b-126">[タイプ ライブラリからアセンブリへの変換の要約](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-127">タイプ ライブラリからアセンブリにインポート変換するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="0b54b-128">[ジェネリック型を使用する相互運用](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b54b-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0b54b-129">COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b54b-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
