---
title: "名前空間の使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.names"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "完全修飾名 [C#]"
  - "名前空間 [C#], 使い方"
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# 名前空間の使用 (C# プログラミング ガイド)
C\# プログラムでは、名前空間が 2 つの点で頻繁に使用されます。  1 つは、.NET Framework クラスが多数のクラスを編成するために名前空間を使用するからであり、  もう 1 つは、固有の名前空間を宣言すると、大型のプログラミング プロジェクトでクラス名とメソッド名のスコープを管理するのに役立つからです。  
  
## 名前空間へのアクセス  
 C\# アプリケーションは、一般に `using` ディレクティブのセクションから始まります。  このセクションには、アプリケーションが頻繁に使用する名前空間が列挙され、包含されているメソッドを使用するたびに完全修飾名を指定しなくても済むようにします。  
  
 たとえば、次の行を記述したとします。  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/using.cs#1)]  
  
 この場合、プログラムの開始位置で、次のコードを使用できます。  
  
 [!code-cs[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#31)]  
  
 このコードの本来の書式は次のとおりです。  
  
 [!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#30)]  
  
## 名前空間エイリアス  
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md) を使用しても[名前空間](../../../csharp/language-reference/keywords/namespace.md)のエイリアスを作成することができます。  たとえば、入れ子になった名前空間を含む、以前に作成した名前空間を使用する場合は、次の例のようにエイリアスを宣言して、特定の名前空間を簡単に参照することもできます。  
  
 [!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces2.cs#7)]  
  
## 名前空間によるスコープの制御  
 `namespace` キーワードは、スコープの宣言に使用します。  プロジェクト内でスコープを作成すると、コードの編成が容易になり、グローバルに一意の型を作成できます。  次の例では、入れ子関係にある 2 つの名前空間で `SampleClass` というクラスを定義します。  [. 演算子](../../../csharp/language-reference/operators/member-access-operator.md) を使用して、呼び出されるメソッドを区別します。  
  
 [!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces.cs#8)]  
  
## 完全修飾名  
 名前空間と型には、論理階層を示す完全修飾名で表された一意のタイトルが割り当てられています。  たとえば、ステートメント `A.B` は、`A` が名前空間または型の名前であり、`B` が A の入れ子であることを意味します。  
  
 入れ子にされたクラスと名前空間を次の例に示します。  完全修飾名は、各エンティティの後のコメントとして示されています。  
  
 [!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces.cs#9)]  
  
 前のコードは、次のような関係になっています。  
  
-   名前空間 `N1` は、グローバル名前空間のメンバーです。  この完全修飾名は `N1` です。  
  
-   名前空間 `N2` は、`N1` のメンバーです。  この完全修飾名は `N1.N2` です。  
  
-   クラス `C1` は `N1` のメンバーです。  この完全修飾名は `N1.C1` です。  
  
-   クラス名 `C2` は、このコードで 2 回使われています。  ただし、完全修飾名は異なります。  `C2` の最初のインスタンスは `C1` の内部で宣言されているので、完全修飾名は `N1.C1.C2` です。  `C2` の 2 番目のインスタンスは名前空間 `N2` の内部で宣言されているので、完全修飾名は `N1.N2.C2` です。  
  
 上のコード セグメントを使用して、次のように新しいクラス メンバー `C3` を名前空間 `N1.N2` に追加できます。  
  
 [!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces.cs#10)]  
  
 通常、`::` は、名前空間エイリアスを参照する際に使用し、`global::` は、グローバル名前空間を参照する際に使用します。`.` は、型またはメンバーを修飾する際に使用します。  
  
 名前空間ではなく型を参照するエイリアスで `::` を使用するのは誤りです。  次に例を示します。  
  
 [!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces2.cs#11)]  
  
 [!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces2.cs#12)]  
  
 `global` という語は定義済みのエイリアスではないので、`global.X` には特別な意味がないことに注意してください。  この語は、`::` と共に使用したときにのみ特別な意味が与えられます。  
  
 `global::` は常にグローバル名前空間を参照し、エイリアスを参照しないので、global という名前のエイリアスを定義すると、コンパイラ警告 CS0440 が生成されます。  たとえば、次の行では警告が生成されます。  
  
 [!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces2.cs#13)]  
  
 エイリアスで `::` を使用すると、追加の型が予想外に導入されることを防ぐことができます。  次に例を示します。  
  
 [!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces.cs#14)]  
  
 [!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces.cs#15)]  
  
 このコードは動作しますが、`Alias` という型が後で導入されると、`Alias.` は代わりにその型にバインドされます。  `Alias::Exception` を使用すると、`Alias` は名前空間エイリアスとして扱われ、型と間違われることがなくなります。  
  
 `global` エイリアスの詳細については、「[方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. 演算子](../../../csharp/language-reference/operators/member-access-operator.md)   
 [:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)