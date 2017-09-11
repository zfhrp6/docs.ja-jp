---
title: "/moduleassemblyname |Microsoft ドキュメント"
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
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
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
ms.openlocfilehash: 6852b8a0d9874fd65e93cdd9507fe9b7119ce5b3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="moduleassemblyname"></a><span data-ttu-id="e3888-102">/target</span><span class="sxs-lookup"><span data-stu-id="e3888-102">/moduleassemblyname</span></span>
<span data-ttu-id="e3888-103">このモジュールが一部となるアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e3888-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3888-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3888-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="e3888-105">引数</span><span class="sxs-lookup"><span data-stu-id="e3888-105">Arguments</span></span>  
  
|<span data-ttu-id="e3888-106">用語</span><span class="sxs-lookup"><span data-stu-id="e3888-106">Term</span></span>|<span data-ttu-id="e3888-107">定義</span><span class="sxs-lookup"><span data-stu-id="e3888-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="e3888-108">このモジュールの一部となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="e3888-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3888-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e3888-109">Remarks</span></span>  
 <span data-ttu-id="e3888-110">コンパイラ プロセス、`/moduleassemblyname`場合にのみ、オプション、`/target:module`オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e3888-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="e3888-111">モジュールを作成するコンパイラに対応します。</span><span class="sxs-lookup"><span data-stu-id="e3888-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="e3888-112">コンパイラによって作成されたモジュールがで指定されたアセンブリに対してのみ有効ですが、`/moduleassemblyname`オプション。</span><span class="sxs-lookup"><span data-stu-id="e3888-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="e3888-113">別のアセンブリでモジュールを配置する場合は、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e3888-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="e3888-114">`/moduleassemblyname`オプションは、次に該当する場合にのみ必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3888-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="e3888-115">モジュール内のデータ型へのアクセスを必要な`Friend`参照先アセンブリの型。</span><span class="sxs-lookup"><span data-stu-id="e3888-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="e3888-116">参照アセンブリは、モジュールをビルドするアセンブリにフレンド アセンブリのアクセス許可を与えします。</span><span class="sxs-lookup"><span data-stu-id="e3888-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="e3888-117">モジュールの作成の詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)します。</span><span class="sxs-lookup"><span data-stu-id="e3888-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="e3888-118">フレンド アセンブリの詳細については、次を参照してください。[フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)します。</span><span class="sxs-lookup"><span data-stu-id="e3888-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3888-119">`/moduleassemblyname`オプションは、Visual Studio 開発環境内から使用できません。 は、コマンド プロンプトからコンパイルする場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e3888-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3888-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3888-120">See Also</span></span>  
 <span data-ttu-id="e3888-121">[方法: マルチファイル アセンブリをビルド](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span><span class="sxs-lookup"><span data-stu-id="e3888-121">[How to: Build a Multifile Assembly](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span></span>  
<span data-ttu-id="e3888-122"> [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-122"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e3888-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="e3888-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span></span>  
<span data-ttu-id="e3888-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="e3888-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span></span>  
<span data-ttu-id="e3888-127"> [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-127"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="e3888-128"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e3888-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="e3888-129"> [フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span><span class="sxs-lookup"><span data-stu-id="e3888-129"> [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span></span>
