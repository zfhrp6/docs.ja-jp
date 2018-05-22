---
title: private (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 26eab2912923c9fcae1ce930bd5b59a2740d500e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="private-c-reference"></a>private (C# リファレンス)
`private` キーワードはメンバー アクセス修飾子です。 
   
 > このページでは、`private` アクセスについて説明します。 `private` キーワードも [`private protected`](./private-protected.md) アクセス修飾子に含まれます。
  
プライベート アクセスは、最も制限の多いアクセス レベルです。 次の例に示すように、プライベート メンバーは、宣言されているクラスまたは構造体の本体内でのみアクセスできます。  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 同じ本体にある入れ子にされた型も、プライベート メンバーにアクセスできます。  
  
 プライベート メンバーへの参照を、クラスの外側やメンバーが宣言されているクラスの外側から行った場合は、コンパイル時のエラーが発生します。  
  
 `private` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」と「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`Employee` クラスに `name` と `salary` という 2 つのプライベート データ メンバーが含まれています。 これらのメンバーは、プライベート メンバーであり、メンバー メソッド以外からはアクセスできません。 `GetName` と `Salary` というパブリック メソッドが追加されており、プライベート メンバーへの制御されたアクセスが許可されています。 `name` メンバーはパブリック メソッドを通してアクセスされ、`salary` メンバーはパブリックな読み取り専用プロパティを通してアクセスされます (詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください)。  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
