---
title: "アクセス修飾子 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセス修飾子 [C#], 概要"
  - "C# 言語, アクセス修飾子"
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# アクセス修飾子 (C# プログラミング ガイド)
すべての型および型のメンバーには、アセンブリ内の他のコードまたは他のアセンブリからそれらを使用できるかどうかを制御するアクセシビリティ レベルがあります。  型またはメンバーの宣言時に、次のいずれかのアクセス修飾子を使用してアクセシビリティを指定できます。  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。  
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 この型またはメンバーには、同じクラス内または同じ構造体内のコードのみがアクセスできます。  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 この型またはメンバーには、同じクラス、同じ構造体、またはこのクラスから派生したクラスにあるコードのみがアクセスできます。  
  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。  
  
 `protected internal`  
 この型またはメンバーには、型またはメンバーが宣言されているアセンブリ内の任意のコード、または他のアセンブリ内にある派生クラスからアクセスできます。  他のアセンブリからのアクセスは、protected internal 要素が宣言されたクラスから派生したクラスの宣言内で行われ、派生したクラス型のインスタンスにおいて実行される必要があります。  
  
 次の例は、型およびメンバーにアクセス修飾子を指定する方法を示しています。  
  
 [!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/access-modifiers_1.cs)]  
  
 すべてのコンテキスト内のすべての型またはメンバーで、すべてのアクセス修飾子を使用できるわけではありません。また、型のメンバーのアクセシビリティは、その包含型のアクセシビリティによって制限される場合があります。  以降のセクションでは、アクセシビリティについて詳しく説明します。  
  
## クラスと構造体のアクセシビリティ  
 名前空間内で直接宣言された \(つまり、他のクラスや構造体に入れ子にされていない\) クラスと構造体には、public または internal を指定できます。  アクセス修飾子が指定されていない場合は、internal が既定値です。  
  
 構造体のメンバー \(入れ子にされたクラスと構造体を含む\) は、public、internal、または private として宣言できます。  クラスのメンバー \(入れ子にされたクラスと構造体を含む\) は、public、protected internal、protected、internal、または private として宣言できます。  クラス メンバーと構造体メンバー \(入れ子にされたクラスと構造体も含む\) のアクセス レベルは、既定で private になります。  入れ子にされたプライベート型に包含型の外からアクセスすることはできません。  
  
 派生クラスのアクセシビリティをその基本型より高く設定することはできません。  つまり、内部クラス `A` からパブリック クラス `B` を派生させることはできません。  これが仮に許可されるとすると、派生クラスからは `A` のすべてのプロテクト メンバーまたは内部メンバーにアクセスできるため、結果として `A` がパブリックになります。  
  
 InternalsVisibleToAttribute を使用することで、他の特定のアセンブリから内部型へのアクセスを有効にできます。  詳細については、「[フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## クラス メンバーと構造体メンバーのアクセシビリティ  
 クラス メンバー \(入れ子にされたクラスと構造体を含む\) は、5 種類のうちのいずれかのアクセス修飾子を使って宣言できます。  構造体は継承をサポートしていないため、構造体のメンバーを protected として宣言することはできません。  
  
 通常、メンバーのアクセシビリティは、そのメンバーを包含している型のアクセシビリティより高くは設定できません。  ただし、内部クラスのパブリック メンバーは、メンバーがインターフェイス メソッドを実装している場合、またはパブリックな基本クラスで定義されている仮想メソッドをオーバーライドしている場合、アセンブリの外部からアクセスできることがあります。  
  
 フィールド、プロパティ、またはイベントである任意のメンバーの型は、少なくともメンバー自身と同程度にアクセス可能である必要があります。  同様に、メソッド、インデクサー、またはデリゲートである任意のメンバーの戻り値の型とパラメーターの型は、少なくともメンバー自身と同程度にアクセス可能である必要があります。  たとえば、クラス `C` を返すメソッド `M` は、`C` もパブリックでない限り、パブリック メソッドにすることはできません。  同様に、型 `A` が private として宣言されている場合、`A` のプロテクト プロパティを使用することはできません。  
  
 ユーザー定義の演算子は、常に public として宣言する必要があります。  詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
 デストラクターではアクセシビリティ修飾子を使用できません。  
  
 クラス メンバーまたは構造体メンバーのアクセス レベルを設定するには、次の例に示すように、適切なキーワードをメンバー宣言に追加します。  
  
 [!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  protected internal というアクセシビリティ レベルは、protected または internal であることを意味しており、protected かつ internal という意味ではありません。  つまり、protected internal メンバーには、派生クラスを含めて同じアセンブリ内のどのクラスからもアクセスできます。  アクセシビリティを同じアセンブリ内の派生クラスだけに限定するには、クラス自体を internal と宣言し、そのメンバーを protected と宣言します。  
  
## その他の型  
 名前空間内で直接宣言されたインターフェイスは、public または internal として宣言できます。クラスや構造体と同様に、インターフェイスには既定で internal のアクセス レベルが指定されます。  インターフェイスの目的は他の型からクラスや構造体にアクセスできるようにすることであるため、インターフェイス メンバーは常に public です。  インターフェイス メンバーにはアクセス修飾子を適用できません。  
  
 列挙型メンバーは常に public になり、アクセス修飾子を適用できません。  
  
 デリゲートは、クラスや構造体と同様の動作を行います。  既定では、デリゲートは名前空間内で直接宣言されると internal、入れ子にされると private のアクセス レベルになります。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [クラス](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)