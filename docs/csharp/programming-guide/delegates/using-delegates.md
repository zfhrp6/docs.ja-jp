---
title: "デリゲートの使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "デリゲート [C#], 使い方"
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# デリゲートの使用 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、C および C\+\+ の関数ポインターのようなメソッドを安全にカプセル化する型です。  ただし、C 関数ポインターとは異なり、デリゲートはオブジェクト指向で、タイプ セーフで、安全です。  デリゲートの型は、デリゲートの名前によって定義されます。  次の例では、引数として[文字列](../../../csharp/language-reference/keywords/string.md)を受け取り、[void](../../../csharp/language-reference/keywords/void.md) を返すメソッドをカプセル化できる `Del` という名前のデリゲートを宣言しています。  
  
 [!code-cs[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 デリゲート オブジェクトは、通常、デリゲートがラップするメソッドの名前を指定して構成されるか、[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)を使用して構成されます。  デリゲートがインスタンス化されると、デリゲートに対するメソッドの呼び出しが、デリゲートからメソッドに渡されます。  呼び出し元によってデリゲートに渡されるパラメーターはメソッドに渡され、戻り値がある場合は、デリゲートによってメソッドから呼び出し元に返されます。  これは、デリゲートの呼び出しと呼ばれます。  インスタンス化されたデリゲートは、ラップされたメソッドそのものであるかのように呼び出すことができます。  次に例を示します。  
  
 [!code-cs[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-cs[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 デリゲート型は、.NET Framework の <xref:System.Delegate> クラスから派生しています。  デリゲート型は [sealed](../../../csharp/language-reference/keywords/sealed.md) \(派生できません\) であり、<xref:System.Delegate> からカスタム クラスを派生することはできません。  インスタンス化されたデリゲートはオブジェクトであるため、パラメーターとして渡したり、プロパティに割り当てたりすることができます。  これにより、メソッドは、パラメーターとしてデリゲートを受け入れ、後でデリゲートを呼び出すことができます。  これは非同期のコールバックと呼ばれ、長いプロセスの完了時に呼び出し元に通知する一般的な方法です。  デリゲートをこの方法で使用する場合、デリゲートを使用するコードは、使用されるメソッドの実装について認識している必要はありません。  機能は、カプセル化インターフェイスが提供する機能に似ています。  
  
 コールバックの別の一般的な使用方法は、カスタム比較メソッドの定義およびそのデリゲートの並べ替えメソッドへの引き渡しです。  これにより、呼び出し元のコードを並べ替えアルゴリズムの一部にすることができます。  次の例のメソッドは `Del` 型をパラメーターとして使用しています。  
  
 [!code-cs[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 上記で作成したデリゲートをメソッドに渡すことができます。  
  
 [!code-cs[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 次の出力がコンソールに表示されます。  
  
 `The number is: 3`  
  
 抽象化としてデリゲートを使用する場合、`MethodWithCallback` がコンソールを直接呼び出す必要はありません。コンソールに留意して設計する必要はありません。  `MethodWithCallback` は文字列を準備し、文字列を別のメソッドに渡すだけです。  これは、デリゲート メソッドが任意の数のパラメーターを使用できるため、特に強力です。  
  
 インスタンス メソッドをラップするようにデリゲートが構築された場合、デリゲートはインスタンスとメソッドの両方を参照します。  デリゲートはラップするメソッド以外のインスタンス型を認識しないため、デリゲート シグネチャと一致するオブジェクトにメソッドがある限り、どの型のオブジェクトでも参照できます。  静的メソッドをラップするようにデリゲートが構築された場合、デリゲートはそのメソッドのみを参照します。  次に宣言の例を示します。  
  
 [!code-cs[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 以前に示した静的な `DelegateMethod` と共に、`Del` インスタンスによってラップできるメソッドが 3 つあります。  
  
 デリゲートは、呼び出されたときに複数のメソッドを呼び出すことができます。  これはマルチキャスティングと呼ばれます。  デリゲートのメソッドの一覧 \(呼び出しリスト\) に追加のメソッドを追加するには、加算演算子または加算代入演算子 \('\+' または '\+\='\) を使用して 2 つのデリゲートを追加する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 この時点で、`allMethodsDelegate` には、呼び出しリスト内の 3 つのメソッド \(`Method1`、`Method2`、`DelegateMethod`\) が含まれています。  元の 3 つのデリゲートである `d1`、`d2`、および `d3` は変更されません。  `allMethodsDelegate` が呼び出されると、すべての 3 つのメソッドが順に呼び出されます。  デリゲートで参照パラメーターを使用する場合、参照は、3 つのメソッドに順番に渡され、1 つのメソッドによって行われた変更は、次のメソッドに示されます。  いずれかのメソッドがメソッド内でキャッチされない例外をスローした場合、デリゲートの呼び出し元に例外が渡され、呼び出しリスト内の後続のメソッドは呼び出されません。  デリゲートに戻り値や out パラメーターがある場合、デリゲートは戻り値と最後に呼び出されたメソッドのパラメーターを返します。  呼び出しリストからメソッドを削除するには、デクリメント演算子またはデクリメント代入演算子 \('\-' または '\-\='\) を使用します。  次に例を示します。  
  
 [!code-cs[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 デリゲート型が `System.Delegate` から派生しているため、そのクラスで定義されるメソッドとプロパティはデリゲートで呼び出すことができます。  たとえば、デリゲートの呼び出しリスト内のメソッドの数を検索するには、次のように記述します。  
  
 [!code-cs[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 呼び出しリストに複数のメソッドがあるデリゲートは、`System.Delegate` のサブクラスである <xref:System.MulticastDelegate> から派生します。  上記のコードでは、両方のクラスが `GetInvocationList` をサポートしているため、いずれの場合も機能します。  
  
 マルチキャスト デリゲートは、イベント処理で広く使用されます。  イベント ソース オブジェクトはイベントを受け取るように登録されている受信者オブジェクトにイベント通知を送信します。  イベントを登録するには、受信者は、イベントを処理するようにデザインされたメソッドを作成し、そのメソッドのデリゲートを作成してイベント ソースにデリゲートを渡します。  イベントが発生すると、ソースがデリゲートを呼び出します。  デリゲートは、受信者のイベント処理メソッドを呼び出し、イベント データを配信します。  特定のイベントのデリゲート型は、イベント ソースによって定義されます。  詳細については、「[イベント](../../../csharp/programming-guide/events/index.md)」を参照してください。  
  
 コンパイル時に割り当てられた 2 つの異なる型のデリゲートを比較すると、コンパイル エラーが発生します。  デリゲート インスタンスが静的な `System.Delegate` 型の場合は、比較できますが、実行時に false が返されます。  次に例を示します。  
  
 [!code-cs[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [デリゲートの分散の使用](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)   
 [デリゲートの分散](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)   
 [Func および Action 汎用デリゲートでの分散の使用](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)   
 [イベント](../../../csharp/programming-guide/events/index.md)