---
title: "方法: Try ブロックと Catch ブロックを使用して例外をキャッチする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 192f762872b112ea261d22251175db6867229437
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="90376-102">Try ブロックと Catch ブロックを使用して例外をキャッチする方法</span><span class="sxs-lookup"><span data-stu-id="90376-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="90376-103">例外をスローする可能性のあるコードのセクションを `try` ブロックに配置し、例外を処理するコードを `catch` ブロックに配置します。</span><span class="sxs-lookup"><span data-stu-id="90376-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="90376-104">`catch` ブロックは、キーワード `catch` で始まり、その後に例外の種類と実行するアクションが続く一連のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="90376-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="90376-105">次のコード例では、`try`/`catch` ブロックを使用して可能性のある例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="90376-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="90376-106">`Main` メソッドには、`try` ブロックと、`data.txt` と呼ばれるデータ ファイルを開き、ファイルから文字列を書き込む <xref:System.IO.StreamReader> ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="90376-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="90376-107">次の `try` ブロックは、`try` によって生成される任意の例外をキャッチする `catch` ブロックです。</span><span class="sxs-lookup"><span data-stu-id="90376-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="90376-108">共通言語ランタイムは、catch ブロックでキャッチされなかった例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="90376-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="90376-109">ランタイムの構成方法に応じて、デバッグ ダイアログ ボックスが表示されるか、プログラムの実行が停止され、例外情報を含むダイアログ ボックスが表示されるか、または STDERR にエラーが出力されます。</span><span class="sxs-lookup"><span data-stu-id="90376-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="90376-110">ほぼすべてのコード行で例外 (特に、<xref:System.OutOfMemoryException> などの共通言語ランタイムそのものによってスローされる例外) が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90376-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="90376-111">ほとんどのアプリケーションではこれらの例外を処理する必要はありませんが、他のユーザーが使用するライブラリを記述する際には、この可能性に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90376-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="90376-112">Try ブロック内でコードを設定するタイミングに関しては、「[例外の推奨事項](best-practices-for-exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90376-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90376-113">参照</span><span class="sxs-lookup"><span data-stu-id="90376-113">See Also</span></span>  
[<span data-ttu-id="90376-114">例外</span><span class="sxs-lookup"><span data-stu-id="90376-114">Exceptions</span></span>](index.md)
