---
title: "-keycontainer (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
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
ms.openlocfilehash: 5d27fa0b80ca6df15394ad1fda149377cac41a8b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="keycontainer-c-compiler-options"></a><span data-ttu-id="715f6-102">/keycontainer (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="715f6-102">/keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="715f6-103">暗号化キー コンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="715f6-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="715f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="715f6-104">Syntax</span></span>  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="715f6-105">引数</span><span class="sxs-lookup"><span data-stu-id="715f6-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="715f6-106">厳密な名前のキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="715f6-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="715f6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="715f6-107">Remarks</span></span>  
 <span data-ttu-id="715f6-108">**/keycontainer** オプションを指定すると、コンパイラは、指定したコンテナーから公開キーをアセンブリ マニフェストに挿入し、秘密キーで最終アセンブリに署名することで、共有可能なコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="715f6-108">When the **/keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="715f6-109">キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="715f6-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="715f6-110">sn -i は、キー ペアをコンテナーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="715f6-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="715f6-111">[/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、このモジュールを [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) でアセンブリにコンパイルするときに、アセンブリに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="715f6-111">If you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="715f6-112">このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="715f6-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="715f6-113">また、暗号化情報を [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="715f6-113">You can also pass your encryption information to the compiler with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="715f6-114">公開キーをアセンブリ マニフェストに追加してだけおき、アセンブリの署名はテスト後まで待って行いたい場合は、[/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="715f6-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="715f6-115">詳しくは、「[厳密な名前付きアセンブリの作成と使用](https://msdn.microsoft.com/library/xwb8f617)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="715f6-115">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="715f6-116">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="715f6-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="715f6-117">このコンパイラ オプションは、Visual Studio 開発環境では使うことができません。</span><span class="sxs-lookup"><span data-stu-id="715f6-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="715f6-118">このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> を使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="715f6-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715f6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="715f6-119">See Also</span></span>  
 <span data-ttu-id="715f6-120">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="715f6-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="715f6-121">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="715f6-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

