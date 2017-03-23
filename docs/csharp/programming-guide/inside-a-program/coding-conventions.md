---
title: "C# のコーディング規則 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, コーディング規則"
  - "コーディング規則, C#"
  - "Visual C#, コーディング規則"
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# C# のコーディング規則 (C# プログラミング ガイド)
[C\# 言語仕様](http://go.microsoft.com/fwlink/?LinkId=199552)では、コーディング標準が定義されていません。  ただし、このトピックのガイドラインは、サンプルおよびドキュメントを開発するためにマイクロソフトによって使用されます。  
  
 コーディング規約には、次の目的があります。  
  
-   コードの見た目が統一されるため、コードを読むときに、レイアウトではなく内容に重点を置くことができます。  
  
-   これにより、経験に基づいて推測することで、コードをより迅速に理解することができます。  
  
-   コードのコピー、変更、および保守が容易になります。  
  
-   コーディング規約により、C\# のベスト プラクティスがわかります。  
  
## 名前付け規則  
  
-   [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)が含まれていない簡単な例では、名前空間の修飾を使用します。  プロジェクトに名前空間が既定でインポートされていることがわかっている場合は、その名前空間の各名前を完全修飾する必要はありません。   次の例に示すように、修飾名が長すぎて 1 行に収まらない場合は、ドット \(.\) の後で改行できます。  
  
     [!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]  
  
-   他のガイドラインに合わせて、Visual Studio デザイナーのツールを使用して作成されたオブジェクトの名前を変更する必要はありません。  
  
## レイアウト規則  
 コードの構造を強調する書式が使用され、コードが読みやすくなっているのが、優れたレイアウトです。  マイクロソフトの例とサンプルは、次の規則に準拠しています。  
  
-   コード エディターの既定の設定 \(スマート インデント、4 文字インデント、タブを空白として保存\) を使用します。  詳細については、「[\[オプション\]、\[テキスト エディター\]、\[C\#\]、\[書式設定\]](/visual-studio/ide/reference/options-text-editor-csharp-formatting)」を参照してください。  
  
-   1 つの行には 1 つのステートメントのみを記述します。  
  
-   1 つの行には 1 つの宣言のみを記述します。  
  
-   継続行にインデントが自動的に設定されない場合は、1 タブ ストップ \(4 つの空白\) 分のインデントを設定します。  
  
-   メソッド定義とプロパティ定義の間に少なくとも 1 行の空白行を追加します。  
  
-   次のコードに示すように、式に句を作成するときはかっこを使用します。  
  
     [!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]  
  
## コメント規則  
  
-   コメントは、コード行の末尾ではなく別の行に記述します。  
  
-   コメントのテキストは大文字で開始します。  
  
-   コメントのテキストはピリオドで終了します。  
  
-   次の例に示すように、コメント デリミター \(\/\/\) とコメント テキストの間に空白を 1 つ挿入します。  
  
     [!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]  
  
-   アスタリスクを整形したブロックでコメントを囲まないようにします。  
  
## 言語ガイドライン  
 以降のセクションでは、コード例とサンプルを準備する際に C\# チームが従っている方法について説明します。  
  
### 文字列型 \(String\)  
  
-   次のコードに示すように、短い文字列を連結するときは `+` 演算子を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]  
  
-   ループ内で文字列を追加する場合 \(特に大量のテキストを処理する場合\) は、<xref:System.Text.StringBuilder> オブジェクトを使用します。  
  
     [!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]  
  
### 暗黙的に型指定されるローカル変数  
  
-   変数の型が代入の右側から明らかである場合、または厳密な型が重要でない場合は、ローカル変数の[暗黙の型指定](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]  
  
-   代入の右側から型が明らかではない場合は、[var](../../../csharp/language-reference/keywords/var.md) を使用しないでください。  
  
     [!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]  
  
-   変数の型を指定するときに変数名に頼らないでください。  変数名が正しくない場合があります。  
  
     [!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]  
  
-   [dynamic](../../../csharp/language-reference/keywords/dynamic.md) の代わりに `var` を使用しないようにしてください。  
  
-   [for](../../../csharp/language-reference/keywords/for.md) ループおよび [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループでループ変数の型を決定するときは、暗黙の型指定を使用します。  
  
     次の例では、`for` ステートメントで暗黙の型指定を使用しています。  
  
     [!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]  
  
     次の例では、`foreach` ステートメントで暗黙の型指定を使用しています。  
  
     [!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]  
  
### Unsigned データ型  
  
-   通常は、unsigned 型ではなく `int` を使用します。  C\# では `int` を使用するのが一般的です。`int` を使用すると、他のライブラリと対話しやすくなります。  
  
### 配列  
  
-   宣言行で配列を初期化するときは簡潔な構文を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]  
  
### デリゲート  
  
-   デリゲート型のインスタンスを作成するときは簡潔な構文を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]  
  
### 例外処理における try\-catch ステートメントと using ステートメント  
  
-   ほとんどの例外処理には、[try\-catch](../../../csharp/language-reference/keywords/try-catch.md) ステートメントを使用します。  
  
     [!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]  
  
-   C\# の [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)を使用して、コードを簡潔にします。  [try\-finally](../../../csharp/language-reference/keywords/try-finally.md) ステートメントを使用するときに `finally` ブロックのコードが <xref:System.IDisposable.Dispose%2A> メソッドの呼び出しだけである場合は、`using` ステートメントを代わりに使用します。  
  
     [!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]  
  
### && 演算子と &#124;&#124; 演算子  
  
-   例外を回避し、不要な比較を省いてパフォーマンスを向上させるには、次の例に示すように、比較を実行するときに [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) \([&](../../../csharp/language-reference/operators/and-operator.md) ではなく\) および [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) \(                                       [&#124;](../../../csharp/language-reference/operators/or-operator.md) ではなく\) を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]  
  
### new 演算子  
  
-   次の宣言に示すように、暗黙の型指定を使用してオブジェクトのインスタンス化を簡潔な形式にします。  
  
     [!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]  
  
     前の行は次の宣言に相当します。  
  
     [!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]  
  
-   オブジェクト初期化子を使用してオブジェクトの作成を簡略化します。  
  
     [!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]  
  
### イベント処理  
  
-   後で削除する必要のないイベント ハンドラーを定義する場合は、ラムダ式を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]  
  
     [!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]  
  
### 静的メンバー  
  
-   [静的](../../../csharp/language-reference/keywords/static.md)メンバーは、クラス名 \(*ClassName.StaticMember*\) を使用して呼び出します。  こうすることで、静的アクセスが明確になり、コードがよりわかりやすくなります。  派生クラスの名前を持つ基本クラスに定義された静的メンバーを指定しないでください。  このコードをコンパイルすると、コードが読みやすくなくなり、派生クラスに同じ名前の静的メンバーを追加すると、将来的にコードが中断する場合があります。  
  
### LINQ クエリ  
  
-   クエリ変数にはわかりやすい名前を使用します。  次の例では、シアトル在住の顧客に `seattleCustomers` を使用しています。  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   エイリアスを使用して、匿名型のプロパティ名の大文字と小文字の使用が正しい Pascal 形式になるようにします。  
  
     [!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]  
  
-   結果のプロパティ名があいまいになる場合は、プロパティ名を変更します。  たとえば、クエリで顧客名と販売店 ID を返す場合、クエリ結果で `Name` と `ID` をそのまま使用するのではなく、これらの名前を変更し、`Name` が顧客の名前であり、`ID` が販売店の ID であることを明確にします。  
  
     [!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]  
  
-   クエリ変数と範囲変数の宣言で暗黙の型指定を使用します。  
  
     [!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]  
  
-   前の例に示すように、クエリ句を [from](../../../csharp/language-reference/keywords/from-clause.md) 句の下に配置します。  
  
-   [where](../../../csharp/language-reference/keywords/where-clause.md) 句を他のクエリ句より先に使用し、それ以降のクエリ句では、フィルター化されたデータセットが処理されるようにします。  
  
     [!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]  
  
-   内部コレクションにアクセスするときは、[join](../../../csharp/language-reference/keywords/join-clause.md) 句ではなく複数の `from` 句を使用します。   たとえば、`Student` オブジェクトのコレクションがあり、各オブジェクトに試験の点数のコレクションが含まれているとします。  次のクエリを実行すると、90 点より高い点数とその点数を取った学生の姓が返されます。  
  
     [!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]  
  
## セキュリティ  
 「[安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)」のガイドラインに従ってください。  
  
## 参照  
 [Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)   
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)