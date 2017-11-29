---
title: "#<a name=\"ifthenelse-directives\"></a>もし。。。Then... #Else ディレクティブ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="55969-102">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="55969-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="55969-103">条件付きで選択した Visual Basic コード ブロックをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="55969-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55969-104">構文</span><span class="sxs-lookup"><span data-stu-id="55969-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="55969-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="55969-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="55969-106">必要な`#If`と`#ElseIf`ステートメント、省略可能な他の場所。</span><span class="sxs-lookup"><span data-stu-id="55969-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="55969-107">1 つまたは複数の条件付きコンパイラ定数、リテラル、およびに評価される演算子だけで構成される、任意の式`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="55969-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="55969-108">必要な`#If`ステートメント ブロック、省略可能な他の場所。</span><span class="sxs-lookup"><span data-stu-id="55969-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="55969-109">Visual Basic プログラム行またはに関連付けられた式が評価された場合にコンパイルされているコンパイラ ディレクティブ`True`です。</span><span class="sxs-lookup"><span data-stu-id="55969-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="55969-110">終了、`#If`ステートメント ブロックします。</span><span class="sxs-lookup"><span data-stu-id="55969-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55969-111">コメント</span><span class="sxs-lookup"><span data-stu-id="55969-111">Remarks</span></span>  
 <span data-ttu-id="55969-112">画面の動作で、`#If...Then...#Else`ディレクティブが同じのように見える、`If...Then...Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="55969-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="55969-113">ただし、`#If...Then...#Else`ディレクティブ、コンパイラによってどのようなコンパイルが一方の評価、`If...Then...Else`ステートメントが実行時に条件を評価します。</span><span class="sxs-lookup"><span data-stu-id="55969-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="55969-114">条件付きコンパイルは通常、さまざまなプラットフォームの同じプログラムのコンパイルに使用されます。</span><span class="sxs-lookup"><span data-stu-id="55969-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="55969-115">防ぐためにも使用する実行可能ファイルに表示されないコードをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="55969-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="55969-116">条件付きコンパイル中に除外されたコードを完全に省略すると、最終的な実行可能ファイルからサイズやパフォーマンスに影響があるないようにします。</span><span class="sxs-lookup"><span data-stu-id="55969-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="55969-117">使用して、任意の評価の結果に関係なくすべての式が評価は`Option Compare Binary`します。</span><span class="sxs-lookup"><span data-stu-id="55969-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="55969-118">`Option Compare`ステートメントでは内の式には影響しません`#If`と`#ElseIf`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="55969-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55969-119">単一行形式、 `#If`、 `#Else`、 `#ElseIf`、および`#End If`ディレクティブが存在しません。</span><span class="sxs-lookup"><span data-stu-id="55969-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="55969-120">他のコードは、ディレクティブのいずれかと同じ行に表示できません。</span><span class="sxs-lookup"><span data-stu-id="55969-120">No other code can appear on the same line as any of the directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55969-121">例</span><span class="sxs-lookup"><span data-stu-id="55969-121">Example</span></span>  
 <span data-ttu-id="55969-122">この例では、`#If...Then...#Else`コンストラクトを特定のステートメントをコンパイルするかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="55969-122">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="55969-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="55969-123">See Also</span></span>  
 [<span data-ttu-id="55969-124">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="55969-124">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="55969-125">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="55969-125">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="55969-126">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="55969-126">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
