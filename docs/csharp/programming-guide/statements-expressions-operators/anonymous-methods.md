---
title: "匿名メソッド (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d942e0f3245f6404c896173b2c7ca6f1090a8c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-methods-c-programming-guide"></a>匿名メソッド (C# プログラミング ガイド)
C# 2.0 より前のバージョンでは、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)を宣言するには[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)を使用するしかありませんでした。 C# 2.0 では匿名メソッドが導入され、C# 3.0 以降では、インライン コードを記述するための本来の方法として、匿名メソッドに代わってラムダ式が使用されるようになりました。 ただし、このトピックに記載した匿名メソッドに関する情報は、ラムダ式にも適用されます。 ラムダ式にはない機能を匿名メソッドが備えているケースが 1 つあります。 匿名メソッドではパラメーター リストを省略できます。 つまり、匿名メソッドを、さまざまなシグネチャを持つデリゲートに変換できます。 これはラムダ式では不可能です。 ラムダ式の詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 匿名メソッドは、基本的にコード ブロックをデリゲート パラメーターとして渡すときに作成します。 2 つの例を挙げます。  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 匿名メソッドを使用すると、別のメソッドを作成する必要がないため、デリゲートをインスタンス化する際のコーディングのオーバーヘッドを削減できます。  
  
 たとえば、デリゲートの代わりにコード ブロックを指定すると、メソッドを作成するのが余分なオーバーヘッドと思われる場合に役立つことがあります。 新しいスレッドを開始する場合などがそのよい例です。 このクラスではスレッドを作成し、スレッドが実行するコードも含みますが、デリゲート用の追加のメソッドは作成していません。  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>コメント  
 匿名メソッドのパラメーターのスコープは、"*匿名メソッド ブロック*" です。  
  
 匿名メソッド ブロックの内部で使用しているジャンプ ステートメント ([goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md) など) のジャンプ先がブロックの外部にある場合はエラーになります。 また、匿名メソッド ブロックの外部で使用しているジャンプ ステートメント (`goto`、`break`、`continue` など) のジャンプ先がブロックの内部にある場合もエラーになります。  
  
 匿名メソッドの宣言をスコープに含むローカル変数とパラメーターは、匿名メソッドの "*外部*" 変数と呼ばれます。 たとえば、次のコード セグメントに示されている `n` は外部変数です。  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 外部変数 `n` への参照は、デリゲートの作成時に "*キャプチャ*" されるといわれます。 ローカル変数とは異なり、匿名メソッドを参照するデリゲートがガベージ コレクションの対象になるまで、キャプチャされた変数の有効期間を拡張します。  
  
 匿名メソッドは、外部スコープの [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターや [out](../../../csharp/language-reference/keywords/out.md) パラメーターにアクセスできません。  
  
 "*匿名メソッド ブロック*" 内のアンセーフ コードにはアクセスできません。  
  
 匿名メソッドは、[is](../../../csharp/language-reference/keywords/is.md) 演算子の左辺では使用できません。  
  
## <a name="example"></a>例  
 次の例は、デリゲートをインスタンス化する 2 つの方法を示しています。  
  
-   デリゲートと匿名メソッドを関連付ける。  
  
-   デリゲートと名前付きメソッド (`DoWork`) を関連付ける。  
  
 どちらの場合も、デリゲートを呼び出すと、メッセージが表示されます。  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
