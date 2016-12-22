---
title: "アクセサーのアクセシビリティの制限 (C# プログラミング ガイド) | Microsoft Docs"
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
  - "アクセサー [C#]"
  - "非対称アクセサーのアクセシビリティ [C#]"
  - "インデクサー [C#], 読み取り専用"
  - "プロパティ [C#], 読み取り専用"
  - "読み取り専用インデクサー [C#]"
  - "読み取り専用プロパティ [C#]"
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティやインデクサーの [get](../../../csharp/language-reference/keywords/get.md) および [set](../../../csharp/language-reference/keywords/set.md) の部分は、*アクセサー*と呼ばれます。  既定では、これらのアクセサーの参照範囲、つまりアクセス レベルは、それが属するプロパティまたはインデクサーのアクセス レベルと同じになります。  詳細については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」を参照してください。  ただし、これらのアクセサーのいずれかへのアクセスを制限すると便利な場合があります。  この場合は、通常、`set` アクセサーのアクセシビリティを制限し、`get` アクセサーはパブリックにアクセス可能にしておきます。  次に例を示します。  
  
 [!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 この例では、`Name` というプロパティが `get` アクセサーおよび `set` アクセサーを定義しています。  `get` アクセサーは、プロパティ自体のアクセシビリティ レベル \(この場合は `public`\) を受け取りますが、`set` アクセサーは、[protected](../../../csharp/language-reference/keywords/protected.md) アクセス修飾子をアクセサー自体に適用することにより、明示的に制限されています。  
  
## アクセス修飾子によるアクセサーの制限  
 プロパティやインデクサーでアクセス修飾子を使用する際には、以下の条件が適用されます。  
  
-   アクセス修飾子は、インターフェイスや明示的な[インターフェイス](../../../csharp/language-reference/keywords/interface.md) メンバー実装で使用できません。  
  
-   アクセス修飾子を使用できるのは、プロパティやインデクサーが `set` と `get` の両方のアクセサーを備えている場合に限られます。  この場合、修飾子は、これら 2 つのアクセスのうちの一方でのみ許可されます。  
  
-   プロパティやインデクサーに[オーバーライド](../../../csharp/language-reference/keywords/override.md)修飾子がある場合、アクセス修飾子は、オーバーライドされたアクセサーのアクセサーに一致する必要があります。  
  
-   アクセサーのアクセシビリティ レベルは、プロパティやインデクサー自体のアクセシビリティ レベルよりも制限する必要があります。  
  
## アクセサーのオーバーライド時のアクセス修飾子  
 プロパティやインデクサーをオーバーライドした場合、オーバーライドされたアクセサーは、オーバーライド側のコードにアクセスできる必要があります。  また、プロパティとインデクサーの両方のアクセシビリティ レベル、およびアクセサーのアクセシビリティ レベルは、オーバーライドされた、対応するプロパティとインデクサー、およびアクセサーに適合する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## インターフェイスの実装  
 アクセサーを使用してインターフェイスを実装するときは、アクセサーでアクセス修飾子を使用できません。  ただし、`get` などの 1 つのアクセサーを使用してインターフェイスを実装する場合は、次の例に示すように、もう 1 つのアクセサーでアクセス修飾子を使用できます。  
  
 [!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## アクセサーのアクセシビリティ ドメイン  
 アクセサーでアクセス修飾子を使用した場合は、この修飾子によって、アクセサーの[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)が決定されます。  
  
 アクセサーでアクセス修飾子を使用しない場合は、プロパティやインデクサーのアクセシビリティ レベルによって、アクセサーのアクセシビリティ ドメインが決定されます。  
  
## 使用例  
 次の例には、`BaseClass`、`DerivedClass`、`MainClass` の 3 つのクラスがあります。  `BaseClass` には `Name` と `Id` の 2 つのプロパティがあり、これらのプロパティは派生クラスにもあります。  この例は、[protected](../../../csharp/language-reference/keywords/protected.md) や [private](../../../csharp/language-reference/keywords/private.md) などの制限付きのアクセス修飾子を使用したときに、`DerivedClass` の `Id` プロパティを `BaseClass` の `Id` プロパティによってどのように隠ぺいできるかを示しています。  そのため、前者のプロパティに値を割り当てると、代わりに `BaseClass` クラスのプロパティが呼び出されます。  アクセス修飾子を [public](../../../csharp/language-reference/keywords/public.md) に置き換えると、このプロパティにアクセスできるようになります。  
  
 また、次の例は、`private` や `protected` などの制限付きのアクセス修飾子を、`DerivedClass` の `Name` プロパティの `set` アクセサーに指定すると、このアクセサーにアクセスできなくなり、このプロパティに値を割り当てると、エラーが生成されることも示しています。  
  
 [!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## コメント  
 宣言 `new private string Id` を `new public string Id` に置き換えると、次の出力が得られます。  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)