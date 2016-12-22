---
title: "for (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
  - "for_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "for キーワード [C#]"
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# for (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`for` のループを使用して、`false`指定した式がになるまでステートメントまたはステートメントのブロックを繰り返し実行できます。  この種類のループが配列の反復処理に何時間を反復処理してループにするか、先立ってがわかっている他のアプリケーションに便利です。  
  
## 使用例  
 次の例では、`i` の値がコンソールに出力され、1でループの各反復処理の間にインクリメントされます。  
  
 [!code-cs[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 前の例の `for` のステートメントは次のアクションを実行します。  
  
1.  最初に、可変 `i` の初期値はに設定されます。  この手順は一度だけに関係なく、数時間をループの繰り返し回数発生します。  イベントの外側として初期化するプロセスをループについて考えることができます。  
  
2.  要件 \(`i <= 5`\) を評価するには、`i` の値は5.と比較されます。  
  
    -   `i` が5以下の場合、条件が `true`に評価され、次のアクションが発生します。  
  
        1.  ループ本体の `Console.WriteLine` のステートメントは `i`の値を表示します。  
  
        2.  `i` の値は1.でインクリメントされます。  
  
        3.  ループは、手順2の先頭に条件を再評価するに返されます。  
  
    -   `i` が5より大きい場合、条件はと評価 `false`し、ループを終了します。  
  
 `i` の初期値が5よりも大きい場合は、ループの本体が一度実行されないことに注意してください。  
  
 `for` のステートメントで初期化子、要件、および反復子のセクションを定義します。  これらのセクションでは、通常、数時間をループが反復処理するかを判定します。  
  
```c#  
for (initializer; condition; iterator)  
    body  
```  
  
 セクションには、次の目的に使用されます。  
  
-   初期化子のセクションでは、最初の条件を設定します。  こののステートメントは一度だけループに入る前に、実行をバッチ処理されます。  セクションには、次の2種類の選択項目の1つがだけ指定できます。  
  
    -   最初の例として、ローカル ループ変数の宣言と初期化は、示します \(`int i = 1`\)。  変数はループにローカルで、ループの外部からアクセスできません。  
  
    -   コンマで区切られた次の一覧からのゼロ以上のステートメントのexpressons。  
  
        -   [割り当て](../../../csharp/language-reference/operators/assignment-operator.md) のステートメント  
  
        -   メソッドの呼び出し  
  
        -   `++i` または `i++`などの [インクリメント](../../../csharp/language-reference/operators/increment-operator.md) の式のプレフィックスまたは後に追加します。  
  
        -   `--i` または `i--`などの [デクリメント](../../../csharp/language-reference/operators/decrement-operator.md) の式のプレフィックスまたは後に追加します。  
  
        -   [&#91;new&#93;](../../../visual-basic/language-reference/operators/new-operator.md)を使用してオブジェクトの作成  
  
        -   [&#91;await&#93;](../../../csharp/language-reference/keywords/await.md) の式  
  
-   要件のセクションでは、ループが終了するか、または再度実行する必要があるかどうかの決定を評価するブール式が含まれます。  
  
-   反復子のセクションが発生して、ループ本体の各反復後に定義します。  反復子のセクションでは、次のステートメントの式のゼロ以上を、コンマで区切って含まれています:  
  
    -   [割り当て](../../../csharp/language-reference/operators/assignment-operator.md) のステートメント  
  
    -   メソッドの呼び出し  
  
    -   `++i` または `i++`などの [インクリメント](../../../csharp/language-reference/operators/increment-operator.md) の式のプレフィックスまたは後に追加します。  
  
    -   `--i` または `i--`などの [デクリメント](../../../csharp/language-reference/operators/decrement-operator.md) の式のプレフィックスまたは後に追加します。  
  
    -   [&#91;new&#93;](../../../visual-basic/language-reference/operators/new-operator.md)を使用してオブジェクトの作成  
  
    -   [&#91;await&#93;](../../../csharp/language-reference/keywords/await.md) の式  
  
-   ループの本体は、ステートメントで、空のステートメントも、独自に作成する中かっこのゼロ以上のステートメントを囲むことで、ステートメント ブロック構成されます。  
  
     `for` のループの [&#91;break&#93;](../../../csharp/language-reference/keywords/break.md) のキーワードを使用して生成したり、次のイテレーションに [&#91;continue&#93;](../../../csharp/language-reference/keywords/continue.md) のキーワードを使用してステップ インできます。  また [Goto](../../../csharp/language-reference/keywords/goto.md)、[返します。](../../../csharp/language-reference/keywords/return.md)、または [スローされます。](../../../csharp/language-reference/keywords/throw.md) のステートメントを使用してループを抜けることができます。  
  
 このトピックの最初の例は、セクションの次のオプションをする最も一般的な種類の `for` のループを示します。  
  
-   初期化子はループの反復カウントを保持するローカル `i`、ループ変数の宣言と初期化します。  
  
-   状態チェック既知の最終的な値である5.に対するループ変数の値。  
  
-   反復子のセクションでは、ループの各反復を集計するには、後置インクリメントのステートメント、`i++`を使用します。  
  
 次の例では、複数のあまり一般的なオプションを示します。: 値を初期化子、および反復子のセクションの両方の `Console.WriteLine` のメソッド、および反復子のセクションの2種類の変数の値の変更を開始する初期化子のセクションの外部ループ変数に割り当てます。  
  
 [!code-cs[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 `for` のステートメントを定義する式はすべて省略可能です。  たとえば、次のステートメントでは、無限ループを作成します。  
  
 [!code-cs[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [for ステートメント \(C\+\+\)](/visual-cpp/cpp/for-statement-cpp)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)