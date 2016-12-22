---
title: "方法 : 抽象プロパティを定義する (C# プログラミング ガイド) | Microsoft Docs"
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
  - "抽象プロパティ [C#]"
  - "プロパティ [C#], abstract"
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 抽象プロパティを定義する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の例では、[抽象](../../../csharp/language-reference/keywords/abstract.md)プロパティの定義方法を示します。  抽象プロパティの宣言では、プロパティ アクセサーは実装されません。クラスがプロパティをサポートしていることは宣言しますが、アクセサーの実装は派生クラスに委ねます。  基本クラスから継承された抽象プロパティを実装する方法を次の例に示します。  
  
 この例は、次の 3 つのファイルで構成されています。各ファイルは個別にコンパイルされ、生成されたアセンブリが次のコンパイルによって参照されます。  
  
-   abstractshape.cs: `Area` 抽象プロパティを含む `Shape` クラス。  
  
-   shapes.cs: `Shape` クラスのサブクラス。  
  
-   shapetest.cs: `Shape` から派生したオブジェクトの面積を表示するテスト プログラム。  
  
 この例をコンパイルするには、次のコマンドを入力します。  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 これで、実行可能ファイル shapetest.exe が作成されます。  
  
## 使用例  
 このファイルは、`double` 型の `Area` プロパティを持つ `Shape` クラスを宣言します。  
  
 [!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   プロパティの修飾子は、プロパティ宣言自体に設定されます。  次に例を示します。  
  
    ```  
    public abstract double Area  
    ```  
  
-   抽象プロパティ \(例では `Area`\) を宣言するときは、使用できるプロパティ アクセサーを指示するだけで、実装はしません。  この例では、[get](../../../csharp/language-reference/keywords/get.md) アクセサーだけが有効なため、プロパティは読み取り専用です。  
  
## 使用例  
 次のコードは、`Shape` の 3 種類のサブクラスと、それらがどのように `Area` プロパティをオーバーライドして独自の実装を提供するかを示しています。  
  
 [!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## 使用例  
 次のコードは、`Shape` から派生するオブジェクトを作成し、それらの面積を出力するテスト プログラムを示しています。  
  
 [!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [方法: コマンド ラインを使用してアセンブリを作成および使用する](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)