---
title: "IDisposable を実装するオブジェクトの使用"
ms.custom: 
ms.date: 04/07/2017
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
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable を実装するオブジェクトの使用

共通言語ランタイムのガベージ コレクターがマネージ オブジェクトによって使用されるメモリを解放がアンマネージ リソースを使用する型を実装、<xref:System.IDisposable>インターフェイスが解放されるアンマネージ リソースに割り当てられたメモリを有効にします。 <xref:System.IDisposable> を実装するオブジェクトを使い終わったら、オブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を呼び出す必要があります。 2 つの方法のいずれかでこれを行うことができます。  
  
* C# の `using` ステートメントまたは Visual Basic の `Using` ステートメントを使用します。  
  
* `try/finally` ブロックを実装します。  

## <a name="the-using-statement"></a>using ステートメント

C# の `using` ステートメントおよび Visual Basic の `Using` ステートメントを使用すると、オブジェクトの作成時やクリーンアップ時に記述する必要のあるコードが簡略化されます。 `using` ステートメントは、1 つ以上のリソースを取得し、指定されたステートメントを実行し、オブジェクトを自動的に破棄します。 ただし、`using` ステートメントは、オブジェクトが構築されるメソッドのスコープ内で使用されるオブジェクトに対してのみ有効です。  
  
次の例では、`using` ステートメントを使用して <xref:System.IO.StreamReader?displayProperty=nameWithType> オブジェクトを作成し解放します。  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<xref:System.IO.StreamReader> クラスは <xref:System.IDisposable> インターフェイスを実装し、これはアンマネージ リソースを使用することを示していますが、例では <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> メソッドを明示的に呼び出していないことに注意してください。 C# または Visual Basic コンパイラが `using` ステートメントを見つけると、明示的に `try/finally` ブロックを含む次のコードと同等の中間言語 (IL) を生成します。  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C#`using`ステートメントでは入れ子に内部的には 1 つのステートメントで複数のリソースを取得することもできます`using`ステートメントです。 次の例では、2 つの異なるファイルの内容を読み取るために、<xref:System.IO.StreamReader> の 2 つのオブジェクトをインスタンス化します。  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/Finally ブロック

`using` ステートメントで `try/finally` ブロックをラップする代わりに、`try/finally` ブロックを直接実装することもできます。 これは、個人のコーディング スタイルであることも、次のいずれかの理由からそうすることもあります。  
  
* `catch` ブロックでスローされた例外をすべて処理する `try` ブロックを含めるため。 そうしないと、`try/catch` ブロックがない場合に `using` ブロック内でスローされた例外と同様に、`using` ステートメントによってスローされた例外は処理されません。  
  
* 宣言されたブロックに対してスコープがローカルでない <xref:System.IDisposable> を実装するオブジェクトをインスタンス化するため。  
  
使用する点を除いて、次の例は、前の例に似ています、`try/catch/finally`のインスタンスを作成、使用、および破棄するブロック、<xref:System.IO.StreamReader>オブジェクト、およびによってスローされる例外を処理できる、<xref:System.IO.StreamReader>コンス トラクターと、その<xref:System.IO.StreamReader.ReadToEnd%2A>メソッドです。 `finally` メソッドを呼び出す前に <xref:System.IDisposable> を実装するオブジェクトが `null` でないことを <xref:System.IDisposable.Dispose%2A> ブロックのコードがチェックしていることに注意してください。 これを行わない場合、実行時に <xref:System.NullReferenceException> 例外が発生する可能性があります。  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
実装するか、実装する必要がある場合は、この基本的なパターンを行うことができる、`try/finally`ブロックを使用するプログラミング言語をサポートしていないため、`using`ステートメントを直接呼び出すことを許可、<xref:System.IDisposable.Dispose%2A>メソッドです。 
  
## <a name="see-also"></a>関連項目

[アンマネージ リソースのクリーンアップ](../../../docs/standard/garbage-collection/unmanaged.md)   
[using ステートメント (c# リファレンス)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Using ステートメント (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
