---
title: "ジェネリック クラス (C# プログラミング ガイド) | Microsoft Docs"
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
  - "C# 言語, ジェネリック クラス"
  - "ジェネリック [C#], クラス"
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ジェネリック クラス (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック クラスは、特定のデータ型に固有ではない操作をカプセル化します。  一般に、ジェネリック クラスは、リンクされたリスト、ハッシュ テーブル、スタック、キュー、ツリーなどのコレクションと共に使用されます。  コレクション内の項目の追加や削除などの操作は、格納されるデータ型にかかわらず、基本的に同じ方法で実行されます。  
  
 コレクション クラスが必要な場合、一般に、.NET Framework クラス ライブラリに用意されているものを使用することをお勧めします。  これらのクラスの使用方法の詳細については、「[.NET Framework クラス ライブラリのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)」を参照してください。  
  
 通常、ジェネリック クラスを作成するには、既存の具象クラスから始め、生成と使いやすさが最適なバランスになるまで、1 つずつ、型を型パラメーターに変更します。  独自にジェネリック クラスを作成する場合は、次の点を考慮する必要があります。  
  
-   型パラメーターに一般化する型。  
  
     一般に、パラメーター化できる型が増えると、コードの柔軟性と再利用できる度合いが向上します。  ただし、一般化しすぎると、他の開発者が読んだり理解したりするのが困難なコードになります。  
  
-   型パラメーターに適用する制約 \(存在する場合\) の内容 \(「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください\)。  
  
     望ましい規則は、必要に応じて型を処理できる範囲で、最大の制約を適用することです。  たとえば、参照型でのみジェネリック クラスを使用することがわかっていれば、そのクラスの制約を適用します。  こうすることで、値型でクラスを使うという意図しない用法を回避できます。また、`T` で `as` 演算子を使用し、null 値をチェックできるようになります。  
  
-   ジェネリックの動作を基本クラスとサブクラスにファクタリングするかどうか。  
  
     ジェネリック クラスは基本クラスとして機能するため、非ジェネリック クラスと同様なデザインの考慮事項が適用されます。  ジェネリックな基本クラスからの継承に関する規則については、後述します。  
  
-   1 つ以上のジェネリック インターフェイスを実装するかどうか。  
  
     たとえば、ジェネリック ベースのコレクションに項目を作成するときに使用するクラスを設計している場合、`T` がそのクラスの型である <xref:System.IComparable%601> などのインターフェイスの実装が必要になることがあります。  
  
 単純なジェネリック クラスの例については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。  
  
 型パラメーターの規則と制約には、ジェネリック クラスの動作 \(特に、継承とメンバーのアクセシビリティ\) について、暗示的な意味合いがあります。  次に進む前に、いくつかの用語を理解しておく必要があります。  ジェネリック クラスで、`Node<T>,` クライアント コードでクラスを参照するには、型の引数を指定してクローズ構築型 \(`Node<int>`\) を作成します。  または、たとえばジェネリックな基本クラスを指定するときに型パラメーターを指定せずに、オープン構築型 \(`Node<T>`\) を作成します。  ジェネリック クラスは、具象、クローズ構築、またはオープン構築の各基本クラスから継承できます。  
  
 [!code-cs[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 非ジェネリック クラス \(つまり具象クラス\) は、クローズ構築の基本クラスからは継承できますが、オープン構築のクラスや型パラメーターからは継承できません。実行時に、クライアント コードから基本クラスをインスタンス化するときに必要な型の引数を提示する方法がないためです。  
  
 [!code-cs[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 オープン構築型から継承するジェネリック クラスの場合、継承するクラスで共有されない基本クラスの型パラメーターに対して、型の引数を提示する必要があります。次にコード例を示します。  
  
 [!code-cs[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 オープン構築型から継承するジェネリック クラスでは、基本型に対する制約のスーパーセットである制約、または基本型に対する制約を暗示する制約を指定する必要があります。  
  
 [!code-cs[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 ジェネリック型では、次のように複数の型パラメーターと制約を使用できます。  
  
 [!code-cs[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 オープン構築型とクローズ構築j型は、メソッドのパラメーターとして使用できます。  
  
 [!code-cs[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 ジェネリック クラスがインターフェイスを実装する場合、そのクラスのすべてのインスタンスをそのインターフェイスにキャストできます。  
  
 ジェネリック クラスは不変です。  つまり、入力パラメーターで `List<BaseClass>` を使用していて、`List<DerivedClass>` を提示しようとすると、コンパイル時にエラーが発生します。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Saving the State of Enumerators \(列挙子の状態を保存する\)](http://go.microsoft.com/fwlink/?LinkId=112390)   
 [An Inheritance Puzzle, Part One \(継承パズル、パート 1\)](http://go.microsoft.com/fwlink/?LinkId=112380)