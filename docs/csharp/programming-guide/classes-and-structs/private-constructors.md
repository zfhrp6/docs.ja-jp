---
title: "プライベート コンストラクター (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f63f4a2189848f8d12ae09eab215c7e15a57863
ms.lasthandoff: 03/13/2017

---
# <a name="private-constructors-c-programming-guide"></a>プライベート コンストラクター (C# プログラミング ガイド)
プライベート コンストラクターは、特別なインスタンス コンストラクターです。 通常は、静的メンバーだけを含むクラスで使用されます。 クラスに 1 つ以上のプライベート コンストラクターがあり、パブリック コンストラクターがない場合、他のクラス (入れ子になったクラスを除く) は、このクラスのインスタンスを作成できません。 例:  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 空のコンストラクターを宣言すると、既定コンストラクターの自動生成は行われません。 コンストラクターにアクセス修飾子を指定しない場合でも、コンストラクターは既定でプライベートになります。 しかし、通常は、[プライベート](../../../csharp/language-reference/keywords/private.md)修飾子を明示的に使用して、クラスをインスタンス化できないことを明確に示します。  
  
 プライベート コンストラクターは、<xref:System.Math> クラスなどのインスタンス フィールドやメソッドが存在しない場合や、クラスのインスタンスを取得するためにメソッドが呼び出される場合に、クラスのインスタンスが作成されないようにするために使用します。 クラス内のすべてのメソッドが静的な場合は、クラス全体を静的にすることを検討してください。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
## <a name="example"></a>例  
 次に示すのは、プライベート コンストラクターを使用するクラスの例です。  
  
 [!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 この例で、次のステートメントをコメント解除すると、保護レベルのためにコンストラクターにアクセスできなくなり、エラーが発生します。  
  
 [!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)
