---
title: "アクセシビリティ レベル (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a>アクセシビリティ レベル (C# リファレンス)
以下に示したのは、メンバーに適用されるアクセシビリティ レベルの宣言です。[public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[private](../../../csharp/language-reference/keywords/private.md) の各アクセス修飾子を使用して指定します。  
  
|アクセシビリティの宣言|説明|  
|----------------------------|-------------|  
|`public`|アクセスは無制限です。|  
|`protected`|コンテナーであるクラスまたはそこから派生した型にアクセスが限定されます。|  
|`internal`|アクセスは現在のアセンブリに限定されます。|  
|`protected internal`|現在のアセンブリ、またはコンテナーであるクラスから派生した型にアクセスが限定されます。|  
|`private`|コンテナーである型にアクセスが限定されます。|  
|`private protected`|アクセスは、含んでいるクラスまたは現在のアセンブリ内の外側のクラスから派生した型に制限されます。|  
  
 1 つだけアクセス修飾子は使用メンバーまたは型、以外を使用するときに、`protected internal`または`private protected`の組み合わせ。  
  
 アクセス修飾子を名前空間に適用することはできません。 名前空間には、アクセス制限がありません。  
  
 メンバーが宣言されているコンテキストによっては、決まったアクセシビリティしか宣言できない場合があります。 メンバーの宣言にアクセス修飾子が指定されていない場合は、既定のアクセシビリティが使用されます。  
  
 トップレベルの型 (他の型に対して入れ子にされていない型) に指定できるアクセシビリティは `internal` と `public` だけです。 既定では、そのような型に `internal` のアクセシビリティが適用されます。  
  
 入れ子にされた型 (他の型のメンバーになっている型) には、次の表に示したアクセシビリティを宣言することができます。  
  
|コンテナー|メンバーの既定のアクセシビリティ|メンバーに対して宣言できるアクセシビリティ|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|なし|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|なし|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 入れ子にされた型のアクセシビリティは、その型の[アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)によって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。 ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ ドメイン](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
