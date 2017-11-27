---
title: "相互運用プロジェクトのコンパイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc541911670c533caa97c645085ad09bde5eefdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="ece8f-102">相互運用プロジェクトのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ece8f-102">Compiling an Interop Project</span></span>
<span data-ttu-id="ece8f-103">インポートされた COM 型を含む 1 つ以上のアセンブリを参照する COM 相互運用プロジェクトは、他のマネージ プロジェクトと同じようにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ece8f-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="ece8f-104">相互運用機能アセンブリは、Visual Studio などの開発環境で参照できます。コマンド ライン コンパイラを使用して参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="ece8f-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="ece8f-105">どちらの場合でも、正常にコンパイルするには、相互運用機能アセンブリを、その他のプロジェクト ファイルと同じディレクトリに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece8f-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="ece8f-106">相互運用機能アセンブリを参照する方法には、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="ece8f-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="ece8f-107">埋め込まれた相互運用機能型: [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] および [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="ece8f-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="ece8f-108">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ece8f-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="ece8f-109">相互運用機能アセンブリの配置: 相互運用機能アセンブリへの標準の参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ece8f-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="ece8f-110">この場合、アプリケーションで相互運用機能アセンブリを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece8f-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="ece8f-111">この 2 つの手法の違いの詳細については、「[Using COM Types in Managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)」(マネージ コードでの COM 型の使用) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ece8f-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
 <span data-ttu-id="ece8f-112">Visual Studio での相互運用機能型の埋め込みについては、「[チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み (C# および Visual Basic)](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)」および「[チュートリアル: マネージ アセンブリからの型の埋め込み (C# および Visual Basic)](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ece8f-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) and [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="ece8f-113">コマンド ライン コンパイラを使用して相互運用機能アセンブリを参照し、実行可能ファイルに型情報を埋め込むには、[/link (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) または [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) コンパイラ スイッチを使用して、相互運用機能アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ece8f-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ece8f-114">Visual C++ アプリケーションは型情報を埋め込むことはできませんが、型情報を埋め込むことができるアプリケーションまたはアドインと相互運用できます。</span><span class="sxs-lookup"><span data-stu-id="ece8f-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="ece8f-115">配置時にプライマリ相互運用機能アセンブリを含むアプリケーションをコンパイルするには、**/reference** コンパイラ スイッチを使用して、相互運用機能アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ece8f-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece8f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ece8f-116">See Also</span></span>  
 [<span data-ttu-id="ece8f-117">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="ece8f-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="ece8f-118">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ece8f-118">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="ece8f-119">マネージ コードの COM 型の使用</span><span class="sxs-lookup"><span data-stu-id="ece8f-119">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="ece8f-120">チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み</span><span class="sxs-lookup"><span data-stu-id="ece8f-120">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="ece8f-121">チュートリアル: マネージ アセンブリからの型の埋め込み</span><span class="sxs-lookup"><span data-stu-id="ece8f-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="ece8f-122">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="ece8f-122">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
