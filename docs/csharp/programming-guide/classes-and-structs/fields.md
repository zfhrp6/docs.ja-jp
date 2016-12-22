---
title: "フィールド (C# プログラミング ガイド) | Microsoft Docs"
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
  - "フィールド [C#]"
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# フィールド (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

*フィールド*とは、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)で直接宣言される任意の型の変数です。  フィールドは、それを含んでいる型の*メンバー*です。  
  
 クラスや構造体には、インスタンス フィールドと静的フィールドのいずれかまたは両方が含まれていることがあります。  インスタンス フィールドは、型のインスタンスに固有になります。  たとえば、クラス T と、そのクラスのインスタンス フィールド F があるとします。型 T のオブジェクトを 2 つ作成した場合、他方のオブジェクトの値には影響を与えずに、各オブジェクトの F の値を変更できます。  これとは対照的に、クラス自体に属する静的フィールドは、そのクラスのすべてのインスタンスで共有されます。  インスタンス A に変更が加えられると、インスタンス B と C においても、それらのインスタンスがフィールドにアクセスした場合にすぐに確認できる形で反映されます。  
  
 通常、フィールドは、プライベートまたはプロテクトのアクセシビリティを持つ変数にのみ使用します。  クラスからクライアント コードに公開するデータは、[メソッド](../../../fsharp/language-reference/members/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、および[インデクサー](../../../csharp/programming-guide/indexers/index.md)を使用して提供する必要があります。  これらの構成要素を内部フィールドへの間接アクセスとして使用することで、無効な値が入力されることを防止できます。  パブリック プロパティによって公開されるデータを格納するプライベート フィールドは、*バッキング ストア*または*バッキング フィールド*と呼ばれます。  
  
 一般に、フィールドには、複数のクラス メソッドからアクセスできるようにする必要があり、かつ 1 つのメソッドの有効期間よりも長く保持する必要のあるフィールドを格納します。  たとえば、暦の日付を表すクラスには、月、日、年を表す 3 つの整数フィールドが存在します。  1 つのメソッドのスコープ外で使用されることのない変数は、メソッド本体の内部で*ローカル変数*として宣言する必要があります。  
  
 フィールドは、フィールドのアクセス レベル、フィールドの型、フィールドの名前を順に指定して、クラス ブロック内で宣言します。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 オブジェクト内のフィールドにアクセスするには、`objectname.fieldname` のように、オブジェクト名の後にピリオドを追加し、その後にフィールド名を続けます。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 フィールドには、フィールドの宣言時に代入演算子を使用して初期値を設定できます。  たとえば、`day` フィールドに自動的に `"Monday"` を代入するには、次の例のように `day` を宣言します。  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 フィールドは、オブジェクト インスタンスのコンストラクターが呼び出される直前に初期化されます。  コンストラクターがフィールドの値を代入すると、フィールドの宣言中に指定された値はすべて上書きされます。  詳細については、「[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)」を参照してください。  
  
> [!NOTE]
>  フィールド初期化子は、他のインスタンス フィールドを参照できません。  
  
 フィールドは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected internal` とマークできます。  これらのアクセス修飾子により、クラスのユーザーがフィールドにどのようにアクセスできるかが定義されます。  詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 フィールドは、[static](../../../csharp/language-reference/keywords/static.md) と宣言することもできます。  このように宣言すると、クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもフィールドにアクセスできます。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 フィールドは、[readonly](../../../csharp/language-reference/keywords/readonly.md) として宣言できます。  読み取り専用フィールドには、初期化時またはコンストラクターでしか値を代入できません。  `static` `readonly` フィールドは基本的に定数と同じですが、C\# コンパイラは、このフィールドの値にはコンパイル時にアクセスできず、実行時にしかアクセスできません。  詳細については、「[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)