---
title: "方法 : catch ブロックで特定の例外を使用する"
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
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>特定の例外を catch ブロックで使用する方法

一般に、適切なプログラミング、basic を使用するのではなく、特定の種類の例外をキャッチする方法は`catch`ステートメントです。

例外が発生すると、スタックに渡され、各 catch ブロックが処理する機会を与えられます。 catch ステートメントの順序が重要です。 一般的な例外 catch ブロックまたはコンパイラがエラーを発行する前に、特定の例外を対象とした catch ブロックを配置します。 適切な catch ブロックは、例外の種類を catch ブロックで指定された例外の名前に一致させることで決まります。 特定の catch ブロックがない場合は、汎用 catch ブロック (ある場合) によってキャッチされます。

次のコード例では、`try`/`catch` ブロックを使用して <xref:System.InvalidCastException> をキャッチします。 サンプルでは、1 つのプロパティ、従業員レベル (`Emlevel`) を使用して、`Employee` と呼ばれるクラスを作成します。 メソッド `PromoteEmployee` は、オブジェクトを受け取って、従業員レベルをインクリメントします。 <xref:System.DateTime> インスタンスが `PromoteEmployee` メソッドに渡されたとき、<xref:System.InvalidCastException> が発生します。

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>関連項目  
[例外](index.md)
