---
title: /target
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a><span data-ttu-id="7f9e3-102">/target</span><span class="sxs-lookup"><span data-stu-id="7f9e3-102">/moduleassemblyname</span></span>
<span data-ttu-id="7f9e3-103">このモジュールが一部となるアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f9e3-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f9e3-105">引数</span><span class="sxs-lookup"><span data-stu-id="7f9e3-105">Arguments</span></span>  
  
|<span data-ttu-id="7f9e3-106">用語</span><span class="sxs-lookup"><span data-stu-id="7f9e3-106">Term</span></span>|<span data-ttu-id="7f9e3-107">定義</span><span class="sxs-lookup"><span data-stu-id="7f9e3-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="7f9e3-108">このモジュールの一部となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f9e3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="7f9e3-109">Remarks</span></span>  
 <span data-ttu-id="7f9e3-110">コンパイラ プロセス、`/moduleassemblyname`場合にのみ、オプション、`/target:module`オプションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="7f9e3-111">これにより、コンパイラでモジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="7f9e3-112">コンパイラによって作成されたモジュールがで指定されたアセンブリに対してのみ有効では、`/moduleassemblyname`オプション。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="7f9e3-113">別のアセンブリでモジュールを配置すると、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="7f9e3-114">`/moduleassemblyname`オプションは、次に当てはまる場合にのみ必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="7f9e3-115">モジュール内のデータ型へのアクセスを必要な`Friend`参照先アセンブリの型。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="7f9e3-116">参照アセンブリがモジュールをビルドするアセンブリにフレンド アセンブリへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="7f9e3-117">モジュールの作成の詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="7f9e3-118">フレンド アセンブリの詳細については、次を参照してください。[フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)です。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f9e3-119">`/moduleassemblyname`オプションは、Visual Studio 開発環境からは利用できません。 使用可能なコマンド プロンプトからコンパイルするときにのみです。</span><span class="sxs-lookup"><span data-stu-id="7f9e3-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9e3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f9e3-120">See Also</span></span>  
 [<span data-ttu-id="7f9e3-121">方法: マルチファイル アセンブリをビルドする</span><span class="sxs-lookup"><span data-stu-id="7f9e3-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="7f9e3-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="7f9e3-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7f9e3-123">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9e3-123">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="7f9e3-124">/main</span><span class="sxs-lookup"><span data-stu-id="7f9e3-124">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="7f9e3-125">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9e3-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="7f9e3-126">/addmodule</span><span class="sxs-lookup"><span data-stu-id="7f9e3-126">/addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="7f9e3-127">アセンブリとグローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="7f9e3-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="7f9e3-128">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="7f9e3-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="7f9e3-129">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="7f9e3-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
