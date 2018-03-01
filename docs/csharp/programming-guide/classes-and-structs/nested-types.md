---
title: "入れ子にされた型 (C# プログラミング ガイド)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a>入れ子にされた型 (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md)や[構造体](../../../csharp/language-reference/keywords/struct.md)の中で定義された型は、入れ子にされた型と呼ばれます。 例:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
外側の型がクラスまたは構造体のいずれであっても、入れ子にされた型は既定で [private](../../../csharp/language-reference/keywords/private.md) になります。これらにはその包含する型からのみアクセスできます。 前の例では、`Nested` クラスは外部の型にアクセスできません。 

次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。

- 入れ子にされた型の**クラス**できます[パブリック](../../../csharp/language-reference/keywords/public.md)、[保護](../../../csharp/language-reference/keywords/protected.md)、[内部](../../../csharp/language-reference/keywords/internal.md)、[内部保護](../../../csharp/language-reference/keywords/protected-internal.md)、[プライベート](../../../csharp/language-reference/keywords/private.md)または[保護されたプライベート](../../../csharp/language-reference/keywords/private-protected.md)です。 

   ただし、定義、 `protected`、`protected internal`または`private protected`内のクラスを入れ子になった、[クラスをシール](../../language-reference/keywords/sealed.md)コンパイラの警告が生成されます[CS0628](../../misc/cs0628.md)、「新規のプロテクト メンバーはシール クラスで宣言されています」。
  
- **構造体**の入れ子にされた型は、は、[public](../../../csharp/language-reference/keywords/public.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または [private](../../../csharp/language-reference/keywords/private.md) のいずれかが可能です。
  
次の例では、`Nested` クラスを public にします。
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。 包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。 例:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。 入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。  
  
 上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。 これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)
