---
title: "方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
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
ms.openlocfilehash: 22feed835b8a868cca2839467a8e5cc7118db39a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="619e5-102">方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="619e5-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="619e5-103">拡張メソッドを使用して、特定の列挙型に固有の機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="619e5-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="619e5-104">例</span><span class="sxs-lookup"><span data-stu-id="619e5-104">Example</span></span>  
 <span data-ttu-id="619e5-105">次の例では、`Grades` 列挙型は学生が授業で受け取る成績評価を表わしています。</span><span class="sxs-lookup"><span data-stu-id="619e5-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="619e5-106">`Passing` という名前の拡張機能メソッドが `Grades` 型に追加されていて、この型の各インスタンスが合格点を表しているかどうかを自ら "認識" できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="619e5-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 <span data-ttu-id="619e5-107">[!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="619e5-107">[!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]</span></span>  
  
 <span data-ttu-id="619e5-108">`Extensions` クラスには動的に更新される静的変数も含まれていて、拡張メソッドの戻り値はその変数の現在の値を反映していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="619e5-108">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="619e5-109">背後では、拡張メソッドが自分が定義されている静的クラスに直接呼び出されることを、この例は示しています。</span><span class="sxs-lookup"><span data-stu-id="619e5-109">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="619e5-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="619e5-110">Compiling the Code</span></span>  
 <span data-ttu-id="619e5-111">このコードを実行するには、[!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに、そのコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="619e5-111">To run this code, copy and paste it into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="619e5-112">既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="619e5-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="619e5-113">これらの要件のうち、1 つ以上がプロジェクトから欠落している場合、手動で追加できます。</span><span class="sxs-lookup"><span data-stu-id="619e5-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="619e5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="619e5-114">See Also</span></span>  
 <span data-ttu-id="619e5-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="619e5-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="619e5-116">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="619e5-116">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

