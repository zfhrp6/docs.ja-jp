---
title: "方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
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
ms.openlocfilehash: 766b5cd0879edec1dc409e07c4f62ee693fd615d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="f9725-102">方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f9725-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="f9725-103">配列の反復処理には、この例で示すように [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="f9725-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="f9725-104">`foreach` ステートメントは、配列、.NET Framework コレクション クラス、または <xref:System.Collections.IEnumerable> インターフェイスを実装する任意のクラスや構造体の反復処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9725-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9725-105">Visual Studio でアプリケーションを実行する場合、「[[デバッグ] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/debug-page-project-designer)」のコマンド ライン引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f9725-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9725-106">例</span><span class="sxs-lookup"><span data-stu-id="f9725-106">Example</span></span>  
 <span data-ttu-id="f9725-107">この例では、`foreach` を使用したコマンド ライン引数の出力方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9725-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 <span data-ttu-id="f9725-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9725-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span></span>  
  
 <span data-ttu-id="f9725-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9725-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9725-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9725-110">See Also</span></span>  
 <span data-ttu-id="f9725-111"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="f9725-111"><xref:System.Array></span></span>   
 <span data-ttu-id="f9725-112"><xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="f9725-112"><xref:System.Collections></span></span>   
 <span data-ttu-id="f9725-113">[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="f9725-113">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="f9725-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9725-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f9725-115">[foreach、in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="f9725-115">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 <span data-ttu-id="f9725-116">[Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9725-116">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="f9725-117">[方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="f9725-117">[How to: Display Command Line Arguments](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span></span>  
 [<span data-ttu-id="f9725-118">Main() の戻り値</span><span class="sxs-lookup"><span data-stu-id="f9725-118">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

