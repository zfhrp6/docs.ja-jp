---
title: for (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a>for (C# リファレンス)
`for` ループを使うと、指定した式が `false` と評価されるまで、ステートメントまたはステートメント ブロックを繰り返し実行することができます。 この種類のループは、配列の反復処理などループの反復回数が事前にわかっている用途に使用します。  
  
## <a name="example"></a>例  
 次の例では、`i` の値をコンソールに出力し、ループの反復ごとにその値を 1 ずつインクリメントします。  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 前の例で `for` ステートメントによって実行されている処理は次のとおりです。  
  
1.  まず、変数 `i` の初期値が確立されます。 ループの反復回数に関係なく、このステップが実行されるのは 1 回だけです。 この初期化は、ループ処理プロセスの外で実行されると考えることができます。  
  
2.  条件 (`i <= 5`) を評価するために、`i` の値が 5 と比較されます。  
  
    -   `i` が 5 以下である場合、条件が `true` に評価され、次の処理が実行されます。  
  
        1.  ループ本体にある `Console.WriteLine` ステートメントによって `i` の値が表示されます。  
  
        2.  `i` の値が 1 ずつインクリメントされます。  
  
        3.  ループがステップ 2 の最初に戻り、再度条件が評価されます。  
  
    -   `i` が 5 より大きい場合、条件が `false` に評価され、ループが終了します。  
  
 `i` の初期値が 5 より大きい場合、ループの本体は一度も実行されないことに注意してください。  
  
 すべての `for` ステートメントには、初期化子、条件、反復子のセクションが定義されています。 通常、ループの反復回数は、これらのセクションによって決まります。  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 各セクションには次の目的があります。  
  
-   初期化子セクションによって初期条件が設定されます。 ループに入る前に、このセクションのステートメントが 1 回だけ実行されます。 このセクションには、次の 2 つの項目のうち、いずれか一方のみを記述することができます。  
  
    -   ローカル ループ変数の宣言と初期化。冒頭の例 (`int i = 1`) を参照してください。 この変数はループに対してローカルであり、ループ外からアクセスすることはできません。  
  
    -   次に列挙した 0 個以上のステートメント式 (コンマ区切り)。  
  
        -   [代入](../../../csharp/language-reference/operators/assignment-operator.md)ステートメント  
  
        -   メソッドの呼び出し  
  
        -   前置または後置の[インクリメント](../../../csharp/language-reference/operators/increment-operator.md)式 (`++i`、`i++` など)  
  
        -   前置または後置の[デクリメント](../../../csharp/language-reference/operators/decrement-operator.md)式 (`--i`、`i--` など)  
  
        -   [new](../../../csharp/language-reference/keywords/new-operator.md) を使用したオブジェクト作成  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) 式  
  
-   条件セクションには、ループを終了するか再度実行するかを判断する際に評価されるブール式を記述します。  
  
-   ループ本体の反復処理が終わるたびに実行される処理を反復子セクションで定義します。 反復子セクションには、次のステートメント式を 0 個以上、コンマで区切って記述します。  
  
    -   [代入](../../../csharp/language-reference/operators/assignment-operator.md)ステートメント  
  
    -   メソッドの呼び出し  
  
    -   前置または後置の[インクリメント](../../../csharp/language-reference/operators/increment-operator.md)式 (`++i`、`i++` など)  
  
    -   前置または後置の[デクリメント](../../../csharp/language-reference/operators/decrement-operator.md)式 (`--i`、`i--` など)  
  
    -   [new](../../../csharp/language-reference/keywords/new-operator.md) を使用したオブジェクト作成  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) 式  
  
-   ループの本体は、単一のステートメント、空のステートメント、またはステートメント ブロックで構成され、0 個以上のステートメントを中かっこで囲んで記述します。  
  
     [break](../../../csharp/language-reference/keywords/break.md) キーワードを使って `for` ループを抜けたり、[continue](../../../csharp/language-reference/keywords/continue.md) キーワードを使って次の反復処理にステップ実行したりできます。 また、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、[throw](../../../csharp/language-reference/keywords/throw.md) のいずれかのステートメントを使ってループを終了することもできます。  
  
 このトピックの冒頭の例は、きわめて標準的な `for` ループで、各セクションには次の内容が記述されています。  
  
-   初期化子では、ループの反復回数を保持するローカル ループ変数 `i` を宣言して初期化しています。  
  
-   条件では、既知の最終値 (5) と照らし合わせてループ変数の値をチェックしています。  
  
-   反復子セクションでは、後置インクリメント ステートメント (`i++`) を使って、ループの反復回数をカウントしています。  
  
 次のコードはやや特殊な例です。初期化子セクションで外部ループ変数に値を代入し、初期化子セクションと反復子セクションの両方で `Console.WriteLine` メソッドを呼び出しています。さらに、反復子セクションで 2 つの変数の値を変更しています。  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 `for` ステートメントを定義する式はすべて省略可能です。 たとえば次のステートメントは無限ループを作成します。  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [for ステートメント (C++)](/cpp/cpp/for-statement-cpp)  
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)
