---
title: '方法: ステートメントへのラベル付け (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650125"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="9b813-102">方法: ステートメントへのラベル付け (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b813-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="9b813-103">ステートメント ブロックは、コロンで区切られたコードの行が構成をされています。</span><span class="sxs-lookup"><span data-stu-id="9b813-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="9b813-104">行の識別文字列または整数に続くコードと呼ばれます*というラベルの付いた*です。</span><span class="sxs-lookup"><span data-stu-id="9b813-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="9b813-105">ステートメント ラベルはなどを識別に使用するステートメントを使用するコードの行をマークするために使用`On Error Goto`です。</span><span class="sxs-lookup"><span data-stu-id="9b813-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="9b813-106">ラベルとして使用できるは、有効な Visual Basic 識別子 — などのプログラミング要素を識別するもの、または整数リテラル。</span><span class="sxs-lookup"><span data-stu-id="9b813-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="9b813-107">ラベルは、ソース コードの行の先頭に置く必要があり、後にするかどうかが続くことは、ステートメントが同じ直線上に関係なく、コロン必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b813-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="9b813-108">コンパイラは、行の先頭が任意に定義済みの識別子と一致するかどうかをチェックして、ラベルを識別します。</span><span class="sxs-lookup"><span data-stu-id="9b813-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="9b813-109">そうでない場合、コンパイラはラベルであると想定します。</span><span class="sxs-lookup"><span data-stu-id="9b813-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="9b813-110">ラベルは、独自の宣言領域があるし、その他の識別子に干渉しません。</span><span class="sxs-lookup"><span data-stu-id="9b813-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="9b813-111">ラベルのスコープは、メソッドの本体です。</span><span class="sxs-lookup"><span data-stu-id="9b813-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="9b813-112">ラベルの宣言は、あいまいな場合でも優先されます。</span><span class="sxs-lookup"><span data-stu-id="9b813-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b813-113">ラベルは、メソッドの中の実行可能なステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b813-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="9b813-114">コードの行にラベル付け</span><span class="sxs-lookup"><span data-stu-id="9b813-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="9b813-115">その後にソース コードの行の先頭に、コロン、識別子を配置します。</span><span class="sxs-lookup"><span data-stu-id="9b813-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="9b813-116">たとえば、次のコード行は、ラベルが付いた`Jump`と`120`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="9b813-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9b813-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b813-117">See Also</span></span>  
 [<span data-ttu-id="9b813-118">ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b813-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="9b813-119">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="9b813-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="9b813-120">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="9b813-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
