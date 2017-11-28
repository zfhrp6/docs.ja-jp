---
title: "方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="994d4-102">方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="994d4-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="994d4-103"><xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> メソッドは、キー用と値用の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="994d4-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="994d4-104">複数のパラメーターを受け取る <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` メソッドを初期化するには、次の例に示すように、各パラメーターのセットを中かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="994d4-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="994d4-105">例</span><span class="sxs-lookup"><span data-stu-id="994d4-105">Example</span></span>  
 <span data-ttu-id="994d4-106">次のコード例では、<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`。</span><span class="sxs-lookup"><span data-stu-id="994d4-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="994d4-107">コレクションの各要素の中かっこの 2 つのペアに注目してください。</span><span class="sxs-lookup"><span data-stu-id="994d4-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="994d4-108">最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students`<xref:System.Collections.Generic.Dictionary\`2> に追加されるキーと値のペアの初期化子を囲んでいます。</span><span class="sxs-lookup"><span data-stu-id="994d4-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="994d4-109">最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="994d4-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="994d4-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="994d4-110">Compiling the Code</span></span>  
 <span data-ttu-id="994d4-111">このコードを実行するには、クラスをコピーし、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="994d4-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="994d4-112">既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の using ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="994d4-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="994d4-113">これらの要件のうち 1 つまたは複数がプロジェクトから欠落している場合は、手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="994d4-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994d4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="994d4-114">See Also</span></span>  
 [<span data-ttu-id="994d4-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="994d4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="994d4-116">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="994d4-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
