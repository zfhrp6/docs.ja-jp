---
title: "遅延実行の例 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 04839f4f729158406c3107f2dcdfbff74753c29c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="beb80-102">遅延実行の例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="beb80-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="beb80-103">このトピックでは、遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="beb80-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beb80-104">例</span><span class="sxs-lookup"><span data-stu-id="beb80-104">Example</span></span>  
 <span data-ttu-id="beb80-105">遅延実行を利用する拡張メソッドの使用時における実行順序の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="beb80-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="beb80-106">この例では、3 つの文字列の配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="beb80-106">The example declares an array of three strings.</span></span> <span data-ttu-id="beb80-107">次に、`ConvertCollectionToUpperCase` によって返されるコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="beb80-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="beb80-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="beb80-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="beb80-109">`ConvertCollectionToUpperCase` によって返されるコレクションの反復処理時、各アイテムはソース文字列の配列から取得され、次のアイテムがソース文字列の配列から取得される前に大文字に変換されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="beb80-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="beb80-110">返されるコレクションの各アイテムが `foreach` の `Main` ループで処理されるまで、文字列の配列全体は大文字に変換されないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="beb80-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb80-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="beb80-111">See Also</span></span>  
 [<span data-ttu-id="beb80-112">チュートリアル: 遅延実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="beb80-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
