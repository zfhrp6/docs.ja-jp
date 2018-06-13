---
title: -target (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 7736b8850a7b09f7212e83e05acf0e1994bce0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215499"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="8c600-102">-target (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8c600-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="8c600-103">**-target** コンパイラ オプションは、次の 6 つの形式のいずれかで指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c600-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="8c600-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="8c600-104">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="8c600-105">[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] アプリの .exe ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="8c600-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="8c600-106">-target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="8c600-107">.exe ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="8c600-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="8c600-108">-target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="8c600-109">コード ライブラリを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="8c600-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="8c600-110">-target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="8c600-111">モジュールを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-111">To create a module.</span></span>  
  
 [<span data-ttu-id="8c600-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="8c600-112">-target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="8c600-113">Windows プログラムを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="8c600-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="8c600-114">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="8c600-115">.winmdobj 中間ファイルを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="8c600-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="8c600-116">**-target:module** を指定しない限り、**-target** を使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8c600-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="8c600-117">詳細については、「[共通言語ランタイムのアセンブリ](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)」と「[共通の属性](../../programming-guide/concepts/attributes/common-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c600-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="8c600-118">アセンブリ マニフェストは、コンパイル中の最初の .exe 出力ファイルに配置されます。 .exe 出力ファイルがない場合には、最初の DLL ファイルに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8c600-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="8c600-119">たとえば、次のコマンド ラインでは、マニフェストは `1.exe` に配置されます。</span><span class="sxs-lookup"><span data-stu-id="8c600-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="8c600-120">コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="8c600-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="8c600-121">コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c600-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="8c600-122">**-target:module** で作成されたもの以外のすべての出力ファイルには、アセンブリ マニフェストを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8c600-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="8c600-123">コマンド ラインで複数の出力ファイルを生成する場合は、アセンブリ マニフェストを 1 つだけ作成できます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c600-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="8c600-124">最初の出力ファイル (**-target:exe**、**-target:winexe**、**-target:library**、**-target:module**) にかかわらず、同じコンパイルで生成された他の出力ファイルはすべてモジュール (**-target:module**) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8c600-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="8c600-125">アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c600-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="8c600-126">このコンパイラ オプションのプログラムによる設定の詳細については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c600-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c600-127">参照</span><span class="sxs-lookup"><span data-stu-id="8c600-127">See Also</span></span>  
 [<span data-ttu-id="8c600-128">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="8c600-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="8c600-129">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="8c600-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="8c600-130">-subsystemversion (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8c600-130">-subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
