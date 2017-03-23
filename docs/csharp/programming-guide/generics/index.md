---
title: "ジェネリック (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, ジェネリック"
  - "ジェネリック [C#]"
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# ジェネリック (C# プログラミング ガイド)
ジェネリックは、C\# 言語と共通言語ランタイム \(CLR: Common Language Runtime\) の Version 2.0 に追加されたものです。  ジェネリックは、.NET Framework に型パラメーターという概念を導入します。型パラメーターを使用すると、クラスやメソッドがクライアント コードで宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスとメソッドを設計できます。  たとえば、ジェネリック型パラメーター T を使用すると、次に示すようにランタイムのキャストやボックス化操作のコストやリスクを負わずに他のクライアント コードで使用できる単一のクラスを記述できます。  
  
 [!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## ジェネリックの概要  
  
-   ジェネリック型は、コードの再利用性、タイプ セーフ性、およびパフォーマンスを最大化するために使用します。  
  
-   ジェネリックの最も一般的な用途は、コレクション クラスの作成です。  
  
-   .NET Framework クラス ライブラリには、複数の新しいジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。  これらのクラスは、<xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限り使用してください。  
  
-   独自のジェネリック インターフェイス、クラス、メソッド、イベント、およびデリゲートを作成できます。  
  
-   ジェネリック クラスは、特定のデータ型のメソッドのみへのアクセスを許可するように制約できます。  
  
-   ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。  
  
## 関連項目  
 詳細情報  
  
-   [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [ジェネリックの利点](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [ジェネリック型の型パラメーター](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [default キーワード](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md)  
  
-   [C\+\+ テンプレートと C\# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [.NET Framework クラス ライブラリのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## C\# 言語仕様  
 詳細については、「[C\# 言語仕様](../../../csharp/language-reference/language-specification.md)」を参照してください。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)   
 [\<typeparamref\>](../../../csharp/programming-guide/xmldoc/typeparamref.md)