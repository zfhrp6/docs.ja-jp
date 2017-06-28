---
title: "リフレクションとジェネリック型 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: 6860a46bfb2d8959e1db2b4714874081a156b76f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="reflection-and-generic-types"></a>リフレクションとジェネリック型
<a name="top"></a> リフレクションの観点から言えば、ジェネリック型は、それがジェネリック型定義である場合は型パラメーター セットが、構築された型である場合は型引数セットが関連付けられているという点で通常の型と異なります。 ジェネリック メソッドと通常のメソッドの違いも、それと同様です。  
  
 リフレクションでジェネリック型とジェネリック メソッドが処理されるしくみを理解するうえで、次の 2 つの点が重要となります。  
  
-   ジェネリック型の定義とジェネリック メソッドの定義の型パラメーターは、<xref:System.Type> クラスのインスタンスによって表されます。  
  
    > [!NOTE]
    >  <xref:System.Type> オブジェクトがジェネリック型パラメーターを表す場合、<xref:System.Type> の多数のプロパティとメソッドの動作が異なります。 これらの相違点については、該当するプロパティおよびメソッドに関するトピックに記載されています。 たとえば、<xref:System.Type.IsAutoClass%2A> や <xref:System.Type.DeclaringType%2A> を参照してください。 さらに、一部のメンバーは <xref:System.Type> オブジェクトがジェネリック型パラメーターを表す場合にのみ有効です。 例については、「<xref:System.Type.GetGenericTypeDefinition%2A>」を参照してください。  
  
-   <xref:System.Type> のインスタンスがジェネリック型を表す場合、そのインスタンスには、型パラメーター (ジェネリック型の定義の場合) または型引数 (構築された型の場合) を表す型の配列が含まれます。 ジェネリック メソッドを表す <xref:System.Reflection.MethodInfo> クラスのインスタンスの場合も同様です。  
  
 リフレクションが提供する <xref:System.Type> および <xref:System.Reflection.MethodInfo> のメソッドを使用すると、型パラメーターの配列にアクセスしたり、<xref:System.Type> のインスタンスが型パラメーターと実際の型のどちらを表しているかを確認したりできます。  
  
 ここで説明するメソッドを示すコード例については、「[方法 : リフレクションを使用してジェネリック型をチェックおよびインスタンス化する](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)」をご覧ください。  
  
 以下の説明は、型パラメーターと型引数の違いや、オープン構築型とクローズ構築型の違いなど、ジェネリックの用語を十分に理解していることを前提としています。 詳細については、「[ジェネリック](../../../docs/standard/generics/index.md)」を参照してください。  
  
 この概要は、次のセクションで構成されています。  
  
