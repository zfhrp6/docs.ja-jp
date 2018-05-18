---
title: '方法: Try ブロックと Catch ブロックを使用して例外をキャッチする'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b169353752f6e6483a056cdc9dd8c3227b9ebeb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Try ブロックと Catch ブロックを使用して例外をキャッチする方法

例外をスローする可能性のあるコードのセクションを `try` ブロックに配置し、例外を処理するコードを `catch` ブロックに配置します。 `catch` ブロックは、キーワード `catch` で始まり、その後に例外の種類と実行するアクションが続く一連のステートメントです。

次のコード例では、`try`/`catch` ブロックを使用して可能性のある例外をキャッチします。 `Main` メソッドには、`try` ブロックと、`data.txt` と呼ばれるデータ ファイルを開き、ファイルから文字列を書き込む <xref:System.IO.StreamReader> ステートメントが含まれます。 次の `try` ブロックは、`try` によって生成される任意の例外をキャッチする `catch` ブロックです。

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

共通言語ランタイムは、catch ブロックでキャッチされなかった例外をキャッチします。 ランタイムの構成方法に応じて、デバッグ ダイアログ ボックスが表示されるか、プログラムの実行が停止され、例外情報を含むダイアログ ボックスが表示されるか、または STDERR にエラーが出力されます。

> [!NOTE] 
> ほぼすべてのコード行で例外 (特に、<xref:System.OutOfMemoryException> などの共通言語ランタイムそのものによってスローされる例外) が発生する可能性があります。 ほとんどのアプリケーションではこれらの例外を処理する必要はありませんが、他のユーザーが使用するライブラリを記述する際には、この可能性に注意する必要があります。 Try ブロック内でコードを設定するタイミングに関しては、「[例外の推奨事項](best-practices-for-exceptions.md)」を参照してください。

## <a name="see-also"></a>参照  
[例外](index.md)
