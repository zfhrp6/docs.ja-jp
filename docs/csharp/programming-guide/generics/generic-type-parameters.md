---
title: "ジェネリック型の型パラメーター (C# プログラミング ガイド) | Microsoft Docs"
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
  - "ジェネリック [C#], 型パラメーター"
  - "型パラメーター [C#]"
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ジェネリック型の型パラメーター (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ジェネリック型またはジェネリック メソッドの定義では、型パラメーターは、ジェネリック型の変数をインスタンス化するときにクライアントが指定する、特定の型のプレースホルダーです。  「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」に紹介されている `GenericList<T>` などのジェネリック クラスは、実際のところ型ではなく、型の設計図のようなものなので、そのままでは使用できません。  `GenericList<T>` を使用するには、クライアント コードで、山かっこ内に型の引数を指定して構築型を宣言し、インスタンス化する必要があります。  この特定クラスの型の引数には、コンパイラで認識される任意の型を使用できます。  構築型のインスタンスはいくつでも作成できます。また、それぞれに対して、次のように異なる型の引数を使用できます。  
  
 [!code-cs[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 この `GenericList<T>` の各インスタンスでは、クラスで `T` が発生すると、実行時に型の引数で置換されます。  この置換を利用して、単一のクラス定義を使用したタイプ セーフで効率的なオブジェクトを 3 つ作成しました。  この置換を CLR で実行する方法の詳細については、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
## 型パラメーターの名前付けのガイドライン  
  
-   1 文字の名前だけで理解でき、追加の文字が必要ない場合を除き、ジェネリック型の型パラメーターには、わかりやすい名前を付けます。  
  
     [!code-cs[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   1 文字の型パラメーターを持つ型である場合、型パラメーター名として T を使用することを検討します。  
  
     [!code-cs[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   わかりやすい型パラメーター名の前に "T" を付けます。  
  
     [!code-cs[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   パラメーターの名前に型パラメーターに関する制約を指定することを検討します。  たとえば、`ISession` に制約されるパラメーターである場合、`TSession` と指定します。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\+\+ テンプレートと C\# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)