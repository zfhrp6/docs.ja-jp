---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 12895e4a18203a0d6c409a3b2117abbc59fab7a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-keyfile"></a><span data-ttu-id="c506d-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="c506d-102">-keyfile</span></span>
<span data-ttu-id="c506d-103">アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c506d-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c506d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c506d-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c506d-105">引数</span><span class="sxs-lookup"><span data-stu-id="c506d-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="c506d-106">必須。</span><span class="sxs-lookup"><span data-stu-id="c506d-106">Required.</span></span> <span data-ttu-id="c506d-107">キーを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="c506d-107">File that contains the key.</span></span> <span data-ttu-id="c506d-108">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。</span><span class="sxs-lookup"><span data-stu-id="c506d-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c506d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c506d-109">Remarks</span></span>  
 <span data-ttu-id="c506d-110">コンパイラは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを使用し、最終的なアセンブリを署名します。</span><span class="sxs-lookup"><span data-stu-id="c506d-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="c506d-111">キー ファイルを生成する入力`sn -k file`コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="c506d-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="c506d-112">詳細については、[Sn.exe (厳密名ツール)] を参照してください。[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="c506d-112">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="c506d-113">コンパイルする場合`-target:module`、キー ファイルの名前が、モジュール内に保持しを伴うアセンブリをコンパイルするときに作成されるアセンブリに組み込む[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)です。</span><span class="sxs-lookup"><span data-stu-id="c506d-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="c506d-114">また、暗号化情報を [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) でコンパイラに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c506d-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="c506d-115">部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。</span><span class="sxs-lookup"><span data-stu-id="c506d-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="c506d-116">カスタム属性としては、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyFileAttribute>)、Microsoft intermediate language モジュールのソース コードにします。</span><span class="sxs-lookup"><span data-stu-id="c506d-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="c506d-117">場合両方`-keyfile`と[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)がで指定された (コマンド ライン オプションまたはカスタム属性によって)、同じコンパイル時に、コンパイラにより、キー コンテナーを最初に試行します。</span><span class="sxs-lookup"><span data-stu-id="c506d-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="c506d-118">それが成功すると、アセンブリはキー コンテナーの情報で署名されます。</span><span class="sxs-lookup"><span data-stu-id="c506d-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="c506d-119">指定されたファイルを試みますが、コンパイラが、キー コンテナーを見つけられない場合`-keyfile`です。</span><span class="sxs-lookup"><span data-stu-id="c506d-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="c506d-120">これが成功した、キーのファイルの情報と、アセンブリは署名およびキー コンテナーにキー情報がインストールされている場合 (に似て`sn -i`) 次のコンパイル時に、キー コンテナーが有効になるようにします。</span><span class="sxs-lookup"><span data-stu-id="c506d-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="c506d-121">キー ファイルには公開キーだけが含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c506d-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="c506d-122">参照してください[作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリに署名する方法についてです。</span><span class="sxs-lookup"><span data-stu-id="c506d-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c506d-123">`-keyfile`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="c506d-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c506d-124">例</span><span class="sxs-lookup"><span data-stu-id="c506d-124">Example</span></span>  
 <span data-ttu-id="c506d-125">次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="c506d-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c506d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c506d-126">See Also</span></span>  
 [<span data-ttu-id="c506d-127">アセンブリとグローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="c506d-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="c506d-128">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c506d-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c506d-129">-参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c506d-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="c506d-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="c506d-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
