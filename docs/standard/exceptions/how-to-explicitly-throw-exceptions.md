---
title: '方法 : 例外を明示的にスローする'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4eeb70c10d71a7c96136039342bcdcc7bc8ece20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="2f0c9-102">例外を明示的にスローする方法</span><span class="sxs-lookup"><span data-stu-id="2f0c9-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="2f0c9-103">`throw` ステートメントを使用して、例外を明示的にスローできます。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="2f0c9-104">`throw` ステートメントを使って、キャッチした例外をもう一度スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="2f0c9-105">再スローされる例外に情報を追加して、デバッグ時により多くの情報を提供するコーディング手法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="2f0c9-106">次のコード例では、`try`/`catch` ブロックを使用して可能性のある <xref:System.IO.FileNotFoundException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="2f0c9-107">次の `try` ブロックは、<xref:System.IO.FileNotFoundException> をキャッチし、データ ファイルが見つからない場合に、メッセージをコンソールに出力する `catch` ブロックです。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="2f0c9-108">次のステートメントは、新しい <xref:System.IO.FileNotFoundException> をスローして、テキスト情報を例外に追加する `throw` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="2f0c9-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="2f0c9-109">参照</span><span class="sxs-lookup"><span data-stu-id="2f0c9-109">See Also</span></span>  
[<span data-ttu-id="2f0c9-110">例外</span><span class="sxs-lookup"><span data-stu-id="2f0c9-110">Exceptions</span></span>](index.md)
