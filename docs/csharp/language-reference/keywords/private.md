---
title: "private (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "private_CSharpKeyword"
  - "private"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "private キーワード [C#]"
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# private (C# リファレンス)
`private` キーワードは、メンバー アクセス修飾子です。  プライベートなアクセスは、許容度が最も低いアクセス レベルです。  この例に示すように、プライベートなメンバーには、クラスの本体内か、メンバーが宣言されている構造体の内部でだけアクセス可能です。  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 同じ本体にある入れ子になったクラスも、プライベートなメンバーにアクセスできます。  
  
 プライベートなメンバーへの参照を、クラスの外側や、メンバーが宣言されているクラスの外側から行った場合は、コンパイル エラーになります。  
  
 `private` と他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」および「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
## 使用例  
 この例では、`Employee` クラスに `name` および `salary` という 2 つのプライベート データ メンバーが含まれています。  これらのメンバーは、プライベート メンバーであり、メンバー メソッド以外からはアクセスできません。  `GetName` および `Salary` というパブリック メソッドが追加され、プライベート メンバーへの制御されたアクセスを許可します。  `name` メンバーはパブリック メソッドを介してアクセスされ、`salary` メンバーはパブリックな読み取り専用プロパティを介してアクセスされます。  詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)