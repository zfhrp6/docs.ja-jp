---
title: "方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: de6f4f1aeb07d7878d02b4f51e6f42b69d0bdcf5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="61d1c-102">方法 : クエリで要素のプロパティのサブセットを返す (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="61d1c-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="61d1c-103">次の両方の条件に当てはまる場合は、クエリ式に匿名型を使用します。</span><span class="sxs-lookup"><span data-stu-id="61d1c-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="61d1c-104">各ソース要素のプロパティの一部のみを返したい。</span><span class="sxs-lookup"><span data-stu-id="61d1c-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="61d1c-105">クエリを実行したメソッドのスコープ外のクエリ結果を保存する必要がない。</span><span class="sxs-lookup"><span data-stu-id="61d1c-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="61d1c-106">各ソース要素の 1 つのプロパティまたはフィールドのみを返す場合は、`select` 句でドット演算子 (.) を使用します。</span><span class="sxs-lookup"><span data-stu-id="61d1c-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="61d1c-107">たとえば、各 `student` の `ID` のみを返すには、次のように `select` 句を記述します。</span><span class="sxs-lookup"><span data-stu-id="61d1c-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="61d1c-108">例</span><span class="sxs-lookup"><span data-stu-id="61d1c-108">Example</span></span>  
 <span data-ttu-id="61d1c-109">次に、匿名型を使用して、各ソース要素のプロパティのうち、指定した条件に一致するプロパティのみを返す例を示します。</span><span class="sxs-lookup"><span data-stu-id="61d1c-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 <span data-ttu-id="61d1c-110">[!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="61d1c-110">[!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]</span></span>  
  
 <span data-ttu-id="61d1c-111">名前を指定しない場合、匿名型にはプロパティのソース要素名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="61d1c-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="61d1c-112">匿名型のプロパティに新しい名前を付けるには、次のように `select` ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="61d1c-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="61d1c-113">前の例でこの方法を試すには、`Console.WriteLine` ステートメントも次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d1c-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61d1c-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="61d1c-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="61d1c-115">このコードを実行するには、クラスをコピーし、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="61d1c-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="61d1c-116">既定で、このプロジェクトは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] バージョン 3.5 をターゲットにしており、System.Core.dll および System.Linq の `using` ディレクティブの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="61d1c-116">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="61d1c-117">これらの要件のうち 1 つまたは複数を満たしていないプロジェクトの場合は、手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="61d1c-117">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="61d1c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="61d1c-118">See Also</span></span>  
 <span data-ttu-id="61d1c-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="61d1c-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="61d1c-120">[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="61d1c-120">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 [<span data-ttu-id="61d1c-121">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="61d1c-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

