---
title: "アクセシビリティ レベル (C# リファレンス)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
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
|`private protected`|現在のアセンブリ内の、コンテナーであるクラス、またはコンテナーであるクラスから派生した型にアクセスが制限されます。 C# 7.2 以降で使用可能です。 |  
  
 `protected internal` または `private protected` の組み合わせを使う場合を除き、1 つのメンバーまたは 1 つの型に指定できるアクセス修飾子は 1 つだけです。  
  
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
