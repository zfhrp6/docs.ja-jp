---
title: "方法: シングルファイル アセンブリをビルドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd9f2bab23fff1bbc4ebb521b167ac8031af3bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="7f0b9-102">方法: シングルファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="7f0b9-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="7f0b9-103">アセンブリの最も単純な形式であるシングルファイル アセンブリには、型の情報、実装、[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="7f0b9-104">コマンド ライン コンパイラや [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を利用し、シングルファイル アセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="7f0b9-105">既定では、コンパイラは .exe 拡張子でアセンブリ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f0b9-106">C# と Visual Basic の [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] は、シングルファイル アセンブリの作成にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-106">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="7f0b9-107">マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++ を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="7f0b9-108">次の手順は、コマンド ライン コンパイラでシングルファイル アセンブリを作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="7f0b9-109">拡張子が .exe のアセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="7f0b9-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="7f0b9-110">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="7f0b9-111">\<*コンパイラ コマンド*> \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="7f0b9-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="7f0b9-112">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="7f0b9-113">次の例では、`myCode` という名前のコード モジュールから `myCode.exe` という名前のアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="7f0b9-114">拡張子が .exe のアセンブリを作成し、出力ファイル名を指定するには</span><span class="sxs-lookup"><span data-stu-id="7f0b9-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="7f0b9-115">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="7f0b9-116">\<*コンパイラ コマンド*> **/out:**\<*ファイル名*> \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="7f0b9-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="7f0b9-117">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンド、*ファイル名*は出力ファイル名、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="7f0b9-118">次の例では、`myCode` という名前のコード モジュールから `myAssembly.exe` という名前のアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="7f0b9-119">ライブラリ アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="7f0b9-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="7f0b9-120">ライブラリ アセンブリはクラス ライブラリに似ています。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="7f0b9-121">他のアセンブリにより参照される型が含まれますが、実行を開始するためのエントリ ポイントがありません。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="7f0b9-122">ライブラリ アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="7f0b9-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="7f0b9-123">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="7f0b9-124">\<*コンパイラ コマンド*> **/t:library** \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="7f0b9-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="7f0b9-125">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="7f0b9-126">**/out:** オプションなど、他のコンパイラ オプションも使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="7f0b9-127">次の例では、`myCode` という名前のコード モジュールから `myCodeAssembly.dll` という名前のライブラリ アセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7f0b9-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f0b9-128">参照</span><span class="sxs-lookup"><span data-stu-id="7f0b9-128">See Also</span></span>  
 [<span data-ttu-id="7f0b9-129">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="7f0b9-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="7f0b9-130">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="7f0b9-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="7f0b9-131">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="7f0b9-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="7f0b9-132">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="7f0b9-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
