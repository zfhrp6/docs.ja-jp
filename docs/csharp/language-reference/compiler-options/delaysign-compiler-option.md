---
title: "-delaysign (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62f76747a29a90562706dff5fa742316c5b99b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign-c-compiler-options"></a><span data-ttu-id="53d47-102">/delaysign (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="53d47-102">/delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="53d47-103">このオプションを使用すると、出力ファイルに署名用のスペースが予約され、デジタル署名を後で追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="53d47-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d47-104">構文</span><span class="sxs-lookup"><span data-stu-id="53d47-104">Syntax</span></span>  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="53d47-105">引数</span><span class="sxs-lookup"><span data-stu-id="53d47-105">Arguments</span></span>  
 <span data-ttu-id="53d47-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="53d47-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="53d47-107">完全署名されたアセンブリを作成する場合は、**/delaysign-** を使用します。</span><span class="sxs-lookup"><span data-stu-id="53d47-107">Use **/delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="53d47-108">アセンブリに公開キーだけを含める場合は、**/delaysign+** を使用します。</span><span class="sxs-lookup"><span data-stu-id="53d47-108">Use **/delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="53d47-109">既定値は **/delaysign-** です。</span><span class="sxs-lookup"><span data-stu-id="53d47-109">The default is **/delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53d47-110">コメント</span><span class="sxs-lookup"><span data-stu-id="53d47-110">Remarks</span></span>  
 <span data-ttu-id="53d47-111">**/delaysign** オプションは、[/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) または [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) と共に使用しない場合、無効になります。</span><span class="sxs-lookup"><span data-stu-id="53d47-111">The **/delaysign** option has no effect unless used with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="53d47-112">アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。</span><span class="sxs-lookup"><span data-stu-id="53d47-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="53d47-113">結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="53d47-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="53d47-114">アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="53d47-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="53d47-115">たとえば、**/delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。</span><span class="sxs-lookup"><span data-stu-id="53d47-115">For example, using **/delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="53d47-116">テスト後に、[アセンブリ リンカー](../../../framework/tools/al-exe-assembly-linker.md) ユーティリティを使用してアセンブリに秘密キーを配置することにより、そのアセンブリに完全署名できます。</span><span class="sxs-lookup"><span data-stu-id="53d47-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>  
  
 <span data-ttu-id="53d47-117">詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="53d47-117">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="53d47-118">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="53d47-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="53d47-119">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="53d47-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="53d47-120">**[遅延署名のみ]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="53d47-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="53d47-121">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53d47-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d47-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="53d47-122">See Also</span></span>  
 [<span data-ttu-id="53d47-123">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="53d47-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="53d47-124">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="53d47-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
