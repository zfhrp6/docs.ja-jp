---
title: "方法 : 例外を明示的にスローする"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="cb086-102">例外を明示的にスローする方法</span><span class="sxs-lookup"><span data-stu-id="cb086-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="cb086-103">`throw` ステートメントを使用して、例外を明示的にスローできます。</span><span class="sxs-lookup"><span data-stu-id="cb086-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="cb086-104">`throw` ステートメントを使って、キャッチした例外をもう一度スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cb086-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="cb086-105">再スローされる例外に情報を追加して、デバッグ時により多くの情報を提供するコーディング手法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cb086-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="cb086-106">次のコード例では、`try`/`catch` ブロックを使用して可能性のある <xref:System.IO.FileNotFoundException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="cb086-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="cb086-107">次の `try` ブロックは、<xref:System.IO.FileNotFoundException> をキャッチし、データ ファイルが見つからない場合に、メッセージをコンソールに出力する `catch` ブロックです。</span><span class="sxs-lookup"><span data-stu-id="cb086-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="cb086-108">次のステートメントは、新しい <xref:System.IO.FileNotFoundException> をスローして、テキスト情報を例外に追加する `throw` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="cb086-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="cb086-109">参照</span><span class="sxs-lookup"><span data-stu-id="cb086-109">See Also</span></span>  
[<span data-ttu-id="cb086-110">例外</span><span class="sxs-lookup"><span data-stu-id="cb086-110">Exceptions</span></span>](index.md)
