---
title: -詳細
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f257fce67d8e348b69404411c12ded785cfd68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652130"
---
# <a name="-verbose"></a><span data-ttu-id="a6aab-102">-詳細</span><span class="sxs-lookup"><span data-stu-id="a6aab-102">-verbose</span></span>
<span data-ttu-id="a6aab-103">詳細なステータスとエラー メッセージを生成するためにコンパイラ ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a6aab-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6aab-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6aab-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6aab-105">引数</span><span class="sxs-lookup"><span data-stu-id="a6aab-105">Arguments</span></span>  
 <span data-ttu-id="a6aab-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a6aab-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a6aab-107">任意。</span><span class="sxs-lookup"><span data-stu-id="a6aab-107">Optional.</span></span> <span data-ttu-id="a6aab-108">指定する`-verbose`を指定することと同じ`-verbose+`、詳細メッセージを出力するようコンパイラを停止します。</span><span class="sxs-lookup"><span data-stu-id="a6aab-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="a6aab-109">このオプションの既定値は`-verbose-`します。</span><span class="sxs-lookup"><span data-stu-id="a6aab-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6aab-110">コメント</span><span class="sxs-lookup"><span data-stu-id="a6aab-110">Remarks</span></span>  
 <span data-ttu-id="a6aab-111">`-verbose`オプション、コンパイラによって生成したエラーの合計数に関する情報を表示対象のアセンブリ、モジュールから読み込んでいる、現在コンパイルされているどのファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6aab-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6aab-112">`-verbose`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="a6aab-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6aab-113">例</span><span class="sxs-lookup"><span data-stu-id="a6aab-113">Example</span></span>  
 <span data-ttu-id="a6aab-114">次のコードのコンパイル`In.vb`し、詳細なステータス情報を表示することをコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="a6aab-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6aab-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6aab-115">See Also</span></span>  
 [<span data-ttu-id="a6aab-116">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a6aab-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a6aab-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="a6aab-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