-   [ジェネリック型またはジェネリック メソッドであるかどうかの確認](#is_this_a_generic_type_or_method)  
  
-   [クローズ ジェネリック型の生成](#generating_closed_generic_types)  
  
-   [型引数と型パラメーターの確認](#examining_type_arguments)  
  
-   [インバリアント](#invariants)  
  
-   [関連トピック](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>ジェネリック型またはジェネリック メソッドであるかどうかの確認  
 リフレクションを使用して、<xref:System.Type> のインスタンスによって表される不明な型を調べる場合は、<xref:System.Type.IsGenericType%2A> プロパティを使用してその不明な型がジェネリックかどうかを確認します。 型がジェネリックの場合、`true` を返します。 同様に、<xref:System.Reflection.MethodInfo> クラスのインスタンスによって表される不明なメソッドを調べる場合には、<xref:System.Reflection.MethodInfo.IsGenericMethod%2A> プロパティを使用してそのメソッドがジェネリックかどうかを確認します。  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>ジェネリック型の定義またはジェネリック メソッドの定義であるかどうかの確認  
 <xref:System.Type> オブジェクトがジェネリック型の定義を表しているかどうかを確認するには、<xref:System.Type.IsGenericTypeDefinition%2A> プロパティを使用します。また、<xref:System.Reflection.MethodInfo> がジェネリック メソッドの定義を表しているかどうかを確認するには、<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> メソッドを使用します。  
  
 ジェネリック型の定義とジェネリック メソッドの定義は、インスタンス化可能な型の作成元となるテンプレートです。 <xref:System.Collections.Generic.Dictionary%602> など、.NET Framework クラス ライブラリのジェネリック型は、ジェネリック型の定義です  
  
### <a name="is-the-type-or-method-open-or-closed"></a>型またはメソッドがオープンかクローズか  
 すべての型パラメーター (すべての内包する型のすべての型パラメーターを含む) がインスタンス化可能な型に置き換えられている場合、ジェネリック型またはジェネリック メソッドはクローズであるといいます。 ジェネリック型のインスタンスを作成できるのは、それがクローズである場合だけです。 型がオープンである場合、<xref:System.Type.ContainsGenericParameters%2A?displayProperty=fullName> プロパティは `true` を返します。 メソッドの場合、<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=fullName> メソッドで同じ機能が実行されます。  
  
 [ページのトップへ](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>クローズ ジェネリック型の生成  
 ジェネリック型の定義を取得したら、<xref:System.Type.MakeGenericType%2A> メソッドを使用してクローズ ジェネリック型を作成します。また、ジェネリック メソッドの定義を取得したら、<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> メソッドを使用してクローズ ジェネリック メソッドの <xref:System.Reflection.MethodInfo> を作成します。  
  
### <a name="getting-the-generic-type-or-method-definition"></a>ジェネリック型の定義またはジェネリック メソッドの定義の取得  
 ジェネリック型またはジェネリック メソッドの定義ではないオープン ジェネリック型またはオープン ジェネリック メソッドがある場合、そのインスタンスを作成することはできず、欠落している型パラメーターを指定することもできません。 ジェネリック型の定義またはジェネリック メソッドの定義が必要です。 ジェネリック型の定義を取得するには <xref:System.Type.GetGenericTypeDefinition%2A> メソッドを使用し、ジェネリック メソッドの定義を取得するには <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> メソッドを使用します。  
  
 たとえば、`Dictionary<int, string>` (Visual Basic では `Dictionary(Of Integer, String)`) を表す <xref:System.Type> オブジェクトがあり、`Dictionary<string, MyClass>` 型を作成する必要がある場合は、<xref:System.Type.GetGenericTypeDefinition%2A> メソッドを使用して `Dictionary<TKey, TValue>` を表す <xref:System.Type> を取得し、<xref:System.Type.MakeGenericType%2A> メソッドを使用して `Dictionary<int, MyClass>` を表す <xref:System.Type> を作成します。  
  
 ジェネリック型ではないオープン ジェネリック型の例は、この後の「型パラメーターまたは型引数」セクションを参照してください。  
  
 [ページのトップへ](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>型引数と型パラメーターの確認  
 ジェネリック型の型パラメーターまたは型引数を表す <xref:System.Type> オブジェクトの配列を取得するには、<xref:System.Type.GetGenericArguments%2A?displayProperty=fullName> メソッドを使用します。また、ジェネリック メソッドに対して同じ操作を実行するには、<xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=fullName> メソッドを使用します。  
  
 <xref:System.Type> オブジェクトが型パラメーターを表していることがわかったら、リフレクションによって他の多くの詳細を確認できます 型パラメーターのソース、その位置、およびその制約を確認できます。  
  
### <a name="type-parameter-or-type-argument"></a>型パラメーターまたは型引数  
 配列の特定の要素が型パラメーターと型引数のどちらであるかを確認するには、<xref:System.Type.IsGenericParameter%2A> プロパティを使用します。 要素が型パラメーターの場合、<xref:System.Type.IsGenericParameter%2A> プロパティは `true` です。  
  
 ジェネリック型には、ジェネリック型の定義がないことがあります。その場合のジェネリック型はオープンであり、型引数と型パラメーターが混在しています。 たとえば、次のコードでは、クラス `D` は `B` の 2 つ目の型パラメーターを `D` の 1 つ目の型パラメーターに置き換えることによって作成された型から派生します。  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp#  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 `D<V, W>` を表す <xref:System.Type> オブジェクトを取得し、<xref:System.Type.BaseType%2A> プロパティを使用してその基本型を取得した場合、結果として得られる `type B<int, V>` はオープンであり、ジェネリック型の定義ではありません。  
  
### <a name="source-of-a-generic-parameter"></a>ジェネリック パラメーターのソース  
 ジェネリック型パラメーターのソースとしては、開発者が今調べている型、外側の型、またはジェネリック メソッドが考えられます。 ジェネリック型パラメーターのソースを特定するには、次の手順を実行します。  
  
-   まず、<xref:System.Type.DeclaringMethod%2A> プロパティを使用して、型パラメーターのソースがジェネリック メソッドかどうかを判定します。 このプロパティの値が null 参照 (Visual Basic では `Nothing`) ではない場合、ソースはジェネリック メソッドです。  
  
-   ソースがジェネリック メソッドでない場合は、<xref:System.Type.DeclaringType%2A> プロパティを使用して、ジェネリック型パラメーターが属しているジェネリック型を判定します。  
  
 型パラメーターがジェネリック メソッドに属している場合、<xref:System.Type.DeclaringType%2A> プロパティはそのジェネリック メソッドを宣言した型を返しますが、これは無関係です。  
  
### <a name="position-of-a-generic-parameter"></a>ジェネリック パラメーターの位置  
 まれなケースですが、宣言するクラスの型パラメーター リスト内の型パラメーターの位置を確認することが必要な場合があります。 たとえば、上の例の `B<int, V>` 型を表す <xref:System.Type> オブジェクトについて考えてみます。 <xref:System.Type.GetGenericArguments%2A> メソッドからは、型引数のリストが提供されます。`V` を調べるときには、<xref:System.Type.DeclaringMethod%2A> プロパティと <xref:System.Type.DeclaringType%2A> プロパティを使用してそれがどこからのものかを確認できます 次に、<xref:System.Type.GenericParameterPosition%2A> プロパティを使用することにより、型パラメーター リストの中でそれが定義されていた位置を判定できます。 この例では、`V` は、定義された型パラメーター リスト内の 0 (ゼロ) の位置にあります。  
  
### <a name="base-type-and-interface-constraints"></a>基本データ型とインターフェイスの制約  
 <xref:System.Type.GetGenericParameterConstraints%2A> メソッドを使用すると、基本データ型の制約と型パラメーターのインターフェイス制約を取得できます。 配列の要素の順序は重要ではありません。 要素がインターフェイス型の場合、その要素はインターフェイスの制約を表します。  
  
### <a name="generic-parameter-attributes"></a>ジェネリック パラメーターの属性  
 <xref:System.Type.GenericParameterAttributes%2A> プロパティを使用すると、型パラメーターの変化 (共変性または反変性) と特殊な制約を示す <xref:System.Reflection.GenericParameterAttributes> 値を取得できます。  
  
#### <a name="covariance-and-contravariance"></a>共変性と反変性  
 型パラメーターが共変性と反変性のどちらであるかを判定するには、<xref:System.Type.GenericParameterAttributes%2A> プロパティから返される <xref:System.Reflection.GenericParameterAttributes> 値に <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=fullName> マスクを適用します。 結果が <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=fullName> の場合、型パラメーターはインバリアント (不変) です。 「 [共変性と反変性](../../../docs/standard/generics/covariance-and-contravariance.md)を参照してください。  
  
#### <a name="special-constraints"></a>特殊な制約  
 型パラメーターの特殊な制約を判定するには、<xref:System.Type.GenericParameterAttributes%2A> プロパティから返される <xref:System.Reflection.GenericParameterAttributes> 値に <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=fullName> マスクを適用します。 結果が <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=fullName> の場合、特殊な制約はありません。 型パラメーターに対する制約としては、参照型であること、null 非許容値型であること、既定のコンストラクターが存在すること、があります。  
  
 [ページのトップへ](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>インバリアント  
 ジェネリック型のリフレクションで使用される一般的な用語に対するインバリアント条件を記載した表は、<xref:System.Type.IsGenericType%2A?displayProperty=fullName> を参照してください。 ジェネリック メソッドに関連するその他の用語については、<xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=fullName> を参照してください。  
  
 [ページのトップへ](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法 : リフレクションを使用してジェネリック型をチェックおよびインスタンス化する](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|<xref:System.Type> と <xref:System.Reflection.MethodInfo> のプロパティとメソッドを使用してジェネリック型について調べる方法を説明します。|  
|[ジェネリック](../../../docs/standard/generics/index.md)|ジェネリックの機能と .NET Framework におけるサポートについて説明します。|  
|[方法: リフレクション出力を使用してジェネリック型を定義する](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|リフレクション出力を使用して動的アセンブリにジェネリック型を生成する方法について説明します。|  
|[型情報の表示](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|<xref:System.Type> クラスについて説明します。また、<xref:System.Type> をさまざまなリフレクション クラスと共に使用して、コンストラクター、メソッド、フィールド、プロパティ、およびイベントについての情報を取得する方法を示すコード例を提供します。|
