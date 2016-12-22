---
title: "ランタイムのジェネリック (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "ジェネリック [C#], 実行時"
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ランタイムのジェネリック (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック型またはジェネリック メソッドを Microsoft Intermediate Language \(MSIL\) にコンパイルすると、型パラメーターを持つと識別されるメタデータが組み込まれます。  ジェネリック型の MSIL の使用方法は、指定した型パラメーターが値型か参照型かによって異なります。  
  
 パラメーターとして値型を持つジェネリック型を初めて構築すると、ランタイムは指定したパラメーターが適切な位置で置換された特殊なジェネリック型を MSIL で作成します。  特殊なジェネリック型は、パラメーターとして使用される一意の値型ごとに、1 回作成されます。  
  
 たとえば、プログラミング コードで、次のように整数で構築されたスタックが宣言されているとします。  
  
 [!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 この時点で、ランタイムはパラメーターを整数に置き換えた特殊なバージョンの <xref:System.Collections.Generic.Stack%601> クラスを生成します。  これで、プログラミング コードで整数のスタックを使用すると、ランタイムでは、この生成された特殊な <xref:System.Collections.Generic.Stack%601> クラスが必ず再利用されるようになります。  次の例では、整数スタックの 2 つのインスタンスを作成し、これらのインスタンスが `Stack<int>` コードの単一のインスタンスを共有します。  
  
 [!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 一方、`long` などの異なる値型やユーザー定義の構造体をパラメーターとして持つ別の <xref:System.Collections.Generic.Stack%601> クラスがコードの別の箇所で作成されるとします。  その結果、ランタイムは別のバージョンのジェネリック型を生成し、MSIL で適切な位置にある `long` を置換します。  この特殊なジェネリック クラスにはそれぞれネイティブに値型が含まれるため、変換は必要ありません。  
  
 参照型の場合、ジェネリックの機能はやや異なります。  ジェネリック型を参照型で初めて構築すると、MSIL のパラメーターを置換するオブジェクト参照を持つ、特殊なジェネリック型がランタイムで作成されます。  次に、構築された型がパラメーターとして参照型でインスタンス化されるたびに、その型の種類にかかわらず、以前に作成した特殊なバージョンのジェネリック型がランタイムで再利用されます。  参照はいずれも同じサイズのため、このように処理されます。  
  
 たとえば、`Customer` クラスと `Order` クラスという 2 つの参照型があり、さらに `Customer` 型のスタックを作成したとします。  
  
 [!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 この時点で、データではなく、後で入力されるオブジェクト参照を格納した、特殊なバージョンの <xref:System.Collections.Generic.Stack%601> クラスがランタイムで生成されます。  次のコード行で、`Order` という別の参照型のスタックが作成されるとします。  
  
 [!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 値型とは異なり、`Order` 型用に特殊なバージョンの <xref:System.Collections.Generic.Stack%601> クラスは新たに作成されません。  代わりに、特殊なバージョンの <xref:System.Collections.Generic.Stack%601> クラスのインスタンスが作成され、`orders` 変数はそのインスタンスを参照するように設定されます。  このとき、`Customer` 型のスタックを作成するコード行があるとします。  
  
 [!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 前述した、`Order` 型を使用して作成された <xref:System.Collections.Generic.Stack%601> クラスを使用する場合と同様に、特殊な <xref:System.Collections.Generic.Stack%601> クラスのインスタンスが新たに作成されます。  インスタンスに含まれるポインターは、`Customer` 型のサイズを示すメモリ領域を参照するように設定されます。  参照型の数はプログラムによって大幅に異なるため、C\# のジェネリックの実装は、参照型のジェネリック クラスのためにコンパイラで作成される特殊なクラスの数を 1 つに減らし、コードの量を大幅に少なくします。  
  
 さらに、ジェネリック C\# クラスを値型パラメーターまたは参照型パラメーターを使用してインスタンス化する場合は、それに対してリフレクションが実行時にクエリを実行でき、実際の型と型パラメーターの両方を確認できます。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)