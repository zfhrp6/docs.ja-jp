---
title: class (C# リファレンス)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 20968d2f72195db6d16de1b726c6e946b91ffcd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="class-c-reference"></a>class (C# リファレンス)

クラスは、次の例に示すように、キーワード `class` を使用して宣言します。

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a>コメント
C# では、単一継承のみを使用できます。 つまり、クラスは 1 つの基底クラスの実装だけを継承できます。 ただし、クラスは複数のインターフェイスを実装できます。 クラスの継承とインターフェイスの実装の例を次の表に示します。

|継承|例|
|-----------------|-------------|
|なし|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|なし。2 つのインターフェイスを実装|`class ImplClass: IFace1, IFace2 { }`|
|1 つ。1 つのインターフェイスを実装|`class ImplDerivedClass: BaseClass, IFace1 { }`|

名前空間内で直接宣言され、他のクラスに入れ子にされていないクラスは、[public](../../../csharp/language-reference/keywords/public.md) または [internal](../../../csharp/language-reference/keywords/internal.md) のいずれかです。 クラスは既定で `internal` です。

クラスのメンバー (入れ子にされているクラスも含む) は、[public](../../../csharp/language-reference/keywords/public.md)、`protected internal`、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[private](../../../csharp/language-reference/keywords/private.md)、`private protected` のいずれかとして宣言できます。 メンバーは既定で [private](../../../csharp/language-reference/keywords/private.md) です。

詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。

型パラメーターを持つジェネリック クラスを宣言することができます。 詳細については、「[ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)」を参照してください。

クラスには、次のメンバーの宣言を含めることができます。

- [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [定数](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [インデクサー](../../../csharp/programming-guide/indexers/index.md)

- [演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [イベント](../../../csharp/programming-guide/events/index.md)

- [デリゲート](../../../csharp/programming-guide/delegates/index.md)

- [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)

- [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a>例
ここでは、クラスのフィールド、コンストラクター、メソッドの宣言例を示します。 また、オブジェクト インスタンスの作成とインスタンス データの出力の例も示します。 次の例では、2 つのクラスが宣言されています。 最初の `Child` クラスには、2 つのプライベート フィールド (`name` と `age`)、2 つのパブリック コンストラクター、および 1 つのパブリック メソッドがあります。 2 番目のクラスである `StringTest` は、`Main`の格納に使用されます。

[!code-csharp[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]

## <a name="comments"></a>コメント
前の例で、プライベート フィールド (`name` および `age`) にアクセスできるのは、`Child` クラスのパブリック メソッドだけであることに注意してください。 たとえば、次のステートメントを使用して `Main` メソッドから子の名前を印刷することはできません。

```csharp
Console.Write(child1.name);   // Error
```

`Main` から `Child`のプライベート メンバーへのアクセスは、`Main` がそのクラスのメンバーである場合にのみ可能です。

アクセス修飾子を指定せずにクラス内で宣言された型は既定で `private` になります。そのため、キーワードが削除されてもこの例のデータ メンバーは `private` です。

最後に、既定のコンストラクターを使用して作成されたオブジェクト (`child3`) は、既定で年齢フィールドが 0 に初期化されることに注意してください。

## <a name="c-language-specification"></a>C# 言語仕様
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>参照
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)
