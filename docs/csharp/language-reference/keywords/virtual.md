---
title: virtual (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 5a188e9a7cbb7a1c497d577039c2b2578eaa7526
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="virtual-c-reference"></a>virtual (C# リファレンス)
`virtual` キーワードは、メソッド、プロパティ、インデクサー、またはイベント宣言を変更し、それを派生クラスでオーバーライドできるようにするために使用されます。 たとえば、次のメソッドはそれを継承する任意のクラスでオーバーライドできます。  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 仮想メンバーの実装は、派生クラスの[オーバーライド メンバー](../../../csharp/language-reference/keywords/override.md)によって変更できます。 `virtual` キーワードの使い方について詳しくは、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。  
  
## <a name="remarks"></a>コメント  
 仮想メソッドが呼び出されると、オブジェクトの実行時の型が、オーバーライドするメンバーに対してチェックされます。 いずれの派生クラスもメンバーをオーバーライドしなかった場合は、最派生クラスのオーバーライド メンバー (元のメンバーである可能性があります) が呼び出されます。  
  
 既定では、メソッドは仮想ではありません。 非仮想メソッドをオーバーライドすることはできません。  
  
 `virtual` 修飾子を、`static`、`abstract`、`private`、`override` 修飾子と共に使用することはできません。 次のコードは、仮想のプロパティの例です。  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 仮想プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。  
  
-   `virtual` 修飾子を静的プロパティに対して使うのは誤りです。  
  
-   継承する仮想プロパティは、派生クラス内で `override` 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。  
  
## <a name="example"></a>例  
 この例では、`Shape` クラスに 2 つの座標 (`x` と `y`) と仮想メソッド `Area()` が含まれています。 他の図形クラス (`Circle`、 `Cylinder`、`Sphere` など) は `Shape` クラスを継承しており、各図の表面積が計算されています。 各派生クラスは、`Area()` のオーバーライド実装を独自に持っています。  
  
 次の宣言に示すように、継承されたクラス (`Circle`、 `Sphere`、および `Cylinder`) はいずれも、基底クラスを初期化するコンス トラクターを使用します。  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 次のプログラムは、メソッドに関連付けられたオブジェクトに従って `Area()` メソッドの適切な実装を呼び出すことにより、各図形の面積を計算し、表示します。  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [new](../../../csharp/language-reference/keywords/new.md)
