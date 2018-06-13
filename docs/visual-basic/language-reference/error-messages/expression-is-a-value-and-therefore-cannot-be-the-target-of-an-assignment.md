---
title: Expression は値であるため、代入式のターゲットにすることはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590239"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="74af3-102">Expression は値であるため、代入式のターゲットにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74af3-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="74af3-103">ステートメントでは、式に値を代入しようとしています。</span><span class="sxs-lookup"><span data-stu-id="74af3-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="74af3-104">実行時に、書き込み可能な変数、プロパティ、または配列要素にのみ値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="74af3-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="74af3-105">次の例では、このエラーが発生する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="74af3-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="74af3-106">同様の例は、プロパティと配列の要素に適用でした。</span><span class="sxs-lookup"><span data-stu-id="74af3-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="74af3-107">**間接的なアクセス。**</span><span class="sxs-lookup"><span data-stu-id="74af3-107">**Indirect Access.**</span></span> <span data-ttu-id="74af3-108">値型を通じて間接的にアクセスには、このエラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="74af3-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="74af3-109">値を設定しようとしています。 次のコード例を検討してください<xref:System.Drawing.Point>を通じて間接的にアクセスして<xref:System.Windows.Forms.Control.Location%2A>です。</span><span class="sxs-lookup"><span data-stu-id="74af3-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="74af3-110">割り当てを一時的なのみを作成するために前の例の最後のステートメントが失敗した、<xref:System.Drawing.Point>によって返される構造体、<xref:System.Windows.Forms.Control.Location%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="74af3-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="74af3-111">構造体は、値の型と、ステートメントの実行後、一時的な構造は保持されません。</span><span class="sxs-lookup"><span data-stu-id="74af3-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="74af3-112">宣言との変数を使用して、問題が解決<xref:System.Windows.Forms.Control.Location%2A>の永続的な割り当てを作成する、<xref:System.Drawing.Point>構造体。</span><span class="sxs-lookup"><span data-stu-id="74af3-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="74af3-113">次の例では、前の例の最後のステートメントを置き換えることができるコードを示します。</span><span class="sxs-lookup"><span data-stu-id="74af3-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="74af3-114">**エラー ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="74af3-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74af3-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="74af3-115">To correct this error</span></span>  
  
-   <span data-ttu-id="74af3-116">ステートメントは、式に値を割り当てます場合、は、1 つの書き込み可能な変数、プロパティ、または配列要素で式を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="74af3-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="74af3-117">ステートメントが値型 (通常は構造体) を通じて間接的にアクセスする場合、値の型を保持する変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="74af3-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="74af3-118">適切な構造体 (またはその他の値の型) を変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="74af3-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="74af3-119">値を代入するのにプロパティにアクセスするのにには、変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="74af3-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74af3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="74af3-120">See Also</span></span>  
 [<span data-ttu-id="74af3-121">演算子および式</span><span class="sxs-lookup"><span data-stu-id="74af3-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="74af3-122">ステートメント</span><span class="sxs-lookup"><span data-stu-id="74af3-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="74af3-123">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="74af3-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
