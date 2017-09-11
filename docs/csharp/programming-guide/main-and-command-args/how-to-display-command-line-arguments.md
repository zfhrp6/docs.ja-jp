---
title: "方法: コマンド ライン引数を表示する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
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
ms.openlocfilehash: cf8a57cce252b3596f0a19c9df643427615467c6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="d94c1-102">方法: コマンド ライン引数を表示する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d94c1-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="d94c1-103">実行可能ファイルに対してコマンド ラインで指定した引数には、省略可能なパラメーターを介して `Main` からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d94c1-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="d94c1-104">引数は、文字列の配列の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="d94c1-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="d94c1-105">配列の各要素には、1 つの引数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d94c1-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="d94c1-106">引数間の空白は削除されます。</span><span class="sxs-lookup"><span data-stu-id="d94c1-106">White-space between arguments is removed.</span></span> <span data-ttu-id="d94c1-107">たとえば、架空の実行可能ファイルを呼び出すためのコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d94c1-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="d94c1-108">コマンドラインでの入力</span><span class="sxs-lookup"><span data-stu-id="d94c1-108">Input on Command-line</span></span>|<span data-ttu-id="d94c1-109">Main に渡される文字列の配列</span><span class="sxs-lookup"><span data-stu-id="d94c1-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="d94c1-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="d94c1-110">**executable.exe a b c**</span></span>|<span data-ttu-id="d94c1-111">"a"</span><span class="sxs-lookup"><span data-stu-id="d94c1-111">"a"</span></span><br /><br /> <span data-ttu-id="d94c1-112">"b"</span><span class="sxs-lookup"><span data-stu-id="d94c1-112">"b"</span></span><br /><br /> <span data-ttu-id="d94c1-113">"c"</span><span class="sxs-lookup"><span data-stu-id="d94c1-113">"c"</span></span>|  
|<span data-ttu-id="d94c1-114">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="d94c1-114">**executable.exe one two**</span></span>|<span data-ttu-id="d94c1-115">"one"</span><span class="sxs-lookup"><span data-stu-id="d94c1-115">"one"</span></span><br /><br /> <span data-ttu-id="d94c1-116">"two"</span><span class="sxs-lookup"><span data-stu-id="d94c1-116">"two"</span></span>|  
|<span data-ttu-id="d94c1-117">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="d94c1-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="d94c1-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="d94c1-118">"one two"</span></span><br /><br /> <span data-ttu-id="d94c1-119">"three"</span><span class="sxs-lookup"><span data-stu-id="d94c1-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d94c1-120">Visual Studio でアプリケーションを実行する場合は、[[デバッグ] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/debug-page-project-designer) でコマンド ライン引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d94c1-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d94c1-121">例</span><span class="sxs-lookup"><span data-stu-id="d94c1-121">Example</span></span>  
 <span data-ttu-id="d94c1-122">この例は、コマンド ライン アプリケーションに渡されるコマンド ライン引数を示しています。</span><span class="sxs-lookup"><span data-stu-id="d94c1-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="d94c1-123">次の出力は、上の表の最初のエントリに対するものです。</span><span class="sxs-lookup"><span data-stu-id="d94c1-123">The output shown is for the first entry in the table above.</span></span>  
  
 <span data-ttu-id="d94c1-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d94c1-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d94c1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d94c1-125">See Also</span></span>  
 <span data-ttu-id="d94c1-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d94c1-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d94c1-127">[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="d94c1-127">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="d94c1-128">[Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="d94c1-128">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="d94c1-129">[方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span><span class="sxs-lookup"><span data-stu-id="d94c1-129">[How to: Access Command-Line Arguments Using foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span></span>  
 [<span data-ttu-id="d94c1-130">Main() の戻り値</span><span class="sxs-lookup"><span data-stu-id="d94c1-130">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

