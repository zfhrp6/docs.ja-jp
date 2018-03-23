---
title: -quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0ed08e013f088f512ae915daa9aeb2fa6b249b0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-quiet"></a><span data-ttu-id="b2a43-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="b2a43-102">-quiet</span></span>
<span data-ttu-id="b2a43-103">コンパイラで構文関連のエラーと警告のコードが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b2a43-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a43-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2a43-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2a43-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b2a43-105">Remarks</span></span>  
 <span data-ttu-id="b2a43-106">既定では、`-quiet` は無効です。</span><span class="sxs-lookup"><span data-stu-id="b2a43-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="b2a43-107">コンパイラは、構文に関連するエラーまたは警告を報告、したときにも、ソース コードから行を出力します。</span><span class="sxs-lookup"><span data-stu-id="b2a43-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="b2a43-108">コンパイラの出力を解析するアプリケーションでは、コンパイラで診断のテキストのみを出力する方が便利場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2a43-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="b2a43-109">次の例では、`Module1`を含むソース コードなしでコンパイルされるときにエラーが出力`-quiet`です。</span><span class="sxs-lookup"><span data-stu-id="b2a43-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b2a43-110">Output:</span><span class="sxs-lookup"><span data-stu-id="b2a43-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="b2a43-111">コンパイルされた`-quiet`コンパイラは次のオプションのみを出力します。</span><span class="sxs-lookup"><span data-stu-id="b2a43-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="b2a43-112">`-quiet`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="b2a43-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2a43-113">例</span><span class="sxs-lookup"><span data-stu-id="b2a43-113">Example</span></span>  
 <span data-ttu-id="b2a43-114">次のコードのコンパイル`T2.vb`し、コードの構文に関連するコンパイラの診断情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="b2a43-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2a43-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2a43-115">See Also</span></span>  
 [<span data-ttu-id="b2a43-116">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="b2a43-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b2a43-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="b2a43-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
