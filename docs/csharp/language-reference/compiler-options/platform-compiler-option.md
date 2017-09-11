---
title: "-platform (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /platform
dev_langs:
- CSharp
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44d4cadbc45eb141ecb7a83345d2a7a834ce5299
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="platform-c-compiler-options"></a><span data-ttu-id="2c369-102">/platform (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2c369-102">/platform (C# Compiler Options)</span></span>
<span data-ttu-id="2c369-103">アセンブリを実行できる共通言語ランタイム (CLR) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c369-103">Specifies which version of the common language runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c369-104">構文</span><span class="sxs-lookup"><span data-stu-id="2c369-104">Syntax</span></span>  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c369-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c369-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="2c369-106">anycpu (既定値)、anycpu32bitpreferred、ARM、x64、x86、または Itanium。</span><span class="sxs-lookup"><span data-stu-id="2c369-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c369-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2c369-107">Remarks</span></span>  
  
-   <span data-ttu-id="2c369-108">**anycpu** (既定) は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="2c369-109">可能な場合は、アプリケーションを 64 ビット プロセスとして実行し、32 ビット モードしか使用できない場合は、32 ビットにフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="2c369-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="2c369-110">**anycpu32bitpreferred** は、任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="2c369-111">64 ビットと 32 ビットの両方のアプリケーションをサポートするシステムで、32 ビット モードでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="2c369-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="2c369-112">このオプションは、.NET Framework 4.5 を対象とするプロジェクトに対してのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="2c369-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="2c369-113">**ARM** は、Advanced RISC Machine (ARM) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="2c369-114">**x64** は、AMD64 または EM64T 命令セットをサポートするコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-114">**x64** compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="2c369-115">**x86** は、32 ビット x86 互換共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible common language runtime.</span></span>  
  
-   <span data-ttu-id="2c369-116">**Itanium** は、Itanium プロセッサを搭載したコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="2c369-116">**Itanium** compiles your assembly to be run by the 64-bit common language runtime on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="2c369-117">64 ビット Windows オペレーティング システムの場合:</span><span class="sxs-lookup"><span data-stu-id="2c369-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="2c369-118">**/platform:x86** でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c369-118">Assemblies compiled with **/platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="2c369-119">**/platform:anycpu** でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c369-119">A DLL compiled with the **/platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="2c369-120">**/platform:anycpu** でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c369-120">Executables that are compiled with the **/platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="2c369-121">**/platform:anycpu32bitpreferred** でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c369-121">Executables compiled with **/platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="2c369-122">**anycpu32bitpreferred** 設定は、実行可能 (.EXE) ファイルに対してのみ有効で、.NET Framework 4.5 が必要です。</span><span class="sxs-lookup"><span data-stu-id="2c369-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="2c369-123">Windows 64 ビット オペレーティング システムで実行するアプリケーションの開発に関する詳細は、「[64 ビット アプリケーション](https://msdn.microsoft.com/library/ms241064)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c369-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](https://msdn.microsoft.com/library/ms241064).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2c369-124">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="2c369-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="2c369-125">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c369-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="2c369-126">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c369-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="2c369-127">**プラットフォーム ターゲット** プロパティを変更し、.NET Framework 4.5 を対象とするプロジェクトでは、**[32 ビットを優先]** チェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="2c369-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="2c369-128">**注 /platform** は、Visual C# Express では開発環境で使用できません。</span><span class="sxs-lookup"><span data-stu-id="2c369-128">**Note /platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="2c369-129">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c369-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c369-130">例</span><span class="sxs-lookup"><span data-stu-id="2c369-130">Example</span></span>  
 <span data-ttu-id="2c369-131">次の例では、**/platform** オプションを使用して、Windows 64 ビット オペレーティング システムで 64 ビット CLR によりアプリケーションを実行することを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2c369-131">The following example shows how to use the **/platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c369-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c369-132">See Also</span></span>  
 <span data-ttu-id="2c369-133">[C# コンパイラのオプション](index.md) </span><span class="sxs-lookup"><span data-stu-id="2c369-133">[C# Compiler Options](index.md) </span></span>  
 [<span data-ttu-id="2c369-134">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="2c369-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

