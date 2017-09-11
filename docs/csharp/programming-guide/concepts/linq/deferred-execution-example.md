---
title: "遅延実行の例 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fdbe45ceda1c7c1d82664bcf3b84b79b4fd85511
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="b7ea2-102">遅延実行の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7ea2-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="b7ea2-103">このトピックでは、遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7ea2-104">例</span><span class="sxs-lookup"><span data-stu-id="b7ea2-104">Example</span></span>  
 <span data-ttu-id="b7ea2-105">遅延実行を利用する拡張メソッドの使用時における実行順序の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="b7ea2-106">この例では、3 つの文字列の配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-106">The example declares an array of three strings.</span></span> <span data-ttu-id="b7ea2-107">次に、`ConvertCollectionToUpperCase` によって返されるコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="b7ea2-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="b7ea2-109">`ConvertCollectionToUpperCase` によって返されるコレクションの反復処理時、各アイテムはソース文字列の配列から取得され、次のアイテムがソース文字列の配列から取得される前に大文字に変換されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="b7ea2-110">返されるコレクションの各アイテムが `foreach` の `Main` ループで処理されるまで、文字列の配列全体は大文字に変換されないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="b7ea2-111">このチュートリアルの次のトピックでは、クエリの連結について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7ea2-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
-   [<span data-ttu-id="b7ea2-112">クエリの連結の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7ea2-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7ea2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7ea2-113">See Also</span></span>  
 [<span data-ttu-id="b7ea2-114">チュートリアル: クエリの連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7ea2-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)

