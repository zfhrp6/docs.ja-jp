---
title: Visual Basic のコーディング規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655362"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="ac1fa-102">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="ac1fa-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="ac1fa-103">Microsoft は、ここで示すガイドラインに従ってサンプルおよびドキュメントを開発しています。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="ac1fa-104">同じコーディング規則に従うと、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="ac1fa-105">コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="ac1fa-106">これまでの経験に基づいて推測できるようになるため、コードをすばやく理解できます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="ac1fa-107">コードのコピー、変更、保守がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="ac1fa-108">コードが Visual Basic の "ベスト プラクティス" に従っていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="ac1fa-109">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="ac1fa-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="ac1fa-110">名前付けのガイドラインについては、次を参照してください。[名前付けのガイドライン](../../../standard/design-guidelines/naming-guidelines.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="ac1fa-111">"My" または "my" を変数名の一部として使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="ac1fa-112">`My` オブジェクトとの混同を招くからです。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="ac1fa-113">自動生成されたコードに含まれるオブジェクトの名前をこのガイドラインに合わせて変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="ac1fa-114">レイアウト規則</span><span class="sxs-lookup"><span data-stu-id="ac1fa-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="ac1fa-115">タブを空白として挿入し、4 文字インデントによるスマート インデントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="ac1fa-116">使用して**かなりコードのフォーマット の一覧表示する**コード エディターでコードを書式設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="ac1fa-117">詳細については、次を参照してください。[オプション、[テキスト エディター]、基本 (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="ac1fa-118">1 つの行には 1 つのステートメントのみを記述します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-118">Use only one statement per line.</span></span> <span data-ttu-id="ac1fa-119">Visual Basic の行区切り記号 (:) は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="ac1fa-120">言語で許可される場所では、明示的な行継続文字 "_" ではなく暗黙的な行継続を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="ac1fa-121">1 つの行には 1 つの宣言のみを記述します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="ac1fa-122">場合**かなりコードのフォーマット の一覧表示する**しない形式継続行に自動的に、手動でインデント継続行 1 タブ ストップ。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="ac1fa-123">ただし、リストの項目は常に左揃えにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="ac1fa-124">メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="ac1fa-125">コメント規則</span><span class="sxs-lookup"><span data-stu-id="ac1fa-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="ac1fa-126">コメントは、コード行の末尾ではなく別の行に記述します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="ac1fa-127">英語でコメントを記述する場合、コメント テキストの始まりには英大文字を使用し、終わりにはピリオドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="ac1fa-128">コメント デリミター (') とコメント テキストの間に空白を 1 つ挿入します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="ac1fa-129">アスタリスク (\*) を整形したブロックでコメントを囲まないようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="ac1fa-130">プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="ac1fa-130">Program Structure</span></span>  
  
-   <span data-ttu-id="ac1fa-131">`Main` メソッドを使用するときには、新しいコンソール アプリケーションの既定の構造を使用し、コマンド ライン引数には `My` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="ac1fa-132">言語ガイドライン</span><span class="sxs-lookup"><span data-stu-id="ac1fa-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="ac1fa-133">文字列型 (String)</span><span class="sxs-lookup"><span data-stu-id="ac1fa-133">String Data Type</span></span>  
  
-   <span data-ttu-id="ac1fa-134">文字列を連結するには、アンパサンド (&) を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="ac1fa-135">ループ内での文字列の追加には <xref:System.Text.StringBuilder> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="ac1fa-136">イベント ハンドラー内の厳密でないデリゲート</span><span class="sxs-lookup"><span data-stu-id="ac1fa-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="ac1fa-137">イベント ハンドラーの引数 (Object および EventArgs) は明示的に修飾しません。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="ac1fa-138">イベントに渡されるイベント引数 (sender as Object、e as EventArgs など) を使用しない場合は、厳密でないデリゲートを使用して、コードでイベント引数を省略します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="ac1fa-139">Unsigned データ型</span><span class="sxs-lookup"><span data-stu-id="ac1fa-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="ac1fa-140">特に必要でない限り、unsigned 型ではなく `Integer` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="ac1fa-141">配列</span><span class="sxs-lookup"><span data-stu-id="ac1fa-141">Arrays</span></span>  
  
-   <span data-ttu-id="ac1fa-142">宣言行で配列を初期化するときは短い構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="ac1fa-143">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="ac1fa-144">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="ac1fa-145">配列指定子は、変数ではなく型に指定します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="ac1fa-146">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="ac1fa-147">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="ac1fa-148">基本データ型の配列の宣言と初期化では、{ } 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="ac1fa-149">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="ac1fa-150">次のような構文は使用しません。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="ac1fa-151">With キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="ac1fa-151">Use the With Keyword</span></span>  
 <span data-ttu-id="ac1fa-152">同じオブジェクトの呼び出しを複数回使用する場合には、`With` キーワードの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="ac1fa-153">例外処理を使用する場合の Try...Catch/Using ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="ac1fa-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="ac1fa-154">`On Error Goto` は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="ac1fa-155">IsNot キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="ac1fa-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="ac1fa-156">`Not...Is Nothing` の代わりに `IsNot` キーワードを使用します。 </span><span class="sxs-lookup"><span data-stu-id="ac1fa-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="ac1fa-157">New キーワード</span><span class="sxs-lookup"><span data-stu-id="ac1fa-157">New Keyword</span></span>  
  
-   <span data-ttu-id="ac1fa-158">短い形式のインスタンス化を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-158">Use short instantiation.</span></span> <span data-ttu-id="ac1fa-159">たとえば、次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="ac1fa-160">この行は次の行と同じ結果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="ac1fa-161">新しいオブジェクトには、パラメーターなしのコンストラクターの代わりにオブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="ac1fa-162">イベント処理</span><span class="sxs-lookup"><span data-stu-id="ac1fa-162">Event Handling</span></span>  
  
-   <span data-ttu-id="ac1fa-163">`AddHandler` ではなく `Handles` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="ac1fa-164">`AddressOf` を使用し、デリゲートの明示的なインスタンス化は避けます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="ac1fa-165">イベントを定義するときには、短い構文を使用し、デリゲートの定義はコンパイラに任せます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="ac1fa-166">`Nothing` メソッドを呼び出す前にイベントが `RaiseEvent` (null) かどうか確認しないようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="ac1fa-167">`RaiseEvent` は、イベントを発生させる前に `Nothing` かどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="ac1fa-168">共有メンバーの使用</span><span class="sxs-lookup"><span data-stu-id="ac1fa-168">Using Shared Members</span></span>  
 <span data-ttu-id="ac1fa-169">`Shared` メンバーの呼び出しにはクラス名を使用し、インスタンス変数からは行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="ac1fa-170">XML リテラルの使用</span><span class="sxs-lookup"><span data-stu-id="ac1fa-170">Use XML Literals</span></span>  
 <span data-ttu-id="ac1fa-171">XML リテラルを使用すると、XML 操作時に行う最も一般的なタスク (読み込み、クエリ、変換など) を簡素化できます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="ac1fa-172">XML を使用して開発を行う場合は、次のガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="ac1fa-173">XML API を直接呼び出す代わりに XML リテラルを使用して XML ドキュメントおよびフラグメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="ac1fa-174">ファイル レベルまたはプロジェクト レベルで XML 名前空間をインポートし、XML リテラルによるパフォーマンスの最適化を利用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="ac1fa-175">XML 軸プロパティを使用して XML ドキュメント内の要素と属性にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="ac1fa-176">`Add` メソッドなどの API 呼び出しを使用する代わりに、埋め込み式を使用して既存の値から値を組み込んで XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="ac1fa-177">LINQ クエリ</span><span class="sxs-lookup"><span data-stu-id="ac1fa-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="ac1fa-178">クエリ変数にはわかりやすい名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="ac1fa-179">クエリ内で要素の名前を指定して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="ac1fa-180">結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="ac1fa-181">たとえば、クエリが顧客名と注文 ID を返す場合、それらの名前を結果の `Name` と `ID` のままにはせずに変更します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="ac1fa-182">クエリ変数と範囲変数の宣言で型の推論を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="ac1fa-183">各クエリ句を `From` ステートメントの下に揃えます。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="ac1fa-184">`Where` 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="ac1fa-185">`Join` 句を使用して暗黙的に結合操作を定義する代わりに、`Where` 句を使用して明示的に結合操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac1fa-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac1fa-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac1fa-186">See Also</span></span>  
 [<span data-ttu-id="ac1fa-187">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ac1fa-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
