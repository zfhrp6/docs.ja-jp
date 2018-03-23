---
title: -詳細
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0523409e53a8c7ea34de7dcc24b1bce2885a183
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-verbose"></a><span data-ttu-id="4d5ff-102">-詳細</span><span class="sxs-lookup"><span data-stu-id="4d5ff-102">-verbose</span></span>
<span data-ttu-id="4d5ff-103">詳細なステータスとエラー メッセージを生成するためにコンパイラ ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d5ff-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d5ff-105">引数</span><span class="sxs-lookup"><span data-stu-id="4d5ff-105">Arguments</span></span>  
 <span data-ttu-id="4d5ff-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4d5ff-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4d5ff-107">任意。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-107">Optional.</span></span> <span data-ttu-id="4d5ff-108">指定する`-verbose`を指定することと同じ`-verbose+`、詳細メッセージを出力するようコンパイラを停止します。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="4d5ff-109">このオプションの既定値は`-verbose-`します。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d5ff-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4d5ff-110">Remarks</span></span>  
 <span data-ttu-id="4d5ff-111">`-verbose`オプション、コンパイラによって生成したエラーの合計数に関する情報を表示対象のアセンブリ、モジュールから読み込んでいる、現在コンパイルされているどのファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d5ff-112">`-verbose`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d5ff-113">例</span><span class="sxs-lookup"><span data-stu-id="4d5ff-113">Example</span></span>  
 <span data-ttu-id="4d5ff-114">次のコードのコンパイル`In.vb`し、詳細なステータス情報を表示することをコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="4d5ff-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d5ff-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d5ff-115">See Also</span></span>  
 [<span data-ttu-id="4d5ff-116">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="4d5ff-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4d5ff-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="4d5ff-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
