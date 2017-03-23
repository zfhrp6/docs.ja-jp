---
title: "方法 : カスタム拡張メソッドを実装して呼び出す (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "拡張メソッド [C#], 実装と呼び出し"
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法 : カスタム拡張メソッドを実装して呼び出す (C# プログラミング ガイド)
ここではの独自の拡張メソッドを実装する方法には拡張 [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=217856) する .NET のまたはそのほかの種類を示します。  クライアント コードで拡張メソッドを使用するには、拡張メソッドが格納されている DLL への参照を追加し、さらに、拡張メソッドが定義されている名前空間を指定する [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブを追加します。  
  
### 拡張メソッドを呼び出すには定義  
  
1.  拡張メソッドを格納するための静的[クラス](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)を定義します。  
  
     このクラスは、クライアント コードから参照できる必要があります。  アクセシビリティの規則の詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
2.  拡張メソッドを静的メソッドとして実装します。メソッドの可視性は、包含クラスと同レベル以上を指定します。  
  
3.  メソッドの最初のパラメーターでは、メソッドが操作する型を指定します。型名の前には [this](../../../csharp/language-reference/keywords/this.md) 修飾子を付加します。  
  
4.  呼び出し元のコードで、`using` ディレクティブを追加して、拡張メソッドのクラスを含む[名前空間](../../../csharp/language-reference/keywords/namespace.md)を指定します。  
  
5.  型のインスタンス メソッドと同じようにメソッドを呼び出します。  
  
     呼び出し元のコードでは最初のパラメーターを指定しません。これは、演算子を適用する型を表すものであり、コンパイラはオブジェクトの型を既に認識しているためです。  指定する必要があるのは、2 番目から `n` 番目のパラメーターの引数だけです。  
  
## 使用例  
 `CustomExtensions.StringExtension` クラスの `WordCount` という名前の拡張メソッドを実装する方法を次の例に示します。  このメソッドは、最初のメソッド パラメーターとして指定された <xref:System.String> クラスを操作します。  `CustomExtensions` 名前空間がアプリケーションの名前空間にインポートされ、メソッドが `Main` メソッド内で呼び出されます。  
  
 [!code-cs[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## コードのコンパイル  
 このコードを実行するには、[!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] で作成した Visual C\# コンソール アプリケーション プロジェクトに、コードをコピーして貼り付けます。  既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。  これらの要件が 1 つ以上プロジェクトから欠落していても、手動で追加できます。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## .NET Framework セキュリティ  
 拡張メソッドには、固有のセキュリティ上の脆弱性はありません。  名前の衝突の解決では、型自体で定義されているインスタンス メソッドまたは静的メソッドが常に優先されるため、型の既存のメソッドを偽装するために拡張メソッドが使用されることはありません。  拡張メソッドは、拡張されたクラスのプライベート データにはアクセスできません。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [this](../../../csharp/language-reference/keywords/this.md)   
 [namespace](../../../csharp/language-reference/keywords/namespace.md)