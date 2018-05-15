---
title: '方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b05d9f910e8c268fded8cdcc462392a1e80efdb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="0651f-102">方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0651f-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="0651f-103">拡張メソッドを使用して、特定の列挙型に固有の機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0651f-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0651f-104">例</span><span class="sxs-lookup"><span data-stu-id="0651f-104">Example</span></span>  
 <span data-ttu-id="0651f-105">次の例では、`Grades` 列挙型は学生が授業で受け取る成績評価を表わしています。</span><span class="sxs-lookup"><span data-stu-id="0651f-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="0651f-106">`Passing` という名前の拡張機能メソッドが `Grades` 型に追加されていて、この型の各インスタンスが合格点を表しているかどうかを自ら "認識" できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="0651f-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="0651f-107">`Extensions` クラスには動的に更新される静的変数も含まれていて、拡張メソッドの戻り値はその変数の現在の値を反映していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0651f-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="0651f-108">背後では、拡張メソッドが自分が定義されている静的クラスに直接呼び出されることを、この例は示しています。</span><span class="sxs-lookup"><span data-stu-id="0651f-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0651f-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0651f-109">Compiling the Code</span></span>  
 <span data-ttu-id="0651f-110">このコードを実行するには、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに、そのコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0651f-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="0651f-111">既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のバージョン 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0651f-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="0651f-112">これらの要件のうち、1 つ以上がプロジェクトから欠落している場合、手動で追加できます。</span><span class="sxs-lookup"><span data-stu-id="0651f-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0651f-113">参照</span><span class="sxs-lookup"><span data-stu-id="0651f-113">See Also</span></span>  
 [<span data-ttu-id="0651f-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0651f-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0651f-115">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="0651f-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
