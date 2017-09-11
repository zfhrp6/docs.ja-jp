---
title: "方法 : マルチファイル アセンブリをビルドする"
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
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5dd9de26f083209a0e8da79562f914023e008251
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="de30a-102">方法 : マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="de30a-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="de30a-103">この記事では、マルチファイル アセンブリを作成する方法を説明し、プロシージャの各手順を示すコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="de30a-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de30a-104">Visual Studio IDE for C# および Visual Basic は、シングルファイル アセンブリの作成でしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="de30a-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="de30a-105">マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは Visual C++ 付き Visual Studio を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de30a-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="de30a-106">マルチファイル アセンブリを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="de30a-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="de30a-107">アセンブリ内のほかのモジュールによって参照される名前空間を含むすべてのファイルをコンパイルして、コード モジュールを生成します。</span><span class="sxs-lookup"><span data-stu-id="de30a-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="de30a-108">コード モジュールの既定の拡張子は .netmodule です。</span><span class="sxs-lookup"><span data-stu-id="de30a-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="de30a-109">たとえば、`Stringer` ファイルに `myStringer` と呼ばれるクラスを含む `Stringer` という名前空間があるとします。</span><span class="sxs-lookup"><span data-stu-id="de30a-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="de30a-110">`Stringer` クラスには、コンソールに 1 つの行を書き込む `StringerMethod` メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="de30a-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     <span data-ttu-id="de30a-111">[!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]  [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]  [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="de30a-111">[!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]  [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]  [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]</span></span>  
  
     <span data-ttu-id="de30a-112">このコードをコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="de30a-112">Use the following command to compile this code:</span></span>  
  
     <span data-ttu-id="de30a-113">[!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]  [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]  [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="de30a-113">[!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]  [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]  [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]</span></span>  
  
     <span data-ttu-id="de30a-114">*module* パラメーターと **/t:** コンパイラ オプションを指定すると、ファイルはアセンブリではなくモジュールとしてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="de30a-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="de30a-115">コンパイラは、アセンブリに追加できる `Stringer.netmodule` モジュールを生成します。</span><span class="sxs-lookup"><span data-stu-id="de30a-115">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="de30a-116">コード内で参照されるほかのモジュールを示すために必要なコンパイラ オプションを使用して、ほかのすべてのモジュールをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="de30a-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="de30a-117">この手順では、**/addmodule** コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="de30a-117">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="de30a-118">次の例では、`Client` コード モジュールに、手順 1. で作成した `Main` モジュール内のメソッドを参照するエントリ ポイント `Stringer.dll` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="de30a-118">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     <span data-ttu-id="de30a-119">[!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]  [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]  [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="de30a-119">[!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]  [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]  [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]</span></span>  
  
     <span data-ttu-id="de30a-120">このコードをコンパイルするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="de30a-120">Use the following command to compile this code:</span></span>  
  
     <span data-ttu-id="de30a-121">[!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]  [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]  [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="de30a-121">[!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]  [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]  [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]</span></span>  
  
     <span data-ttu-id="de30a-122">このモジュールは後の手順でアセンブリに追加するため、**/t:module** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-122">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="de30a-123">`Client` 内のコードが `Stringer.netmodule` 内のコードによって作成された名前空間を参照するため、**/addmodule** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-123">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="de30a-124">コンパイラは、`Client.netmodule` という別のモジュールへの参照を格納する `Stringer.netmodule` モジュールを生成します。</span><span class="sxs-lookup"><span data-stu-id="de30a-124">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de30a-125">C# コンパイラと Visual Basic コンパイラは、マルチファイル アセンブリを直接作成する場合、次の 2 種類の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="de30a-125">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="de30a-126">2 回のコンパイルで、2 ファイルのアセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="de30a-126">Two compilations create a two-file assembly:</span></span>  
    >   
    >      <span data-ttu-id="de30a-127">[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="de30a-127">[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]</span></span>  
    > -   <span data-ttu-id="de30a-128">1 回のコンパイルで、2 ファイルのアセンブリを作成する。</span><span class="sxs-lookup"><span data-stu-id="de30a-128">One compilation creates a two-file assembly:</span></span>  
    >   
    >      <span data-ttu-id="de30a-129">[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]   [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]   [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="de30a-129">[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]   [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]   [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]</span></span>  
  
3.  <span data-ttu-id="de30a-130">[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用して、アセンブリ マニフェストを格納する出力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="de30a-130">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="de30a-131">このファイルは、アセンブリの一部であるすべてのモジュールまたはリソースについての参照情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="de30a-131">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="de30a-132">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="de30a-132">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="de30a-133">**al** \<*module name*> \<*module name*> …</span><span class="sxs-lookup"><span data-stu-id="de30a-133">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="de30a-134">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span><span class="sxs-lookup"><span data-stu-id="de30a-134">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="de30a-135">このコマンドで、*module name* 引数はアセンブリに含める各モジュールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-135">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="de30a-136">**/main:** オプションは、アセンブリのエントリ ポイントであるメソッド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-136">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="de30a-137">**/out:** オプションは、アセンブリ メタデータを格納する出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-137">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="de30a-138">**/target:** オプションは、アセンブリがコンソール アプリケーション実行可能ファイル (.exe)、Windows 実行可能ファイル (.win)、またはライブラリ ファイル (.lib) であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="de30a-138">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="de30a-139">Al.exe を使用して、コンソール アプリケーションを実行する `myAssembly.exe` という名前のアセンブリを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="de30a-139">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="de30a-140">このアプリケーションは、`Client.netmodule` と `Stringer.netmodule` の 2 つのモジュール、およびアセンブリ メタデータだけを格納する実行可能ファイル `myAssembly.exe,` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="de30a-140">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata .</span></span> <span data-ttu-id="de30a-141">アセンブリのエントリ ポイントは `Main` クラスの `MainClientApp` メソッドで、`Client.dll` 内に配置されています。</span><span class="sxs-lookup"><span data-stu-id="de30a-141">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="de30a-142">[MSIL 逆アセンブラー (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用すると、アセンブリの内容を調査したり、ファイルがアセンブリであるかモジュールであるかを判断したりできます。</span><span class="sxs-lookup"><span data-stu-id="de30a-142">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de30a-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="de30a-143">See Also</span></span>  
 <span data-ttu-id="de30a-144">[アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="de30a-144">[Creating Assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span></span>  
 <span data-ttu-id="de30a-145">[方法: アセンブリの内容を表示する](../../../docs/framework/app-domains/how-to-view-assembly-contents.md) </span><span class="sxs-lookup"><span data-stu-id="de30a-145">[How to: View Assembly Contents](../../../docs/framework/app-domains/how-to-view-assembly-contents.md) </span></span>  
 <span data-ttu-id="de30a-146">[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="de30a-146">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="de30a-147">マルチファイル アセンブリ</span><span class="sxs-lookup"><span data-stu-id="de30a-147">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)

