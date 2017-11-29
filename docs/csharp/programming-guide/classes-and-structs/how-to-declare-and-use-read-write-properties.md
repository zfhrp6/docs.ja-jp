---
title: "方法: 読み取り/書き込みのプロパティの宣言と使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>方法: 読み取り/書き込みのプロパティの宣言と使用 (C# プログラミング ガイド)
プロパティは、オブジェクトのデータへの保護されていない、制御されず未確認のアクセスに伴うリスクなしにパブリック データ メンバーの利便性を提供します。 これは*アクセサー*を通じて行われます。アクセサーは、基になるデータ メンバーの値を割り当てたり、取得したりする特殊なメソッドです。 [set](../../../csharp/language-reference/keywords/set.md) アクセサーはデータ メンバーの割り当てを可能にし、[get](../../../csharp/language-reference/keywords/get.md) アクセサーはデータ メンバーの値を取得します。  
  
 このサンプルでは、`Name` (string) および `Age` (int) という 2 つのプロパティを持つ `Person` クラスを示します。 両方のプロパティは `get` および `set` アクセサーを提供するため、読み取り/書き込みプロパティと見なされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 前述の例では、`Name` および `Age` プロパティは[パブリック](../../../csharp/language-reference/keywords/public.md)であり、`get` および `set` アクセサーの両方が含まれます。 そのため、任意のオブジェクトがこれらのプロパティを読み書きできます。 ただし、アクセサーのいずれかを除外することが望ましい場合もあります。 たとえば、次のように `set` アクセサーを省略すると、プロパティが読み取り専用になります。  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 また、一方のアクセサーをパブリックに公開し、もう一方を private または protected にすることもできます。 詳細については、「[アクセサーのアクセシビリティの制限 (C# プログラミング ガイド)](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。  
  
 プロパティを宣言すると、プロパティをクラスのフィールドのように使用できます。 そのため、プロパティ値の取得と設定の両方で、次のように自然な構文を使用できます。  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 プロパティの `set` メソッドでは、特殊な `value` 変数を使用できることに注意してください。 この変数には、ユーザーが指定した値が含まれます。たとえば、次のように指定します。  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 `Person` オブジェクトの `Age` プロパティの値を増分する場合は、次のような簡潔な構文を使用します。  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 `set` メソッドと `get` メソッドがそれぞれ使用されてプロパティがモデル化されている場合、上記と同じ内容のコードは次のようになります。  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 この例では、`ToString` メソッドが次のようにオーバーライドされます。  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 プログラムでは `ToString` が明示的に使用されないことに注意してください。 既定では、`WriteLine` 呼び出しによって呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)
