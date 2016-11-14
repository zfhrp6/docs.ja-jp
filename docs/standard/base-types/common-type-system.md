---
title: "共通型システムの詳細"
description: "共通型システムの詳細"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 7d7f869b07d7cf00ffa69da117aa199d1b6e8f20

---

# <a name="common-type-system-in-depth"></a>共通型システムの詳細

このトピックには、共通型システムの詳細を説明する次のセクションが含まれています。

* [.NET の型](#types-in-net)

* [型定義](#type-definitions)

* [型のメンバー](#type-members)

* [型のメンバーの特性](#characteristics-of-type-members)


## <a name="types-in-net"></a>.NET の型

.NET に存在するすべての型は、値型と参照型のどちらかに区別されます。 

値型は、オブジェクトがその実際の値で表されるデータ型です。 変数に値型のインスタンスが割り当てられると、その変数には値の新しいコピーが代入されます。

参照型は、オブジェクトがその実際の値を指す参照 (ポインターのようなもの) によって表されるデータ型です。 参照型が変数に割り当てられている場合、その変数は元の値を参照します (つまり、元の値を指します)。 コピーは作成されません。 

.NET の共通型システムは、次の 5 つの型のカテゴリをサポートしています。

* [クラス](#classes)

* [構造体](#structures)

* [列挙型](#enumerations)

* [インターフェイス](#interfaces)

* [デリゲート](#delegates)

### <a name="classes"></a>クラス

クラスは参照型であり、他のクラスから直接派生させることも、[System.Object](xref:System.Object) から暗黙的に派生させることもできます。 クラスは、オブジェクト (クラスのインスタンス) が実行できる操作 (メソッド、イベント、またはプロパティ) およびオブジェクトが保持するデータ (フィールド) を定義するものです。 通常、クラスは、たとえば定義のみを持ち実装は持たないインターフェイスとは対照的に、定義と実装の両方を持ちます。しかし、実装を持たないメンバーが 1 つ以上存在するクラスもあります。

クラスが持つことのできる特性のいくつかを次の表で説明します。 ランタイムをサポートする言語にはそれぞれ、クラスまたはクラス メンバーに対し、こうした特性の 1 つ以上を指定する手段が用意されています。 ただし、.NET を対象とするすべてのプログラミング言語で、これらすべての特性を利用できるわけではありません。

特徴 | 説明
-------------- | -----------
sealed | 型から別のクラスを派生できないことを示します。
実装 | クラスが、インターフェイスのメンバーの実装を提供することによって、1 つ以上のインターフェイスを使用することを示します。
abstract | クラスをインスタンス化できないことを示します。 クラスを使用するには、このクラスから別のクラスを派生させる必要があります。
継承 | クラスのインスタンスを、基底クラスが指定されている任意の場所で使用できることを示します。 基底クラスから継承する派生クラスは、基底クラスによって提供されるすべてのパブリック メンバーの実装を使用できます。または、派生クラスは、パブリック メンバーの実装をその独自の実装でオーバーライドできます。
exported または not exported | クラスが定義されているアセンブリの外部から、そのクラスを参照できるかどうかを示します。 この特性は、最上位のクラスにのみ適用され、入れ子にされたクラスには適用されません。

> [!NOTE]
> クラスは、親クラスまたは構造体で入れ子にすることもできます。 入れ子にされたクラスにも、メンバー特性を適用できます。 詳細については、「[入れ子にされた型](#nested-types)」を参照してください。

実装を持たないクラス メンバーは抽象メンバーです。 1 つ以上の抽象メンバーを持つクラスは、それ自体が抽象クラスとなり、新しいインスタンスを作成できません。 ランタイムに対応する言語の中には、抽象メンバーを持たないクラスも抽象クラスとしてマークできるものがあります。 抽象クラスは、派生クラスが必要に応じて継承したりオーバーライドしたりできる基本的な一連の機能をカプセル化する必要がある場合に使用できます。 抽象クラスでないクラスを具象クラスと呼びます。

クラスで実装できるインターフェイスの数に制限はありませんが、すべてのクラスが暗黙的に継承する [System.Object](xref:System.Object) を除き、継承できる基底クラスは 1 つだけです。 すべてのクラスには少なくとも 1 つのコンストラクターが必要で、このコンストラクターにより、各クラスの新しいインスタンスが初期化されます。 コンストラクターを明示的に定義しなかった場合、ほとんどのコンパイラでは、自動的に既定の (パラメーターなしの) コンストラクターが使用されます。

### <a name="structures"></a>構造体

構造体は、[System.Object](xref:System.Object) から派生する [System.ValueType](xref:System.ValueType) から暗黙的に派生する値型です。 構造体は、メモリ要件が小さい値を表す場合や、厳密に型指定されたパラメーターを持つメソッドに対してパラメーターを値渡しする場合などに、非常に便利です。 .NET では、すべてのプリミティブ データ型 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)) が構造体として定義されています。

クラスと同様、構造体にもデータ (構造体のフィールド) と、そのデータに対して実行できる操作 (構造体のメソッド) が定義されます。 これは、[System.Object](xref:System.Object) クラスと [System.ValueType](xref:System.ValueType) クラスで定義されている仮想メソッドなどのメソッドと、値型そのものに定義されているすべてのメソッドを、構造体に対して呼び出すことができることを意味します。 言い換えれば、構造体には、静的メソッドと非静的メソッドに加え、フィールド、プロパティ、およびイベントを持たせることができます。 構造体のインスタンスを作成したり、構造体をパラメーターとして渡したりできるほか、構造体をローカル変数として格納することも、別の値型または参照型のフィールドに格納することもできます。 構造体でインターフェイスを実装することもできます。

ただし、値型は、いくつかの点でクラスとは異なります。 まず、値型は [System.ValueType](xref:System.ValueType) を暗黙的に継承しますが、他の型を直接継承することはできません。 同様に、すべての値型には、値型から他の型が派生できないことを示す sealed 属性が適用されます。 また、値型はコンストラクターを必要としません。

共通言語ランタイムは、それぞれの値型に対応するボックス化された型を提供します。ボックス化された型とは、値型と同じ状態および動作を備えたクラスのことです。 値型のインスタンスは、[System.Object](xref:System.Object) 型のパラメーターを受け入れるメソッドに渡されると、ボックス化されます。 参照渡しのパラメーターとして値型を受け入れるメソッドの呼び出しから制御が返されると、ボックス化が解除 (つまり、クラスのインスタンスから値型のインスタンスに変換) されます。 言語によっては、ボックス化された型が必要なときに特別な構文を使用する必要がありますが、ボックス化された型を必要に応じて自動的に使用する言語もあります。 値型を定義するときには、ボックス化された型とボックス化解除された型の両方を定義します。

### <a name="enumerations"></a>列挙体

列挙型 (enum) は、[System.Enum](xref:System.Enum) から直接継承される値型で、基になるプリミティブ型の値に対して別名を割り当てます。 列挙型には名前、基になる型、および一連のフィールドが存在します。基になる型は、組み込みの符号付きまたは符号なし整数型 ([Byte](xref:System.Byte)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64) など) であることが必要です。 フィールドは静的リテラル フィールドで、各フィールドが 1 つの定数を表します。 複数のフィールドに同じ値を割り当てることもできます。 その場合は、リフレクションや文字列変換を行うために、いずれかの値をプライマリ列挙値としてマークしておく必要があります。

基になる型の値を列挙型に割り当てることも、その逆も可能です (キャストは必要ありません)。 列挙型のインスタンスを作成し、[System.Enum](xref:System.Enum) のメソッドや、その列挙型の基となる型に定義されている任意のメソッドを呼び出すことができます。 しかし、言語によっては、基になる型のインスタンスが必要とされるときに、列挙型をパラメーターとして渡すことが許可されていない場合もあります (またはその逆)。

また、列挙型には次のような制限があります。 

* 独自のメソッドは定義できません。

* インターフェイスを実装できません。

* プロパティまたはイベントを定義できません。

* 列挙型は、ジェネリック型に入れ子にされているという理由だけでジェネリックである場合を除き、ジェネリックにはなりません。 つまり、列挙型は、独自の型パラメーターを持つことができません。 

> [!NOTE]
> C# で作成された入れ子にされた型 (列挙型を含む) は、それを囲むすべてのジェネリック型の型パラメーターを含むため、独自の型パラメーターは持ちませんが、ジェネリックです。 詳細については、[Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) のリファレンス トピックを参照してください。 

[FlagsAttribute](xref:System.FlagsAttribute) 属性は、ビット フィールドと呼ばれる特別な種類の列挙型を表します。 ランタイム自体は通常の列挙型とビット フィールドを区別しませんが、言語の中にはそれらを区別するものもあります。 列挙型とビット フィールドが区別される場合、ビット フィールドではビットごとの演算子を使用して名前のない値を生成できますが、列挙型ではビットごとの演算子は使用できません。 通常、列挙型は、曜日、国名、地域名などの一意の要素のリストに使用されます。 通常、ビット フィールドは、`Red And Big And Fast` のような、特性や数量を組み合わせて示すリストに使用されます。

ビット フィールドと通常の列挙型を両方とも使用する方法を次の例に示します。

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a>インターフェイス

インターフェイスは、"can do" 関係または "has a" 関係を指定するコントラクトを定義します。 インターフェイスは、多くの場合、比較と並べ替え ([IComparable](xref:System.IComparable) インターフェイスや [IComparable&lt;T&gt;](xref:System.IComparable%601) インターフェイス)、等価テスト ( [IEquatable&lt;T&gt;](xref:System.IEquatable%601) インターフェイス)、コレクション内の項目の列挙 ([IEnumerable](xref:System.Collections.IEnumerable) インターフェイスや [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) インターフェイス) などの機能を実装するために使用されます。 インターフェイスには、プロパティ、メソッド、およびイベント (すべて抽象メンバー) を設定できます。つまり、インターフェイスは、メンバーとメンバーの署名を定義しますが、インターフェイス メンバーの機能を定義するインターフェイスを実装する型に依存します。 これは、インターフェイスを実装するクラスまたは構造体が、そのインターフェイスで宣言されている抽象メンバーの定義を提供する必要があることを意味します。 インターフェイスは、そのインターフェイスを実装するクラスまたは構造体に対して、1 つ以上の他のインターフェイスも同時に実装するように要求できます。

インターフェイスには、次のような制限があります。 

* 任意のアクセシビリティを指定してインターフェイスを宣言できますが、そのすべてのメンバーのアクセシビリティは public であることが必要です。

* インターフェイスでコンストラクターを定義することはできません。

* インターフェイスでフィールドを定義することはできません。

* インターフェイスで定義できるのはインスタンスのメンバーだけです。 静的メンバーを定義することはできません。

各言語には、メンバーの実装をそのメンバーを要求するインターフェイスに割り当てるための規則があります。これは、複数のインターフェイスで同じシグネチャを持つメンバーを宣言でき、それらのメンバーが別個の実装を持つことができるためです。

### <a name="delegates"></a>デリゲート

デリゲートは、C++ の関数ポインターと類似の目的で使用される参照型です。 これらは、.NET のイベント ハンドラーとコールバック関数に使用されます。 関数ポインターとは異なり、デリゲートは安全で、検証可能で、タイプ セーフです。 デリゲート型は、互換性のあるシグネチャを持つすべてのインスタンス メソッドまたは静的メソッドを表すことができます。 

デリゲートのパラメーターにメソッドのパラメーターよりも限定的な型が指定された場合、両者のパラメーター間に型の互換性があると見なされます。これによって、デリゲートに渡された引数が、メソッドに対して安全に渡されることが保証されます。

同様に、メソッドの戻り値の型の制限がデリゲートの戻り値の型より多いと、メソッドの戻り値がデリゲートの戻り値の型に安全にキャストされることが保証されるため、デリゲートの戻り値の型とメソッドの戻り値の型には互換性があります。

たとえば、[IEnumerable](xref:System.Collections.IEnumerable) 型のパラメーターおよび [Object](xref:System.Object) 型の戻り値を持つデリゲートは、[Object](xref:System.Object) 型のパラメーターおよび [IEnumerable](xref:System.Collections.IEnumerable) 型の戻り値を持ったメソッドを表すことができます。 

 よく "デリゲートは、それが表すメソッドにバインドされる" と言われます。 デリゲートは、メソッドにバインドされる以外にも、オブジェクトにバインドされる場合もあります。 オブジェクトはメソッドの第 1 パラメーターを表し、デリゲートが呼び出されるたびにメソッドに渡されます。 インスタンス メソッドの場合、バインドされたオブジェクトは、暗黙的な `this` パラメーター (Visual Basic では `Me`) として渡されます。静的メソッドの場合、オブジェクトは、メソッドの 1 つ目の仮パラメーターとして渡され、デリゲートのシグネチャは、その残りのパラメーターと完全に一致している必要があります。 
 
 すべてのデリゲートが [System.MulticastDelegate](xref:System.MulticastDelegate) を継承し、System.MulticastDelegate は [System.Delegate](xref:System.Delegate) を継承します。 C# および Visual Basic 言語では、これらの型からの継承は許可されていません。 代わりに、デリゲートを宣言するためのキーワードが用意されています。
 
 デリゲートは [MulticastDelegate](xref:System.MulticastDelegate) を継承するため、デリゲートには呼び出しリストがあります。これは、デリゲートが表し、デリゲートが呼び出されたときに実行されるメソッドのリストです。 リストのすべてのメソッドは、デリゲートが呼び出されたときに指定される引数を受け取ります。

> [!NOTE]
> デリゲートに戻り値が含まれていても、呼び出しリストに複数のメソッドが含まれているデリゲートに対しては、戻り値は定義されません。

コールバック メソッドの場合のように、多くの場合、デリゲートは 1 つのメソッドのみを表すため、デリゲートを作成し、呼び出す以外の処理は必要ありません。 

複数のメソッドを表すデリゲートの場合、.NET は [Delegate](xref:System.Delegate) と [MulticastDelegate](xref:System.MulticastDelegate) デリゲート クラスのメソッドを提供し、デリゲートの呼び出しリスト ([Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) メソッド) にメソッドを追加したり、メソッド ([Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) メソッド) を削除したり、呼び出しリスト ([Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) メソッド) を取得したりする操作をサポートしています。

> [!NOTE]
> C# または Visual Basic では、イベント ハンドラー デリゲートに対して、これらのメソッドを使用する必要はありません。これらの言語には、イベント ハンドラーの追加および削除に使用する構文が用意されているためです。

## <a name="type-definitions"></a>型定義

型定義には、次のものが含まれます。 

* 型に対して定義される属性

* 型のアクセシビリティ (参照範囲)

* 型の名前

* 型の基本型

* 型が実装するインターフェイス

* 型の各メンバーの定義

### <a name="attributes"></a>属性

属性を使用して、ユーザー定義のメタデータを追加できます。 属性の最も一般的な用途は、型についての補足的な情報をそのアセンブリに保存したり、型のメンバーの動作をデザイン時または実行時環境で変更したりすることです。 

属性は、それ自体が [System.Attribute](xref:System.Attribute) を継承するクラスです。 属性を使用できる言語にはそれぞれ、言語要素に属性を適用するための固有の構文があります。 属性はほぼすべての言語要素に適用できます。具体的にどの要素に属性を適用できるかは、その属性クラスに適用されている [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) によって定義されます。

### <a name="type-accessibility"></a>型のアクセシビリティ

すべての型には、他の型からのアクセシビリティを制御する修飾子があります。 ランタイムによってサポートされる型のアクセシビリティについて次の表で説明します。

ユーザー補助 | 説明
------------- | -----------
public | すべてのアセンブリから型にアクセスできます。
アセンブリ | 同じアセンブリ内からだけ型にアクセスできます。

入れ子にされた型のアクセシビリティは、その型のアクセシビリティ ドメインによって決まります。このアクセシビリティ ドメインは、そのメンバーに対して宣言されているアクセシビリティと、そのメンバーの直接のコンテナーである型のアクセシビリティ ドメインの両方によって決定されます。 ただし、入れ子にされた型のアクセシビリティ ドメインが、その型を含んでいる型のアクセシビリティ ドメインを上回ることはできません。

`P` というプログラム内の `T` という型で宣言された `M` という入れ子にされたメンバーのアクセシビリティ ドメインは、次のように定義されます (`M` 自体も型である可能性があります)。 

* `M` に対して宣言されたアクセシビリティが `public` の場合、`M` のアクセシビリティ ドメインは `T` のアクセシビリティ ドメインになります。

* `M` に対して宣言されているアクセシビリティが `protected internal` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと、`P` のプログラム テキストおよび `T` の外側で宣言された `P` から派生した任意の型のプログラム テキストとの積集合になります。

* `M` に対して宣言されているアクセシビリティが `protected` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと、`T` のプログラム テキストおよび `T` から派生した任意の型との積集合になります。

* `M` に対して宣言されているアクセシビリティが `internal` の場合、`M` のアクセシビリティ ドメインは、`T` のアクセシビリティ ドメインと `P` のプログラム テキストとの積集合になります。

* `M` に対して宣言されているアクセシビリティが `private` の場合、`M` のアクセシビリティ ドメインは `T` のプログラム テキストになります。

### <a name="type-names"></a>型名

共通型システムでは、名前に関して適用される制限は次の 2 つだけです。 

* すべての名前は Unicode (16 ビット) 文字列としてエンコードされます。

* 名前には、値 0x0000 (16 ビット) を埋め込むことはできません。

ただし、ほとんどの言語に型名に関する追加の制約が存在します。 すべての比較はバイト単位で行われるため、大文字と小文字を区別し、ロケールに依存しません。

型は、他のモジュールおよびアセンブリの型を参照する場合もありますが、1 つの .NET モジュール内で完全に定義されます  (ただし、コンパイラがサポートしていれば、複数のソース コード ファイルに分割できる場合もあります)。型名は 1 つの名前空間内で一意である必要があります。 型が完全に識別されるようにするため、その型名は、その型の実装を含んでいる名前空間によって修飾される必要があります。

### <a name="base-types-and-interfaces"></a>基本型とインターフェイス

型は、別の型から値と動作を継承できます。 共通型システムでは、複数の基本型から継承する型を作成することはできません。

型は任意の数のインターフェイスを実装できます。 型にインターフェイスを実装するには、そのインターフェイスのすべての仮想メンバーをその型に実装する必要があります。 仮想メソッドは派生型によって実装でき、静的または動的に呼び出すことができます。

## <a name="type-members"></a>型のメンバー

ランタイムでは、型の動作と状態を指定する型のメンバーを定義できます。 型のメンバーには、次のようなものがあります。

* [フィールド](#fields)

* [プロパティ](#properties)

* [メソッド](#methods)

* [コンストラクター](#constructors)

* [イベント](#events)

* [入れ子にされた型](#nested-types)

### <a name="fields"></a>フィールド

フィールドは、型の状態の一部を表し、格納するものです。 フィールドは、ランタイムがサポートする任意の型にすることができます。 通常、フィールドは、同じクラスまたはその派生クラスからしかアクセスできないように、`private` または `protected` のいずれかに設定されます。 フィールドの値を型の外部から変更できるようにする場合は、プロパティの set アクセサーを使用するのが一般的です。 パブリックに公開されたフィールドは、通常、読み取り専用であり、次の 2 種類に分けることができます。 

* 定数。その値は、デザイン時に割り当てられます。 これらはクラスの静的メンバーですが、`static` (Visual Basic では `Shared`) キーワードを使用して定義されません。

* 読み取り専用の変数。その値は、クラスのコンストラクターで割り当てることができます。

次の例は、読み取り専用フィールドの 2 つの用法を示しています。

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a>プロパティ

プロパティは、型の値または状態に名前を付け、そのプロパティの値を取得または設定するためのメソッドを定義します。 プロパティは、プリミティブ型、プリミティブ型のコレクション、ユーザー定義型、ユーザー定義型のコレクションにすることができます。 多くの場合、プロパティは、型のパブリックなインターフェイスを、その型の個々の実装とは切り離すために使用されます。 これにより、クラスに直接格納されていない値をプロパティに反映させたり (プロパティが計算後の値を返す場合など)、プライベート フィールドに割り当てる値を事前に検証したりすることが可能です。 後者のパターンを説明する例を次に示します。

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

読み取り可能なプロパティを含んだ型の Microsoft Intermediate Language (MSIL) には、プロパティそのもののほかに、`get`*_propertyname* メソッドが含まれています。また、書き込み可能なプロパティを含んだ型の MSIL には、`set`*_propertyname* メソッドが含まれています。

### <a name="methods"></a>メソッド

メソッドは、その型で利用できる操作を表します。 メソッドのシグネチャは、そのメソッドのパラメーターの型および戻り値の型として許可される型を示します。

ほとんどのメソッドでは、メソッド呼び出しに必要なパラメーターの厳密な個数が定義されていますが、いくつかのメソッドは可変個のパラメーターをサポートしています。 このようなメソッドで最後に宣言されるパラメーターには、[ParamArrayAttribute](xref:System.ParamArrayAttribute) 属性が適用されます。 通常、言語コンパイラには、C# の `params` や Visual Basic の `ParamArray` など、[ParamArrayAttribute](xref:System.ParamArrayAttribute) の明示的な使用を不要にするキーワードがあります。

### <a name="constructors"></a>コンストラクター

コンストラクターは、クラスまたは構造体の新しいインスタンスを作成する特殊なメソッドです。 他のメソッドと同様に、コンストラクターには、パラメーターを指定することができます。ただし、コンストラクターには戻り値はありません (つまり、`void` が返されます)。 

クラスのソース コードに明示的にコンストラクターが定義されていない場合は、コンパイラによって既定の (パラメーターなしの) コンストラクターが追加されます。 ただし、パラメーター化されたコンストラクターのみがクラスのソース コードで定義されている場合は、C# のコンパイラが、パラメーターなしのコンストラクターを生成しません。

構造体のソース コードでコンストラクターが定義される場合は、それらのコンストラクターがパラメーター化されている必要があります。構造体では既定の (パラメーターなしの) コンストラクターを定義できず、コンパイラは、構造体および他の値型のいずれに対しても、パラメーターなしのコンストラクターを生成しません。 すべての値型には、暗黙の既定コンストラクターがあります。 このコンストラクターは、共通言語ランタイムによって実装され、構造体のすべてのフィールドを既定の値に初期化します。 

### <a name="events"></a>イベント

イベントは、応答可能な事象 (イベント) を定義し、イベントへのサブスクライブ、イベントからのサブスクライブ解除、およびイベントの発生用のメソッドを定義します。 多くの場合、イベントは、他の型に対して状態の変更を通知するために使用されます。

### <a name="nested-types"></a>入れ子にされた型

入れ子にされた型とは、他の型のメンバーである型です。 入れ子にされた型はその親の型と密に結合されているため、汎用型としては使用できません。 入れ子にされた型は、宣言型で、入れ子にされた型のインスタンスを使用したり作成したりする場合に便利で、入れ子にされた型の使用はパブリック メンバーに公開されません。

入れ子にされた型は、混乱を招くおそれがあるため、特別な理由がない限り、パブリックに参照可能にすることはお勧めできません。 適切にデザインされたライブラリでは、入れ子にされた型を使ってオブジェクトをインスタンス化したり、変数を宣言したりすることが必要になることはほとんどありません。

## <a name="characteristics-of-type-members"></a>型のメンバーの特性

共通型システムでは、型のメンバーにさまざまな特性を適用できますが、各言語で、これらの特性がすべてサポートされている必要はありません。 メンバーの特性について次の表で説明します。

特徴 | 適用対象 | 説明
-------------- | ------------ | -----------
abstract | メソッド、プロパティ、およびイベント | 型はメソッドの実装を提供しません。 抽象メソッドを継承または実装する型は、そのメソッドの実装を提供する必要があります。 唯一の例外は、派生型自体が抽象型である場合です。 すべての抽象メソッドは仮想メソッドです。
private | すべて | メンバーが含まれているのと同じ型の内部、またはその型に入れ子にされた型の内部からだけアクセスできます。
family | すべて | メンバーが含まれているのと同じ型の内部、およびその型を継承した派生型からアクセスできます。
assemby | すべて | 型が定義されているアセンブリ内でだけアクセスできます。
family and assembly | すべて | family アクセスと assembly アクセスの両特性を満たす型からだけアクセスできます。
family または assemby | すべて | family アクセスまたは assembly アクセスのいずれかの特性を満たす型からだけアクセスできます。
public | すべて | すべての型からアクセスできます。
final | メソッド、プロパティ、およびイベント | その仮想メソッドを派生型ではオーバーライドできません。
initialize-only | フィールド | 値を初期化することだけでき、初期化後の書き込みは実行できません。
インスタンス | フィールド、メソッド、プロパティ、およびイベント | メンバーが `static` (C# )、`Shared` (Visual Basic)、`virtual` (C# )、または `Overridable` (Visual Basic) でマークされていない場合、それはインスタンス メンバーです (instance キーワードはありません)。 このようなメンバーについては、型を使用するオブジェクトと同数のコピーがメモリ内に格納されます。
リテラル | フィールド | このフィールドには、組み込みの値型の、コンパイル時点の固定値が割り当てられます。 リテラル フィールドを定数と呼ぶこともあります。
newslot または override | すべて | メンバーが、同じシグネチャを持つ継承メンバーとどのようにやり取りするかを定義します。`newslot` は、同じシグネチャを持つ継承されたメンバーを隠します。`override` は、継承された仮想メソッドの定義を置き換えます。 既定値は newslot です。
静的 | フィールド、メソッド、プロパティ、およびイベント | メンバーは、型の特定のインスタンスではなく、そのメンバーが定義されている型に属します。つまり、メンバーは型がインスタンス化されていなくても存在し、その型のすべてのインスタンスによって共有されます。
virtual | メソッド、プロパティ、およびイベント | メソッドは、派生型で実装でき、静的または動的に呼び出すことができます。 動的呼び出しが使用される場合は、実行時に呼び出しを行うインスタンスの型によって (コンパイル時に判明する型ではなく)、メソッドのどの実装が呼び出されるかが決定されます。 仮想メソッドを静的に呼び出すには、目的のバージョンのメソッドを使用する型に、変数をキャストする必要が生じる場合があります。

### <a name="overloading"></a>オーバーロード

型のメンバーには、それぞれ固有のシグネチャがあります。 メソッドのシグネチャは、メソッドの名前とパラメーター リスト (メソッドの引数の順序と型) で構成されます。 シグネチャが同じでなければ、同じ名前を持つ複数のメソッドを 1 つの型の中で定義できます。 同じ名前を持つ 2 つ以上のメソッドが定義されている場合、そのメソッドはオーバーロードされている、と言います。 たとえば、[System.Char](xref:System.Char) では、`IsDigit` メソッドがオーバーロードされています。 一方のメソッドは [Char](xref:System.Char) を受け取ります。 もう一方のメソッドは、[String](xref:System.String) および [Int32](xref:System.Int32) を受け取ります。 

> [!NOTE]
> 戻り値の型は、メソッドのシグネチャの一部として見なされません。 つまり、戻り値の型が異なっているだけでは、メソッドをオーバーロードすることはできません。

### <a name="inheriting-overriding-and-hiding-members"></a>メンバーの継承、オーバーライド、および隠ぺい

派生型は、その基本型のすべてのメンバーを継承します。つまり、基本型のすべてのメンバーは、派生型に対しても定義されており、使用可能です。 継承されたメンバーの動作または特性は、次の 2 つの方法で変更できます。 

* 派生型で、同じシグネチャを持つ新しいメンバーを定義することによって、継承されたメンバーを隠ぺいできます。 この方法は、public のメンバーを private に変更したり、`final` としてマークされている継承メソッドに新しい動作を定義したりするために使用します。

* 派生型で、継承された仮想メソッドをオーバーライドできます。 オーバーライドするメソッドでは、コンパイル時点の変数の型ではなく、実行時の値の型に基づいて呼び出される、メソッドの新しい定義を提供します。 メソッドが仮想メソッドをオーバーライドできるのは、その仮想メソッドが `final` としてマークされておらず、新しいメソッドのアクセシビリティがその仮想メソッドと少なくとも同じ場合に限られます。

## <a name="see-also"></a>関連項目

[.NET Framework における型変換](type-conversion.md)


<!--HONumber=Nov16_HO1-->


