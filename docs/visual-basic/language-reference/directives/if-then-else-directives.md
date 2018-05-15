---
title: '#もし。。。Then... #Else ディレクティブ'
ms.date: 04/11/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="d1d61-102">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d1d61-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="d1d61-103">条件付きで選択した Visual Basic コード ブロックをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d1d61-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d61-104">構文</span><span class="sxs-lookup"><span data-stu-id="d1d61-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="d1d61-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d1d61-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="d1d61-106">必要な`#If`と`#ElseIf`ステートメント、省略可能な他の場所。</span><span class="sxs-lookup"><span data-stu-id="d1d61-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="d1d61-107">1 つまたは複数の条件付きコンパイラ定数、リテラル、およびに評価される演算子だけで構成される、任意の式`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="d1d61-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="d1d61-108">必要な`#If`ステートメント ブロック、省略可能な他の場所。</span><span class="sxs-lookup"><span data-stu-id="d1d61-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="d1d61-109">Visual Basic プログラム行またはに関連付けられた式が評価された場合にコンパイルされているコンパイラ ディレクティブ`True`です。</span><span class="sxs-lookup"><span data-stu-id="d1d61-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="d1d61-110">終了、`#If`ステートメント ブロックします。</span><span class="sxs-lookup"><span data-stu-id="d1d61-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1d61-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d1d61-111">Remarks</span></span>  
 <span data-ttu-id="d1d61-112">画面の動作で、`#If...Then...#Else`ディレクティブが同じのように見える、`If...Then...Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d1d61-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="d1d61-113">ただし、`#If...Then...#Else`ディレクティブ、コンパイラによってどのようなコンパイルが一方の評価、`If...Then...Else`ステートメントが実行時に条件を評価します。</span><span class="sxs-lookup"><span data-stu-id="d1d61-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="d1d61-114">条件付きコンパイルは通常、さまざまなプラットフォームの同じプログラムのコンパイルに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1d61-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="d1d61-115">防ぐためにも使用する実行可能ファイルに表示されないコードをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="d1d61-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="d1d61-116">条件付きコンパイル中に除外されたコードを完全に省略すると、最終的な実行可能ファイルからサイズやパフォーマンスに影響があるないようにします。</span><span class="sxs-lookup"><span data-stu-id="d1d61-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="d1d61-117">使用して、任意の評価の結果に関係なくすべての式が評価は`Option Compare Binary`します。</span><span class="sxs-lookup"><span data-stu-id="d1d61-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="d1d61-118">`Option Compare`ステートメントでは内の式には影響しません`#If`と`#ElseIf`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d1d61-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1d61-119">単一行形式、 `#If`、 `#Else`、 `#ElseIf`、および`#End If`ディレクティブが存在しません。</span><span class="sxs-lookup"><span data-stu-id="d1d61-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="d1d61-120">他のコードは、ディレクティブのいずれかと同じ行に表示できません。</span><span class="sxs-lookup"><span data-stu-id="d1d61-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="d1d61-121">条件付きコンパイル ブロック内のステートメントは、完全な論理ステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1d61-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="d1d61-122">たとえば、条件付きで、関数の属性だけをコンパイルすることはできませんが、条件付きでその属性と共に、関数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="d1d61-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="d1d61-123">例</span><span class="sxs-lookup"><span data-stu-id="d1d61-123">Example</span></span>
 <span data-ttu-id="d1d61-124">この例では、`#If...Then...#Else`コンストラクトを特定のステートメントをコンパイルするかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d1d61-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d1d61-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1d61-125">See Also</span></span>  
[<span data-ttu-id="d1d61-126">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d1d61-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="d1d61-127">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="d1d61-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="d1d61-128">[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="d1d61-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


