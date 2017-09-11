---
title: "/verbose |Microsoft ドキュメント"
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
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
ms.openlocfilehash: 62285a727217aa897a83a9e746588c80a2c519c0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="verbose"></a><span data-ttu-id="cc1f4-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="cc1f4-102">/verbose</span></span>
<span data-ttu-id="cc1f4-103">詳細なステータスおよびエラー メッセージを生成するコンパイラ ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1f4-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc1f4-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc1f4-105">引数</span><span class="sxs-lookup"><span data-stu-id="cc1f4-105">Arguments</span></span>  
 <span data-ttu-id="cc1f4-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cc1f4-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="cc1f4-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-107">Optional.</span></span> <span data-ttu-id="cc1f4-108">指定する`/verbose`を指定することと同じ`/verbose+`、これにより、コンパイル時に詳細メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="cc1f4-109">このオプションの既定値は`/verbose-`です。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc1f4-110">コメント</span><span class="sxs-lookup"><span data-stu-id="cc1f4-110">Remarks</span></span>  
 <span data-ttu-id="cc1f4-111">`/verbose`オプションが、コンパイラによって発行されたエラーの合計数に関する情報を表示し、対象のアセンブリ、モジュールから読み込んでいるおよび現在コンパイルされているどのファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc1f4-112">`/verbose`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1f4-113">例</span><span class="sxs-lookup"><span data-stu-id="cc1f4-113">Example</span></span>  
 <span data-ttu-id="cc1f4-114">次のコードのコンパイル`In.vb`し、詳細なステータス情報を表示することをコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="cc1f4-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc1f4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc1f4-115">See Also</span></span>  
 <span data-ttu-id="cc1f4-116">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc1f4-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="cc1f4-117"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="cc1f4-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
