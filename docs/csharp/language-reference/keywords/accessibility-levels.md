---
title: "アクセシビリティ レベル (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセス修飾子 [C#], アクセシビリティ レベル"
  - "アクセシビリティ レベル"
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# アクセシビリティ レベル (C# リファレンス)
アクセス修飾子 [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または [private](../../../csharp/language-reference/keywords/private.md) を使用して、メンバーに対する宣言済みのアクセシビリティ レベルとして以下のいずれか 1 つを指定できます。  
  
|宣言されたアクセシビリティ|説明|  
|-------------------|--------|  
|`public`|アクセスの制限はありません。|  
|`protected`|アクセスは、コンテナー クラス、またはコンテナー クラスから派生した型に制限されます。|  
|`internal`|アクセスは現在のアセンブリに制限されます。|  
|`protected` `internal`|現在のアセンブリ、またはコンテナー クラスから派生した型に制限されるアクセス|  
|`private`|アクセスはコンテナー型に制限されます。|  
  
 1 つのメンバーまたは型に対してアクセス修飾子を 1 つだけ指定できますが、`protected` `internal` の組み合わせは例外です。  
  
 アクセス修飾子は、名前空間では使用できません。  名前空間には、アクセス制限はありません。  
  
 メンバーの宣言が行われるコンテキストに応じて、特定の宣言されたアクセシビリティだけが許可されます。  メンバー宣言にアクセス修飾子の指定がない場合には、既定のアクセシビリティが使用されます。  
  
 他の型の中の入れ子になっていないトップ レベルの型は、`internal` または `public` のアクセシビリティだけを持つことができます。  このような型の既定のアクセシビリティは `internal` です。  
  
 他の型のメンバーである入れ子にされた型は、次の表に示すように、宣言されたアクセシビリティを持つことができます。  
  
|メンバーとして属する型|既定のメンバー アクセシビリティ|メンバーの許可される宣言されたアクセシビリティ|  
|-----------------|----------------------|-----------------------------|  
|`enum`|`public`|なし|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected` `internal`|  
|`interface`|`public`|なし|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 入れ子にされた型のアクセシビリティは、[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)に依存します。アクセシビリティ ドメインは、メンバーの宣言されたアクセシビリティと、すぐ上位のコンテナー型のアクセシビリティ ドメインによって決定されます。  ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)