---
title: '方法: 拡張メソッドを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="27cc6-102">方法: 拡張メソッドを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27cc6-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="27cc6-103">拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="27cc6-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="27cc6-104">拡張メソッドが宣言されており、スコープに取り込む後、は、拡張する型のインスタンス メソッドと同様に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="27cc6-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="27cc6-105">拡張メソッドを作成する方法の詳細については、次を参照してください。[する方法: 拡張メソッドを記述](./how-to-write-an-extension-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="27cc6-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="27cc6-106">次の手順は、拡張メソッドを参照してください`PrintAndPunctuate`、2 番目のパラメーターを渡して、文字列を呼び出すインスタンス、どのような値を続けて表示される`punc`です。</span><span class="sxs-lookup"><span data-stu-id="27cc6-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="27cc6-107">メソッドが呼び出されるとスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="27cc6-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="27cc6-108">拡張メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="27cc6-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="27cc6-109">拡張メソッドの最初のパラメーターのデータ型を持つ変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="27cc6-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="27cc6-110">`PrintAndPunctuate`、する必要があります、<xref:System.String>変数。</span><span class="sxs-lookup"><span data-stu-id="27cc6-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="27cc6-111">変数が、拡張メソッドを呼び出し、その値が最初のパラメーターにバインドされている`aString`です。</span><span class="sxs-lookup"><span data-stu-id="27cc6-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="27cc6-112">次のステートメントの呼び出しが表示されます`Ready?`です。</span><span class="sxs-lookup"><span data-stu-id="27cc6-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="27cc6-113">この拡張メソッドの呼び出しは単に検索する通知などのいずれかを呼び出し、<xref:System.String>インスタンス メソッドを 1 つのパラメーターを必要とします。</span><span class="sxs-lookup"><span data-stu-id="27cc6-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="27cc6-114">別の文字列変数を宣言し、任意の文字列での動作を確認するには、もう一度メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="27cc6-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="27cc6-115">この時間は、結果:`or not!!!`です。</span><span class="sxs-lookup"><span data-stu-id="27cc6-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27cc6-116">例</span><span class="sxs-lookup"><span data-stu-id="27cc6-116">Example</span></span>  
 <span data-ttu-id="27cc6-117">次のコード作成の完全な例、単純な拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="27cc6-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a><span data-ttu-id="27cc6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="27cc6-118">See Also</span></span>  
 [<span data-ttu-id="27cc6-119">方法 : 拡張メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="27cc6-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="27cc6-120">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="27cc6-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="27cc6-121">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="27cc6-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
