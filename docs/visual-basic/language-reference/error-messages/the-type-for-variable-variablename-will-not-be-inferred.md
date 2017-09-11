---
title: "変数の型 &quot;&lt;variablename&gt;&quot; は、外側のスコープ内のフィールドにバインドされているので、推論できません |。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 0f954fda84c9fd1a4af5315be2329de117e6d169
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="d805e-102">変数の型 '&lt;variablename&gt;' は、外側のスコープ内のフィールドにバインドされているので、推論できません。</span><span class="sxs-lookup"><span data-stu-id="d805e-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="d805e-103">変数の型 '\<variablename >' は、外側のスコープ内のフィールドにバインドされているので、推論できません。</span><span class="sxs-lookup"><span data-stu-id="d805e-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="d805e-104">名前を変更するか '\<variablename >'、または完全修飾名 (:"Me.variablename"や"MyBase.variablename") を使用します。</span><span class="sxs-lookup"><span data-stu-id="d805e-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="d805e-105">コードのループ制御変数は、クラスまたは他の外側のスコープ内のフィールドと同じ名前を持っています。</span><span class="sxs-lookup"><span data-stu-id="d805e-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="d805e-106">制御変数は、`As` 句なしで使用されるため、外側のスコープ内のフィールドにバインドされ、コンパイラがこれに対して新しい変数を作成したり、その型を推論したりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="d805e-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="d805e-107">次の例では、`Index` (`For` ステートメントの制御変数) が、`Index` クラスの `Customer` フィールドにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="d805e-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="d805e-108">コンパイラが制御変数 `Index` に対して新しい変数を作成したり、その型を推論したりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="d805e-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d805e-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="d805e-109">By default, this message is a warning.</span></span> <span data-ttu-id="d805e-110">警告を非表示にする方法または警告をエラーとして処理する方法については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="d805e-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d805e-111">**エラー ID:** BC42110</span><span class="sxs-lookup"><span data-stu-id="d805e-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="d805e-112">この警告に対処するには</span><span class="sxs-lookup"><span data-stu-id="d805e-112">To address this warning</span></span>  
  
-   <span data-ttu-id="d805e-113">ループ制御変数の名前を、クラスのフィールドの名前とは異なる識別子に変更して、この変数をローカルにします。</span><span class="sxs-lookup"><span data-stu-id="d805e-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="d805e-114">変数名の前に `Me.` を付けることにより、クラス フィールドにループ制御変数がバインドされていることを明確にします。</span><span class="sxs-lookup"><span data-stu-id="d805e-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="d805e-115">ローカル型の推定ではなく `As` 句を使用して、ループ制御変数に型を指定します。</span><span class="sxs-lookup"><span data-stu-id="d805e-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="d805e-116">例</span><span class="sxs-lookup"><span data-stu-id="d805e-116">Example</span></span>  
 <span data-ttu-id="d805e-117">次のコードは、上の例に最初の修正を行ったものです。</span><span class="sxs-lookup"><span data-stu-id="d805e-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="d805e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d805e-118">See Also</span></span>  
 <span data-ttu-id="d805e-119">[Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d805e-119">[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="d805e-120"> [各.次のステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d805e-120"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="d805e-121"> [.次のステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d805e-121"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="d805e-122"> [方法: オブジェクトの現在のインスタンスを参照してください](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="d805e-122"> [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="d805e-123"> [ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="d805e-123"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="d805e-124"> [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="d805e-124"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

