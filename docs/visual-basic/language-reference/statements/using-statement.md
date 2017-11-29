---
title: "Using ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed9cc0d04c89eac1fe342a0924dd89bb1e258a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="5a519-102">Using ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a519-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="5a519-103">始まりを宣言、`Using`をブロックし、必要に応じてブロックを制御するシステム リソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a519-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a519-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a519-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="5a519-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="5a519-105">Parts</span></span>  
  
|<span data-ttu-id="5a519-106">用語</span><span class="sxs-lookup"><span data-stu-id="5a519-106">Term</span></span>|<span data-ttu-id="5a519-107">定義</span><span class="sxs-lookup"><span data-stu-id="5a519-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="5a519-108">指定しないかどうかに必要な`resourceexpression`します。</span><span class="sxs-lookup"><span data-stu-id="5a519-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="5a519-109">この 1 つまたは複数のシステム リソースの一覧表示`Using`コントロール、コンマで区切ってをブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="5a519-110">指定しないかどうかに必要な`resourcelist`します。</span><span class="sxs-lookup"><span data-stu-id="5a519-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="5a519-111">参照変数またはこので制御するシステム リソースを参照する式`Using`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="5a519-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5a519-112">Optional.</span></span> <span data-ttu-id="5a519-113">ステートメントのブロックを`Using`ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="5a519-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="5a519-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="5a519-114">Required.</span></span> <span data-ttu-id="5a519-115">定義を終了、`Using`ブロックおよびそれによって制御されるすべてのリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="5a519-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="5a519-116">内の各リソース、`resourcelist`部分は、次の構文とパーツ。</span><span class="sxs-lookup"><span data-stu-id="5a519-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="5a519-117">または</span><span class="sxs-lookup"><span data-stu-id="5a519-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="5a519-118">resourcelist 部分</span><span class="sxs-lookup"><span data-stu-id="5a519-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="5a519-119">用語</span><span class="sxs-lookup"><span data-stu-id="5a519-119">Term</span></span>|<span data-ttu-id="5a519-120">定義</span><span class="sxs-lookup"><span data-stu-id="5a519-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="5a519-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="5a519-121">Required.</span></span> <span data-ttu-id="5a519-122">システム リソースを参照する参照変数を`Using`コントロールをブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="5a519-123">必要な場合、`Using`ステートメントがリソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a519-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="5a519-124">リソースを既に取得した場合は、2 番目の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="5a519-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="5a519-125">必須です。</span><span class="sxs-lookup"><span data-stu-id="5a519-125">Required.</span></span> <span data-ttu-id="5a519-126">リソースのクラスです。</span><span class="sxs-lookup"><span data-stu-id="5a519-126">The class of the resource.</span></span> <span data-ttu-id="5a519-127">このクラスを実装する必要があります、<xref:System.IDisposable>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5a519-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="5a519-128">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5a519-128">Optional.</span></span> <span data-ttu-id="5a519-129">インスタンスを作成するコンス トラクターに渡す引数のリスト`resourcetype`です。</span><span class="sxs-lookup"><span data-stu-id="5a519-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="5a519-130">参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a519-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="5a519-131">必須です。</span><span class="sxs-lookup"><span data-stu-id="5a519-131">Required.</span></span> <span data-ttu-id="5a519-132">変数または式の要件を満たすシステム リソースを参照する`resourcetype`です。</span><span class="sxs-lookup"><span data-stu-id="5a519-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="5a519-133">2 番目の構文を使用する場合は、制御を渡す前に、リソースを取得する必要があります、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a519-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a519-134">コメント</span><span class="sxs-lookup"><span data-stu-id="5a519-134">Remarks</span></span>  
 <span data-ttu-id="5a519-135">場合によって、コードでは、ファイル ハンドル、COM ラッパーの場合は、SQL 接続など、アンマネージ リソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="5a519-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="5a519-136">A`Using`ブロックがそれらにコードが完了すると、そのような 1 つまたは複数のリソースの破棄を保証します。</span><span class="sxs-lookup"><span data-stu-id="5a519-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="5a519-137">これによりを使用するには、他のコードで使用可能です。</span><span class="sxs-lookup"><span data-stu-id="5a519-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="5a519-138">マネージ リソースが破棄、.NET Framework ガベージ コレクター (GC) によって、手動で追加のコーディングなし。</span><span class="sxs-lookup"><span data-stu-id="5a519-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="5a519-139">必要としない、`Using`マネージ リソースをブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="5a519-140">ただし、引き続き使用できます、`Using`強制的にガベージ コレクターを待つ代わりにマネージ リソースの破棄をブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="5a519-141">A`Using`ブロックには 3 つの部分。 取得、使用状況、および破棄します。</span><span class="sxs-lookup"><span data-stu-id="5a519-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="5a519-142">*買収*変数の作成と初期化、システムのリソースを参照することを意味します。</span><span class="sxs-lookup"><span data-stu-id="5a519-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="5a519-143">`Using`ステートメントが 1 つまたは複数のリソースを取得するか、ブロックに入る前にリソースを 1 つを取得してそれを指定する、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a519-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="5a519-144">指定した場合`resourceexpression`に制御を渡す前に、リソースを取得する必要があります、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5a519-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="5a519-145">*使用状況*リソースにアクセスし、それを使ってアクションを実行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="5a519-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="5a519-146">間にあるステートメント`Using`と`End Using`リソースの使用量を表します。</span><span class="sxs-lookup"><span data-stu-id="5a519-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="5a519-147">*廃棄*を呼び出す方法、<xref:System.IDisposable.Dispose%2A>メソッド内のオブジェクトを`resourcename`です。</span><span class="sxs-lookup"><span data-stu-id="5a519-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="5a519-148">これにより、そのリソースを正常に終了するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5a519-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="5a519-149">`End Using`下にあるリソースを破棄するステートメント、`Using`ブロックのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="5a519-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5a519-150">動作</span><span class="sxs-lookup"><span data-stu-id="5a519-150">Behavior</span></span>  
 <span data-ttu-id="5a519-151">A`Using`ブロックの動作と同様に、`Try`しています.`Finally`を構築、`Try`ブロックは、リソースを使用して、`Finally`それらのブロックを破棄します。</span><span class="sxs-lookup"><span data-stu-id="5a519-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="5a519-152">このため、`Using`ブロック、ブロックを終了する方法に関係なく、リソースの破棄を保証します。</span><span class="sxs-lookup"><span data-stu-id="5a519-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="5a519-153">これは、未処理の例外を場合でも当てはまりますを除き、<xref:System.StackOverflowException>です。</span><span class="sxs-lookup"><span data-stu-id="5a519-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="5a519-154">によって取得されたすべてのリソース変数のスコープ、`Using`ステートメントに制限されます、`Using`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="5a519-155">1 つ以上のシステム リソースを指定する場合、`Using`を入れ子にする場合と同じステートメントでは、影響は`Using`互いをブロックします。</span><span class="sxs-lookup"><span data-stu-id="5a519-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="5a519-156">場合`resourcename`は`Nothing`、呼び出しがありません<xref:System.IDisposable.Dispose%2A>が行われると、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="5a519-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="5a519-157">構造化例外処理を使用してブロック内</span><span class="sxs-lookup"><span data-stu-id="5a519-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="5a519-158">内で発生する可能性がある例外を処理する必要があるかどうか、`Using`ブロック、完全なを追加することができます`Try`しています.`Finally`を構築します。</span><span class="sxs-lookup"><span data-stu-id="5a519-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="5a519-159">ケースを処理する必要がある場合で、`Using`ステートメントが、リソースの取得中に失敗した、かどうかをテストできます`resourcename`は`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="5a519-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="5a519-160">構造化例外処理を使用してブロックではなく</span><span class="sxs-lookup"><span data-stu-id="5a519-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="5a519-161">場合は、リソースの取得をより細かく制御する必要がありますまたはでコードを追加する必要があります、`Finally`ブロックを書き直すことができます、`Using`としてブロック、`Try`しています.`Finally`構築します。</span><span class="sxs-lookup"><span data-stu-id="5a519-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="5a519-162">次の例では、スケルトン`Try`と`Using`買収や破棄が同じ構造`resource`です。</span><span class="sxs-lookup"><span data-stu-id="5a519-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  <span data-ttu-id="5a519-163">内のコード、`Using`ブロック内のオブジェクトを割り当てないでください`resourcename`を別の変数です。</span><span class="sxs-lookup"><span data-stu-id="5a519-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="5a519-164">終了すると、`Using`ブロック、リソースが破棄され、他の変数が指すリソースにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="5a519-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a519-165">例</span><span class="sxs-lookup"><span data-stu-id="5a519-165">Example</span></span>  
 <span data-ttu-id="5a519-166">次の例では、log.txt は、ファイルに次の 2 つの行のテキストを書き込むファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5a519-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="5a519-167">例もその同じファイルをテキストの行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5a519-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="5a519-168"><xref:System.IO.TextWriter>と<xref:System.IO.TextReader>クラスで実装、<xref:System.IDisposable>コードで使用できるインターフェイス、`Using`ステートメント ファイルの書き込みの後に閉じられたし、読み取り操作は正しくことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5a519-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5a519-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a519-169">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="5a519-170">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="5a519-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="5a519-171">方法 : システム リソースを破棄する</span><span class="sxs-lookup"><span data-stu-id="5a519-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
