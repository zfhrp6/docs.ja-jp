---
title: "/keycontainer |Microsoft ドキュメント"
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
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
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
ms.openlocfilehash: a783ef85e6ff2b7c6f889f809291ca8c275e709a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="keycontainer"></a><span data-ttu-id="7b6e2-102">T:System.Reflection.AssemblyKeyNameAttribute</span><span class="sxs-lookup"><span data-stu-id="7b6e2-102">/keycontainer</span></span>
<span data-ttu-id="7b6e2-103">アセンブリに厳密な名前を付けるキー ペアのキー コンテナー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6e2-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b6e2-104">Syntax</span></span>  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b6e2-105">引数</span><span class="sxs-lookup"><span data-stu-id="7b6e2-105">Arguments</span></span>  
  
|<span data-ttu-id="7b6e2-106">用語</span><span class="sxs-lookup"><span data-stu-id="7b6e2-106">Term</span></span>|<span data-ttu-id="7b6e2-107">定義</span><span class="sxs-lookup"><span data-stu-id="7b6e2-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="7b6e2-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-108">Required.</span></span> <span data-ttu-id="7b6e2-109">キーが含まれるコンテナー ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-109">Container file that contains the key.</span></span> <span data-ttu-id="7b6e2-110">ファイル名を引用符で囲みます ("") 名前にスペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b6e2-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7b6e2-111">Remarks</span></span>  
 <span data-ttu-id="7b6e2-112">コンパイラは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを含む、最終的なアセンブリを署名することにより、共有可能なコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="7b6e2-113">キー ファイルを生成する入力`sn -k``file`コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="7b6e2-114">`-i`  オプションは、コンテナーにキーのペアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="7b6e2-115">詳細については、「[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-115">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="7b6e2-116">コンパイルする場合は、 `/target:module`、キー ファイルの名前がモジュールに保持され、使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込む[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)します。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-116">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="7b6e2-117">カスタム属性として、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyNameAttribute>)、Microsoft 中間言語 (MSIL) モジュールのソース コードにします</xref:System.Reflection.AssemblyKeyNameAttribute>。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="7b6e2-118">コンパイラに暗号化情報を渡すことができます[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)します。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-118">You can also pass your encryption information to the compiler with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="7b6e2-119">使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)部分署名されているアセンブリを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-119">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="7b6e2-120">参照してください[の作成と using strong-named Assemblies](https://msdn.microsoft.com/library/xwb8f617)アセンブリへの署名の詳細についてです。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-120">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b6e2-121">`/keycontainer`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-121">The `/keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b6e2-122">例</span><span class="sxs-lookup"><span data-stu-id="7b6e2-122">Example</span></span>  
 <span data-ttu-id="7b6e2-123">次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー コンテナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="7b6e2-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b6e2-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b6e2-124">See Also</span></span>  
 <span data-ttu-id="7b6e2-125">[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b6e2-125">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="7b6e2-126"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b6e2-126"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="7b6e2-127"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="7b6e2-127"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="7b6e2-128"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="7b6e2-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
