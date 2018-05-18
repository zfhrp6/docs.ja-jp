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
# <a name="how-to-explicitly-throw-exceptions"></a>例外を明示的にスローする方法

`throw` ステートメントを使用して、例外を明示的にスローできます。 `throw` ステートメントを使って、キャッチした例外をもう一度スローすることもできます。 再スローされる例外に情報を追加して、デバッグ時により多くの情報を提供するコーディング手法をお勧めします。

次のコード例では、`try`/`catch` ブロックを使用して可能性のある <xref:System.IO.FileNotFoundException> をキャッチします。 次の `try` ブロックは、<xref:System.IO.FileNotFoundException> をキャッチし、データ ファイルが見つからない場合に、メッセージをコンソールに出力する `catch` ブロックです。 次のステートメントは、新しい <xref:System.IO.FileNotFoundException> をスローして、テキスト情報を例外に追加する `throw` ステートメントです。

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>参照  
[例外](index.md)
