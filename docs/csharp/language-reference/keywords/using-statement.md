---
title: "using ステートメント (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a>using ステートメント (C# リファレンス)
<xref:System.IDisposable> オブジェクトの正しい使用を保証する簡易構文を提供します。  
  
## <a name="example"></a>例  
 using ステートメントを使用する方法を次の例に示します。  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>コメント  
 <xref:System.IO.File> と <xref:System.Drawing.Font> は、アンマネージ リソース (この場合はファイル ハンドルとデバイス コンテキスト) にアクセスするマネージ型の例です。 アンマネージ リソースや、それをカプセル化するクラス ライブラリ型は他にもたくさんあります。 このような型はすべて、<xref:System.IDisposable> インターフェイスを実装する必要があります。  
  
ときの有効期間、 `IDisposable` 1 つのメソッドに制限は、オブジェクトが宣言しでインスタンス化する必要があります、`using`ステートメントです。 `using` ステートメントは、オブジェクトで正しく <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。(前述のようにこのステートメントを使用する場合) <xref:System.IDisposable.Dispose%2A> が呼び出されるとすぐに、オブジェクト自体がスコープの外側に出されます。 オブジェクトは、`using` ブロック内では読み取り専用です。変更したり再割り当てしたりすることはできません。  
  
 `using` ステートメントを使用すると、オブジェクトでのメソッドの呼び出し中に例外が発生した場合でも <xref:System.IDisposable.Dispose%2A> が必ず呼び出されます。 オブジェクトを try ブロックに配置し、finally ブロックで <xref:System.IDisposable.Dispose%2A> を呼び出しても、同じ結果が得られます。実際には、コンパイラは `using` ステートメントをこのように変換します。 前のコード例は、コンパイル時に次のコードに展開されます (オブジェクトのスコープ制限を定義する中かっこが加えられていることに注意してください)。  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 次の例のように、`using` ステートメントでは型の複数のインスタンスを宣言できます。  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 リソース オブジェクトをインスタンス化してから、変数を `using` ステートメントに渡すことはできますが、これはベスト プラクティスではありません。 この場合、アンマネージ リソースへのアクセスがなくなっている可能性が高いのにもかかわらず、制御が `using` ブロックを離れた後もオブジェクトはスコープ内に残ります。 つまり、完全に初期化されることはありません。 `using` ブロックの外側でオブジェクトを使用しようとすると、例外がスローされる可能性があります。 このため、通常は、オブジェクトを `using` ステートメントでインスタンス化して、そのスコープを `using` ブロックに制限することをお勧めします。  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
破棄の詳細については`IDisposable`、オブジェクトを参照してください[IDisposable を実装するオブジェクトを使用して](../../../standard/garbage-collection/using-objects.md)です。

## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)  
 [ガベージ コレクション](../../../standard/garbage-collection/index.md)  
 [IDisposable を実装するオブジェクトの使用](../../../standard/garbage-collection/using-objects.md)  
 [IDisposable インターフェイス](xref:System.IDisposable)
