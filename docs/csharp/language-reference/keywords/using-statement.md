---
title: using ステートメント (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7bf9138721ecee63c65c2e39922aee96b1dfaa41
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207963"
---
# <a name="using-statement-c-reference"></a>using ステートメント (C# リファレンス)
<xref:System.IDisposable> オブジェクトの正しい使用を保証する簡易構文を提供します。  
  
## <a name="example"></a>例  
 `using` ステートメントを使用する方法の例を次に示します。  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>コメント  
 <xref:System.IO.File> と <xref:System.Drawing.Font> は、アンマネージ リソース (この場合はファイル ハンドルとデバイス コンテキスト) にアクセスするマネージ型の例です。 アンマネージ リソースや、それをカプセル化するクラス ライブラリ型は他にもたくさんあります。 このような型はすべて、<xref:System.IDisposable> インターフェイスを実装する必要があります。  
  
`IDisposable` オブジェクトの有効期間が 1 つのメソッドに限定されているとき、それを `using` ステートメントで宣言し、インスタンス化してください。 `using` ステートメントは、オブジェクトで正しく <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。(前述のようにこのステートメントを使用する場合) <xref:System.IDisposable.Dispose%2A> が呼び出されるとすぐに、オブジェクト自体がスコープの外側に出されます。 オブジェクトは、`using` ブロック内では読み取り専用です。変更したり再割り当てしたりすることはできません。  
  
 `using` ステートメントにより、`using` ブロックで例外が発生した場合でも必ず <xref:System.IDisposable.Dispose%2A> が呼び出されます。 オブジェクトを `try` ブロックに配置し、`finally` ブロックで <xref:System.IDisposable.Dispose%2A> を呼び出しても、同じ結果が得られます。実際には、コンパイラは `using` ステートメントをこのように変換します。 前のコード例は、コンパイル時に次のコードに展開されます (オブジェクトのスコープ制限を定義する中かっこが加えられていることに注意してください)。  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 `try`-`finally` ステートメントの詳細については、「[try-finally](try-finally.md)」のトピックを参照してください。
  
 次の例のように、`using` ステートメントでは型の複数のインスタンスを宣言できます。  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 リソース オブジェクトをインスタンス化してから、変数を `using` ステートメントに渡すことはできますが、これはベスト プラクティスではありません。 この場合、アンマネージ リソースへのアクセスがなくなっている可能性が高いのにもかかわらず、制御が `using` ブロックを離れた後もオブジェクトはスコープ内に残ります。 つまり、完全に初期化されることはなくなります。 `using` ブロックの外側でオブジェクトを使用しようとすると、例外がスローされる可能性があります。 このため、通常は、オブジェクトを `using` ステートメントでインスタンス化して、そのスコープを `using` ブロックに制限することをお勧めします。  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
`IDisposable` オブジェクトの破棄に関する詳細については、「[IDisposable を実装するオブジェクトの使用](../../../standard/garbage-collection/using-objects.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)  
 [ガベージ コレクション](../../../standard/garbage-collection/index.md)  
 [IDisposable を実装するオブジェクトの使用](../../../standard/garbage-collection/using-objects.md)  
 [IDisposable インターフェイス](xref:System.IDisposable)
