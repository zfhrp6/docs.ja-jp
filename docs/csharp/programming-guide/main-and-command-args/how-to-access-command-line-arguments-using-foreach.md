---
title: '方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 2f1723efd4056539e12605bc1a4229f94bc9e055
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332508"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="17f55-102">方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="17f55-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="17f55-103">配列の反復処理には、この例で示すように [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="17f55-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="17f55-104">`foreach` ステートメントは、配列、.NET Framework コレクション クラス、または <xref:System.Collections.IEnumerable> インターフェイスを実装する任意のクラスや構造体の反復処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="17f55-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17f55-105">Visual Studio でアプリケーションを実行する場合、「[[デバッグ] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/debug-page-project-designer)」のコマンド ライン引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="17f55-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f55-106">例</span><span class="sxs-lookup"><span data-stu-id="17f55-106">Example</span></span>  
 <span data-ttu-id="17f55-107">この例では、`foreach` を使用したコマンド ライン引数の出力方法を示します。</span><span class="sxs-lookup"><span data-stu-id="17f55-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="17f55-108">参照</span><span class="sxs-lookup"><span data-stu-id="17f55-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="17f55-109">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="17f55-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="17f55-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="17f55-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="17f55-111">foreach、in</span><span class="sxs-lookup"><span data-stu-id="17f55-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="17f55-112">Main() とコマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="17f55-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="17f55-113">方法: コマンド ライン引数を表示する</span><span class="sxs-lookup"><span data-stu-id="17f55-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="17f55-114">Main() の戻り値</span><span class="sxs-lookup"><span data-stu-id="17f55-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
