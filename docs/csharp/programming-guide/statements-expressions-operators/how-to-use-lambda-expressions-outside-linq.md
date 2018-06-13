---
title: '方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: a7b7d25adab7ce1fc777b3bdbe581666ab952413
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328956"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="75021-102">方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="75021-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="75021-103">ラムダ式の使用は [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリに限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="75021-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="75021-104">デリゲート値が想定される場面、すなわち匿名メソッドを使用できる場面であれば、どこでもラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="75021-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="75021-105">次の例では、Windows フォームのイベント ハンドラーでラムダ式を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75021-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="75021-106">なお、入力 (<xref:System.Object> と <xref:System.Windows.Forms.MouseEventArgs>) の型はコンパイラによって推論されるため、ラムダ入力パラメーターで明示的に指定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="75021-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75021-107">例</span><span class="sxs-lookup"><span data-stu-id="75021-107">Example</span></span>  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="75021-108">参照</span><span class="sxs-lookup"><span data-stu-id="75021-108">See Also</span></span>  
 [<span data-ttu-id="75021-109">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="75021-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="75021-110">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="75021-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="75021-111">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="75021-111">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
