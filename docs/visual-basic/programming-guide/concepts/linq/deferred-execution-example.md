---
title: 遅延実行の例 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="7db96-102">遅延実行の例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db96-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="7db96-103">このトピックでは、遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7db96-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7db96-104">例</span><span class="sxs-lookup"><span data-stu-id="7db96-104">Example</span></span>  
 <span data-ttu-id="7db96-105">遅延実行を利用する拡張メソッドの使用時における実行順序の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7db96-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="7db96-106">この例では、3 つの文字列の配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="7db96-106">The example declares an array of three strings.</span></span> <span data-ttu-id="7db96-107">次に、`ConvertCollectionToUpperCase` によって返されるコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="7db96-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="7db96-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7db96-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="7db96-109">`ConvertCollectionToUpperCase` によって返されるコレクションの反復処理時、各アイテムはソース文字列の配列から取得され、次のアイテムがソース文字列の配列から取得される前に大文字に変換されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7db96-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="7db96-110">返されるコレクションの各アイテムが `foreach` の `Main` ループで処理されるまで、文字列の配列全体は大文字に変換されないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7db96-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db96-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7db96-111">See Also</span></span>  
 [<span data-ttu-id="7db96-112">チュートリアル: 遅延実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7db96-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
