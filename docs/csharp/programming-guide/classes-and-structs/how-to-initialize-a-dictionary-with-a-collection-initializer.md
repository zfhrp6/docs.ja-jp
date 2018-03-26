---
title: '方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="b7e0d-102">方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b7e0d-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="b7e0d-103"><xref:System.Collections.Generic.Dictionary`2> にはキーと値のペアのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs.</span></span> <span data-ttu-id="b7e0d-104">その <xref:System.Collections.Generic.Dictionary`2.Add*> メソッドは、それぞれキーと値に対する 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-104">Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="b7e0d-105">`Add` メソッドが複数のパラメーターを受け取る <xref:System.Collections.Generic.Dictionary`2> またはコレクションを初期化するには、次の例に示すように、各パラメーターのセットを中かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-105">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7e0d-106">例</span><span class="sxs-lookup"><span data-stu-id="b7e0d-106">Example</span></span>  
 <span data-ttu-id="b7e0d-107">次のコード例では、<xref:System.Collections.Generic.Dictionary`2> が型 `StudentName` のインスタンスで初期化されています。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-107">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="b7e0d-108">コレクションの各要素の中かっこの 2 つのペアに注目してください。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="b7e0d-109">最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students`<xref:System.Collections.Generic.Dictionary`2> に追加されるキーと値のペアの初期化子を囲んでいます。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="b7e0d-110">最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7e0d-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b7e0d-111">Compiling the Code</span></span>  
 <span data-ttu-id="b7e0d-112">このコードを実行するには、クラスをコピーし、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="b7e0d-113">既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の using ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="b7e0d-114">これらの要件のうち 1 つまたは複数がプロジェクトから欠落している場合は、手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="b7e0d-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e0d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7e0d-115">See Also</span></span>  
 [<span data-ttu-id="b7e0d-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b7e0d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7e0d-117">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="b7e0d-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
