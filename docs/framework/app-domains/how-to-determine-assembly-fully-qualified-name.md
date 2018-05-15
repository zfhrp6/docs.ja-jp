---
title: '方法: アセンブリの完全修飾名を特定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663e7456337a2d9c413b15236e7ba1de33fbfa9b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="577a4-102">方法: アセンブリの完全修飾名を特定する</span><span class="sxs-lookup"><span data-stu-id="577a4-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="577a4-103">グローバル アセンブリ キャッシュ内のアセンブリの完全修飾名を検出するには、グローバル アセンブリ キャッシュ ツール ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="577a4-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="577a4-104">「[方法 : グローバル アセンブリ キャッシュの内容を表示する](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577a4-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="577a4-105">グローバル アセンブリ キャッシュにないアセンブリについては、複数の方法で完全修飾アセンブリ名を取得できます。コードを使用しコンソールや変数に情報を出力したり、[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して完全修飾名を含むアセンブリのメタデータを調べたりできます。</span><span class="sxs-lookup"><span data-stu-id="577a4-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="577a4-106">アセンブリがアプリケーションによって既に読み込まれている場合、<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> プロパティの値を取得して、完全修飾名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="577a4-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="577a4-107">この方法を使用して、アセンブリが GAC 内にあるかどうかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="577a4-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="577a4-108">具体的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="577a4-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="577a4-109">アセンブリのファイル システム パスがわかっている場合は、(`Shared` Visual Basic で) 静的 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> メソッドを呼び出して、完全修飾アセンブリ名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="577a4-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="577a4-110">単純な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="577a4-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="577a4-111">[Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリのメタデータを使用できます。これには完全修飾名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="577a4-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="577a4-112">バージョン、カルチャ、アセンブリ名などのアセンブリ属性の設定の詳細については、「[アセンブリ属性の設定](../../../docs/framework/app-domains/set-assembly-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577a4-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="577a4-113">アセンブリに厳密な名前を指定する方法の詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="577a4-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="577a4-114">例</span><span class="sxs-lookup"><span data-stu-id="577a4-114">Example</span></span>  
 <span data-ttu-id="577a4-115">指定したクラスを含むアセンブリの完全限定名をコンソールに表示するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="577a4-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="577a4-116">アプリによって既に読み込まれているアセンブリの名前を取得するので、アセンブリが GAC 内にあるかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="577a4-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="577a4-117">参照</span><span class="sxs-lookup"><span data-stu-id="577a4-117">See Also</span></span>  
 [<span data-ttu-id="577a4-118">アセンブリ名</span><span class="sxs-lookup"><span data-stu-id="577a4-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 [<span data-ttu-id="577a4-119">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="577a4-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="577a4-120">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="577a4-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="577a4-121">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="577a4-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="577a4-122">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="577a4-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="577a4-123">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="577a4-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
