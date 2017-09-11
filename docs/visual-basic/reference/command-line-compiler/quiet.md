---
title: "/quiet |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
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
ms.openlocfilehash: bc21be8982fea52bf25d0bedeec2b78eee1e705f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="quiet"></a><span data-ttu-id="c9f57-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="c9f57-102">/quiet</span></span>
<span data-ttu-id="c9f57-103">コンパイラで構文関連のエラーと警告のコードが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="c9f57-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f57-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9f57-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9f57-105">コメント</span><span class="sxs-lookup"><span data-stu-id="c9f57-105">Remarks</span></span>  
 <span data-ttu-id="c9f57-106">既定では、`/quiet` は無効です。</span><span class="sxs-lookup"><span data-stu-id="c9f57-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="c9f57-107">コンパイラは、構文に関連するエラーまたは警告にレポートをするときもソース コードからの行が出力されます。</span><span class="sxs-lookup"><span data-stu-id="c9f57-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="c9f57-108">コンパイラ出力を解析するアプリケーションの場合は、診断のテキストのみを出力するコンパイラでより使いやすく場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9f57-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="c9f57-109">次の例で`Module1`を含むソース コードなしでコンパイルされたときにエラーが出力`/quiet`します。</span><span class="sxs-lookup"><span data-stu-id="c9f57-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c9f57-110">Output:</span><span class="sxs-lookup"><span data-stu-id="c9f57-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="c9f57-111">コンパイルされた`/quiet`コンパイラは次のオプションのみを出力します。</span><span class="sxs-lookup"><span data-stu-id="c9f57-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="c9f57-112">`/quiet`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="c9f57-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f57-113">例</span><span class="sxs-lookup"><span data-stu-id="c9f57-113">Example</span></span>  
 <span data-ttu-id="c9f57-114">次のコードのコンパイル`T2.vb`構文に関連するコンパイラの診断用のコードは表示されません。</span><span class="sxs-lookup"><span data-stu-id="c9f57-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9f57-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9f57-115">See Also</span></span>  
 <span data-ttu-id="c9f57-116">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="c9f57-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="c9f57-117"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="c9f57-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
