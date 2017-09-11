---
title: "/keyfile |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ec63fd990b8524bbc212a33714ec8380a8c99f32
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="keyfile"></a><span data-ttu-id="605f3-102">T:System.Reflection.AssemblyKeyFileAttribute</span><span class="sxs-lookup"><span data-stu-id="605f3-102">/keyfile</span></span>
<span data-ttu-id="605f3-103">アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="605f3-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605f3-104">構文</span><span class="sxs-lookup"><span data-stu-id="605f3-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="605f3-105">引数</span><span class="sxs-lookup"><span data-stu-id="605f3-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="605f3-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="605f3-106">Required.</span></span> <span data-ttu-id="605f3-107">キーを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="605f3-107">File that contains the key.</span></span> <span data-ttu-id="605f3-108">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="605f3-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="605f3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="605f3-109">Remarks</span></span>  
 <span data-ttu-id="605f3-110">コンパイラでは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを含む、最終的なアセンブリを署名します。</span><span class="sxs-lookup"><span data-stu-id="605f3-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="605f3-111">キー ファイルを生成する入力`sn -k file`コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="605f3-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="605f3-112">詳細については、「[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="605f3-112">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="605f3-113">コンパイルする場合は、 `/target:module`、キー ファイルの名前がモジュールに保持され、使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込む[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)します。</span><span class="sxs-lookup"><span data-stu-id="605f3-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="605f3-114">コンパイラに暗号化情報を渡すことができます[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)します。</span><span class="sxs-lookup"><span data-stu-id="605f3-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="605f3-115">使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)部分署名されているアセンブリを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="605f3-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="605f3-116">カスタム属性として、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyFileAttribute>)、Microsoft 中間言語のモジュールのソース コードにします</xref:System.Reflection.AssemblyKeyFileAttribute>。</span><span class="sxs-lookup"><span data-stu-id="605f3-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="605f3-117">例では両方とも`/keyfile`と[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)がで指定された (コマンド ライン オプションまたはカスタム属性によって)、同じコンパイル時に、コンパイラは、まず、キー コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="605f3-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="605f3-118">成功すると、アセンブリがキー コンテナー内の情報で署名します。</span><span class="sxs-lookup"><span data-stu-id="605f3-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="605f3-119">指定されたファイルを試みる場合は、コンパイラでは、キー コンテナーが見つからない、`/keyfile`です。</span><span class="sxs-lookup"><span data-stu-id="605f3-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="605f3-120">正常に実行する場合、キー ファイルの情報と、アセンブリが署名、キー コンテナーにキーの情報がインストールされている場合 (のような`sn -i`) 次のコンパイル時に、キー コンテナーが有効になるようにします。</span><span class="sxs-lookup"><span data-stu-id="605f3-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="605f3-121">キー ファイルが公開キーのみを含めることがありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="605f3-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="605f3-122">参照してください[の作成と using strong-named Assemblies](https://msdn.microsoft.com/library/xwb8f617)アセンブリへの署名の詳細についてです。</span><span class="sxs-lookup"><span data-stu-id="605f3-122">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="605f3-123">`/keyfile`内から使用可能オプションは、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開発環境には、コマンドラインからコンパイルする場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="605f3-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="605f3-124">例</span><span class="sxs-lookup"><span data-stu-id="605f3-124">Example</span></span>  
 <span data-ttu-id="605f3-125">次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="605f3-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="605f3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="605f3-126">See Also</span></span>  
 <span data-ttu-id="605f3-127">[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="605f3-127">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="605f3-128"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="605f3-128"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="605f3-129"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="605f3-129"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="605f3-130"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="605f3-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
