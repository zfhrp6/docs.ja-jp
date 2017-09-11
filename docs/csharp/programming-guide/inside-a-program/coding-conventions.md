---
title: "C# のコーディング規則 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
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
ms.openlocfilehash: 9f32fdc0eb1954cdac30c39e05c74d43301d850c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="1738a-102">C# のコーディング規則 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1738a-102">C# Coding Conventions (C# Programming Guide)</span></span>
<span data-ttu-id="1738a-103">[C# 言語仕様](http://go.microsoft.com/fwlink/?LinkId=199552)では、コーディング標準は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="1738a-103">The [C# Language Specification](http://go.microsoft.com/fwlink/?LinkId=199552) does not define a coding standard.</span></span> <span data-ttu-id="1738a-104">ただし、このトピックのガイドラインは、サンプルおよびドキュメントを開発するためにマイクロソフトによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="1738a-104">However, the guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
 <span data-ttu-id="1738a-105">コーディング規則には、次の目的があります。</span><span class="sxs-lookup"><span data-stu-id="1738a-105">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="1738a-106">コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。</span><span class="sxs-lookup"><span data-stu-id="1738a-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="1738a-107">これにより、経験に基づいて推測することで、コードをより迅速に理解することができます。</span><span class="sxs-lookup"><span data-stu-id="1738a-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="1738a-108">コードのコピー、変更、および保守が容易になります。</span><span class="sxs-lookup"><span data-stu-id="1738a-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="1738a-109">コーディング規約により、C# のベスト プラクティスがわかります。</span><span class="sxs-lookup"><span data-stu-id="1738a-109">They demonstrate C# best practices.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="1738a-110">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="1738a-110">Naming Conventions</span></span>  
  
-   <span data-ttu-id="1738a-111">[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)が含まれていない簡単な例では、名前空間の修飾を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-111">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="1738a-112">プロジェクトに名前空間が既定でインポートされていることがわかっている場合は、その名前空間の各名前を完全修飾する必要はありません。 </span><span class="sxs-lookup"><span data-stu-id="1738a-112">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="1738a-113">次の例に示すように、修飾名が長すぎて 1 行に収まらない場合は、ドット (.) の後で改行できます。</span><span class="sxs-lookup"><span data-stu-id="1738a-113">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     <span data-ttu-id="1738a-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-115">他のガイドラインに合わせて、Visual Studio デザイナーのツールを使用して作成されたオブジェクトの名前を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1738a-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="1738a-116">レイアウト規則</span><span class="sxs-lookup"><span data-stu-id="1738a-116">Layout Conventions</span></span>  
 <span data-ttu-id="1738a-117">コードの構造を強調する書式が使用され、コードが読みやすくなっているのが、優れたレイアウトです。</span><span class="sxs-lookup"><span data-stu-id="1738a-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="1738a-118">マイクロソフトの例とサンプルは、次の規則に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="1738a-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="1738a-119">コード エディターの既定の設定 (スマート インデント、4 文字インデント、タブを空白として保存) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="1738a-120">詳細については、「[[オプション]、[テキスト エディター]、[C#]、[書式設定]](/visualstudio/ide/reference/options-text-editor-csharp-formatting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1738a-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="1738a-121">1 つの行には 1 つのステートメントのみを記述します。</span><span class="sxs-lookup"><span data-stu-id="1738a-121">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="1738a-122">1 つの行には 1 つの宣言のみを記述します。</span><span class="sxs-lookup"><span data-stu-id="1738a-122">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="1738a-123">継続行にインデントが自動的に設定されない場合は、1 タブ ストップ (4 つの空白) 分のインデントを設定します。</span><span class="sxs-lookup"><span data-stu-id="1738a-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="1738a-124">メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。</span><span class="sxs-lookup"><span data-stu-id="1738a-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="1738a-125">次のコードに示すように、式に句を作成するときはかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     <span data-ttu-id="1738a-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="1738a-127">コメント規則</span><span class="sxs-lookup"><span data-stu-id="1738a-127">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="1738a-128">コメントは、コード行の末尾ではなく別の行に記述します。</span><span class="sxs-lookup"><span data-stu-id="1738a-128">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="1738a-129">コメントのテキストは大文字で開始します。</span><span class="sxs-lookup"><span data-stu-id="1738a-129">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="1738a-130">コメントのテキストはピリオドで終了します。</span><span class="sxs-lookup"><span data-stu-id="1738a-130">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="1738a-131">次の例に示すように、コメント デリミター (//) とコメント テキストの間に空白を 1 つ挿入します。</span><span class="sxs-lookup"><span data-stu-id="1738a-131">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     <span data-ttu-id="1738a-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-133">アスタリスクを整形したブロックでコメントを囲まないようにします。</span><span class="sxs-lookup"><span data-stu-id="1738a-133">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="1738a-134">言語ガイドライン</span><span class="sxs-lookup"><span data-stu-id="1738a-134">Language Guidelines</span></span>  
 <span data-ttu-id="1738a-135">以降のセクションでは、コード例とサンプルを準備する際に C# チームが従っている方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1738a-135">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="1738a-136">文字列型 (String)</span><span class="sxs-lookup"><span data-stu-id="1738a-136">String Data Type</span></span>  
  
-   <span data-ttu-id="1738a-137">次のコードに示すように、短い文字列を連結するときは `+` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-137">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     <span data-ttu-id="1738a-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-139">ループ内で文字列を追加する場合 (特に大量のテキストを処理する場合) は、<xref:System.Text.StringBuilder> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-139">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="1738a-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span></span>  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="1738a-141">暗黙的に型指定されるローカル変数</span><span class="sxs-lookup"><span data-stu-id="1738a-141">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="1738a-142">変数の型が割り当ての右側から明らかである場合、または厳密な型が重要でない場合は、ローカル変数の[暗黙の型指定](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-142">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     <span data-ttu-id="1738a-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-144">割り当ての右側から型が明らかではない場合、[var](../../../csharp/language-reference/keywords/var.md) を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1738a-144">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     <span data-ttu-id="1738a-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-146">変数の型を指定するときに変数名に頼らないでください。</span><span class="sxs-lookup"><span data-stu-id="1738a-146">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="1738a-147">変数名が正しくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1738a-147">It might not be correct.</span></span>  
  
     <span data-ttu-id="1738a-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-149">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) の代わりに `var` を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1738a-149">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="1738a-150">[for](../../../csharp/language-reference/keywords/for.md) ループおよび [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループでループ変数の型を決定するときは、暗黙の型指定を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-150">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="1738a-151">次の例では、`for` ステートメントで暗黙の型指定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1738a-151">The following example uses implicit typing in a `for` statement.</span></span>  
  
     <span data-ttu-id="1738a-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span></span>  
  
     <span data-ttu-id="1738a-153">次の例では、`foreach` ステートメントで暗黙の型指定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1738a-153">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     <span data-ttu-id="1738a-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="1738a-155">Unsigned データ型</span><span class="sxs-lookup"><span data-stu-id="1738a-155">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="1738a-156">通常は、unsigned 型ではなく `int` を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="1738a-157">C# では `int` を使用するのが一般的です。`int` を使用すると、他のライブラリと対話しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1738a-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="1738a-158">配列</span><span class="sxs-lookup"><span data-stu-id="1738a-158">Arrays</span></span>  
  
-   <span data-ttu-id="1738a-159">宣言行で配列を初期化するときは簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     <span data-ttu-id="1738a-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span></span>  
  
### <a name="delegates"></a><span data-ttu-id="1738a-161">デリゲート</span><span class="sxs-lookup"><span data-stu-id="1738a-161">Delegates</span></span>  
  
-   <span data-ttu-id="1738a-162">デリゲート型のインスタンスを作成するときは簡潔な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-162">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     <span data-ttu-id="1738a-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span></span>  
  
     <span data-ttu-id="1738a-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span></span>  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="1738a-165">例外処理における try-catch ステートメントと using ステートメント</span><span class="sxs-lookup"><span data-stu-id="1738a-165">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="1738a-166">ほとんどの例外処理には、[try-catch](../../../csharp/language-reference/keywords/try-catch.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-166">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     <span data-ttu-id="1738a-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-168">C# の [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)を使用して、コードを簡潔にします。</span><span class="sxs-lookup"><span data-stu-id="1738a-168">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="1738a-169">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) ステートメントを使用するときに `finally` ブロックのコードが <xref:System.IDisposable.Dispose%2A> メソッドの呼び出しだけである場合は、`using` ステートメントを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-169">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     <span data-ttu-id="1738a-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span></span>  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="1738a-171">&& 演算子および &#124;&#124; 演算子</span><span class="sxs-lookup"><span data-stu-id="1738a-171">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="1738a-172">例外を回避し、不要な比較をスキップしてパフォーマンスを向上させるには、比較を実行する場合、次の例に示すように [&](../../../csharp/language-reference/operators/and-operator.md) の代わりに [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) を、[&#124;](../../../csharp/language-reference/operators/or-operator.md) の代わりに [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-172">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     <span data-ttu-id="1738a-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span></span>  
  
### <a name="new-operator"></a><span data-ttu-id="1738a-174">new 演算子</span><span class="sxs-lookup"><span data-stu-id="1738a-174">New Operator</span></span>  
  
-   <span data-ttu-id="1738a-175">次の宣言に示すように、暗黙の型指定を使用してオブジェクトのインスタンス化を簡潔な形式にします。</span><span class="sxs-lookup"><span data-stu-id="1738a-175">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     <span data-ttu-id="1738a-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span></span>  
  
     <span data-ttu-id="1738a-177">前の行は次の宣言に相当します。</span><span class="sxs-lookup"><span data-stu-id="1738a-177">The previous line is equivalent to the following declaration.</span></span>  
  
     <span data-ttu-id="1738a-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-179">オブジェクト初期化子を使用してオブジェクトの作成を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="1738a-179">Use object initializers to simplify object creation.</span></span>  
  
     <span data-ttu-id="1738a-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="1738a-181">イベント処理</span><span class="sxs-lookup"><span data-stu-id="1738a-181">Event Handling</span></span>  
  
-   <span data-ttu-id="1738a-182">後で削除する必要のないイベント ハンドラーを定義する場合は、ラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-182">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     <span data-ttu-id="1738a-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span></span>  
  
     <span data-ttu-id="1738a-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span></span>  
  
### <a name="static-members"></a><span data-ttu-id="1738a-185">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="1738a-185">Static Members</span></span>  
  
-   <span data-ttu-id="1738a-186">[静的](../../../csharp/language-reference/keywords/static.md)メンバーは、クラス名 (*ClassName.StaticMember*) を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1738a-186">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="1738a-187">こうすることで、静的アクセスが明確になり、コードがよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1738a-187">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="1738a-188">派生クラスの名前を持つ基本クラスに定義された静的メンバーを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="1738a-188">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="1738a-189">このコードをコンパイルすると、コードが読みやすくなくなり、派生クラスに同じ名前の静的メンバーを追加すると、将来的にコードが中断する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1738a-189">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="1738a-190">LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="1738a-190">LINQ Queries</span></span>  
  
-   <span data-ttu-id="1738a-191">クエリ変数にはわかりやすい名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-191">Use meaningful names for query variables.</span></span> <span data-ttu-id="1738a-192">次の例では、シアトル在住の顧客に `seattleCustomers` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1738a-192">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     <span data-ttu-id="1738a-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-194">エイリアスを使用して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。</span><span class="sxs-lookup"><span data-stu-id="1738a-194">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     <span data-ttu-id="1738a-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-196">結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="1738a-196">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="1738a-197">たとえば、クエリで顧客名と販売店 ID を返す場合、クエリ結果で `Name` と `ID` をそのまま使用するのではなく、これらの名前を変更し、`Name` が顧客の名前であり、`ID` が販売店の ID であることを明確にします。</span><span class="sxs-lookup"><span data-stu-id="1738a-197">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     <span data-ttu-id="1738a-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-199">クエリ変数と範囲変数の宣言で暗黙の型指定を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-199">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     <span data-ttu-id="1738a-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-201">前の例に示すように、クエリ句を [from](../../../csharp/language-reference/keywords/from-clause.md) 句の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="1738a-201">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="1738a-202">[where](../../../csharp/language-reference/keywords/where-clause.md) 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1738a-202">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     <span data-ttu-id="1738a-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span></span>  
  
-   <span data-ttu-id="1738a-204">内部コレクションにアクセスするには、[join](../../../csharp/language-reference/keywords/join-clause.md) 句ではなく複数の `from` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="1738a-204">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="1738a-205">たとえば、`Student` オブジェクトのコレクションがあり、各オブジェクトに試験の点数のコレクションが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="1738a-205">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="1738a-206">次のクエリを実行すると、90 点より高い点数とその点数を取った学生の姓が返されます。</span><span class="sxs-lookup"><span data-stu-id="1738a-206">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     <span data-ttu-id="1738a-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span><span class="sxs-lookup"><span data-stu-id="1738a-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="1738a-208">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1738a-208">Security</span></span>  
 <span data-ttu-id="1738a-209">「[安全なコーディングのガイドライン](../../../standard/security/secure-coding-guidelines.md)」のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="1738a-209">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1738a-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="1738a-210">See Also</span></span>  
 <span data-ttu-id="1738a-211">[Visual Basic のコーディング規則](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="1738a-211">[Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span></span>  
 [<span data-ttu-id="1738a-212">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1738a-212">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)

