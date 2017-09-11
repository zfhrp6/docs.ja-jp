---
title: "方法: シングルファイル アセンブリをビルドする"
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
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a584e6ded79489e5e33b07d02dde618541c6cc8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="86fc3-102">方法: シングルファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="86fc3-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="86fc3-103">アセンブリの最も単純な形式であるシングルファイル アセンブリには、型の情報、実装、[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="86fc3-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="86fc3-104">コマンド ライン コンパイラや [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を利用し、シングルファイル アセンブリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="86fc3-105">既定では、コンパイラは .exe 拡張子でアセンブリ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="86fc3-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86fc3-106">C# と Visual Basic の [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] は、シングルファイル アセンブリの作成にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-106">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="86fc3-107">マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++ を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86fc3-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="86fc3-108">次の手順は、コマンド ライン コンパイラでシングルファイル アセンブリを作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="86fc3-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="86fc3-109">拡張子が .exe のアセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="86fc3-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="86fc3-110">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="86fc3-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="86fc3-111">\<*コンパイラ コマンド*> \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="86fc3-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="86fc3-112">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="86fc3-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="86fc3-113">次の例では、`myCode` という名前のコード モジュールから `myCode.exe` という名前のアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="86fc3-114">拡張子が .exe のアセンブリを作成し、出力ファイル名を指定するには</span><span class="sxs-lookup"><span data-stu-id="86fc3-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="86fc3-115">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="86fc3-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="86fc3-116">\<*コンパイラ コマンド*> **/out:**\<*ファイル名*> \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="86fc3-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="86fc3-117">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンド、*ファイル名*は出力ファイル名、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="86fc3-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="86fc3-118">次の例では、`myCode` という名前のコード モジュールから `myAssembly.exe` という名前のアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="86fc3-119">ライブラリ アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="86fc3-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="86fc3-120">ライブラリ アセンブリはクラス ライブラリに似ています。</span><span class="sxs-lookup"><span data-stu-id="86fc3-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="86fc3-121">他のアセンブリにより参照される型が含まれますが、実行を開始するためのエントリ ポイントがありません。</span><span class="sxs-lookup"><span data-stu-id="86fc3-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="86fc3-122">ライブラリ アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="86fc3-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="86fc3-123">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="86fc3-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="86fc3-124">\<*コンパイラ コマンド*> **/t:library** \<*モジュール名*></span><span class="sxs-lookup"><span data-stu-id="86fc3-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="86fc3-125">このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="86fc3-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="86fc3-126">**/out:** オプションなど、他のコンパイラ オプションも使用できます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="86fc3-127">次の例では、`myCode` という名前のコード モジュールから `myCodeAssembly.dll` という名前のライブラリ アセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="86fc3-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="86fc3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="86fc3-128">See Also</span></span>  
 <span data-ttu-id="86fc3-129">[アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="86fc3-129">[Creating Assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span></span>  
 <span data-ttu-id="86fc3-130">[マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="86fc3-130">[Multifile Assemblies](../../../docs/framework/app-domains/multifile-assemblies.md) </span></span>  
 <span data-ttu-id="86fc3-131">[方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="86fc3-131">[How to: Build a Multifile Assembly](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span></span>  
 [<span data-ttu-id="86fc3-132">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="86fc3-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)

