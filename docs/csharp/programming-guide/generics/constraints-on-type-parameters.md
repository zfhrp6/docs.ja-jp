---
title: "型パラメーターの制約 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f7c80acdb3815af4b5d545297894778029a9104
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>型パラメーターの制約 (C# プログラミング ガイド)
ジェネリック クラスを定義する場合、クライアント コードがクラスをインスタンス化するときに、型引数に使用できる種類の型に制限を適用することができます。 クライアント コードで、この制限で許可されていない型を使用してクラスをインスタンス化しようとすると、コンパイル時エラーが発生します。 これらの制限は、制約と呼ばれます。 制約を指定するには、`where` コンテキスト キーワードを使用します。 次の表は、6 種類の制約をまとめた一覧です。  
  
|制約|説明|  
|----------------|-----------------|  
|`where T: struct`|この型引数は値の型である必要があります。 <xref:System.Nullable> を除く任意の値の型を指定できます。 詳細については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください。|  
|`where T : class`|この型引数は、参照型である必要があります。任意のクラス、インターフェイス、デリゲート、または配列型にも適用されます。|  
|`where T : new()`|この型引数には、パラメーターなしのパブリック コンストラクターが必要です。 `new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。|  
|`where T : `*\<基底クラス名>*|この型引数は、指定された基底クラスであるか、そのクラスから派生している必要があります。|  
|`where T : `*\<インターフェイス名>*|この型引数は、指定されたインターフェイスであるか、そのインターフェイスを実装している必要があります。 複数のインターフェイス制約を指定することができます。 制約のインターフェイスを汎用的にすることもできます。|  
|`where T : U`|T に指定する型引数は、U に指定された引数であるか、その引数から派生している必要があります。|  
  
## <a name="why-use-constraints"></a>制約を使用する理由  
 ジェネリック リスト内の項目を調べて、有効かどうかを判断する場合、または他の項目と比較する場合、クライアント コードに指定される可能性があるすべての型引数が、呼び出す必要がある演算子またはメソッドをサポートしているという何らかの保証をコンパイラが獲得する必要があります。 この保証を獲得するには、1 つまたは複数の制約をジェネリック クラス定義に適用します。 たとえば、この基底クラスの制約は、この型のオブジェクト、またはこの型から派生したオブジェクトのみを型引数として使用することをコンパイラに指示しています。 コンパイラがこの保証を獲得したら、その型のメソッドをジェネリック クラスで呼び出すことができるようになります。 制約を適用するには、コンテキスト キーワード `where` を使用します。 基底クラス制約を適用して `GenericList<T>` クラス (「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照) に追加できる機能を説明するコード例を次に示します。  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 この制約を使用すると、型 T のすべての項目は `Employee` オブジェクトであるか、`Employee` から継承されたオブジェクトであると保証されるため、ジェネリック クラスから `Employee.Name` プロパティを使用できます。  
  
 同じ型パラメーターに複数の制約を適用できます。また、制約自体をジェネリック型にすることもできます。次に例を示します。  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 型パラメーターを制約すると、使用できる操作とメソッド呼び出しの数は、制約する型、およびその継承階層内のすべての型でサポートされている数まで増えます。 そのため、ジェネリック クラスまたはメソッドを指定するときに、単純な割り当てや、`System.Object` でサポートされていない任意のメソッド呼び出しでジェネリック メンバーに対して任意の操作を実行する場合、型パラメーターに制約を適用する必要があります。  
  
 `where T : class` 制約を適用する場合は、型パラメーターに `==` および `!=` 演算子を使用しないでください。これらの演算子でテストされるのは、値の等価性ではなく、参照 ID についてのみです。 これらの演算子が、引数として使用されている型内でオーバーロードされている場合でも、同様のことが言えます。 この点を説明するコードを次に示します。<xref:System.String> クラスが `==` 演算子をオーバーロードしている場合でも、出力は false です。  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 この動作の理由は、コンパイル時に、コンパイラは T が参照型であることしか認識しておらず、すべての参照型で有効な既定の演算子を使用する必要があるためです。 値の等価性をテストする必要がある場合は、`where T : IComparable<T>` 制約も適用し、ジェネリック クラスの制約に使用されるすべてのクラスでそのインターフェイスを実装することをお勧めします。  
  
## <a name="constraining-multiple-parameters"></a>複数のパラメーターを制約する  
 複数のパラメーターに制約を適用できます。また、複数の制約を 1 つのパラメーターに適用することができます。次に例を示します。  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>非バインド型パラメーター  
 パブリック クラス `SampleClass<T>{}` の T など、制約がない型パラメーターは、非バインド型パラメーターと呼ばれます。 非バインド型パラメーターには次の規則があります。  
  
-   `!=` および `==` 演算子は使用できません。これは、具象型引数がこれらの演算子をサポートするという保証がないためです。  
  
-   これらの演算子は `System.Object` との間で相互に変換できます。また、任意のインターフェイス型に明示的に変換できます。  
  
-   これは [null](../../../csharp/language-reference/keywords/null.md) と比較することができます。 非バインド型パラメーターと `null` を比較し、その型引数が値の型の場合、比較結果として常に false が返されます。  
  
## <a name="type-parameters-as-constraints"></a>制約としての型パラメーター  
 制約としてジェネリック型パラメーターを使用する方法は、独自の型パラメーターがあるメンバー関数が、含まれる型の型パラメーターにそのパラメーターを制約する必要がある場合に便利です。次に例を示します。  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 前の例の `T` は、`Add` メソッドのコンテキストでは型の制約ですが、`List` クラスのコンテキストでは非バインド型パラメーターです。  
  
 型パラメーターは、ジェネリック クラス定義の制約としても使用できます。 型パラメーターは、他の型パラメーターと共に山かっこ内で宣言する必要があります。  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 ジェネリック クラスで制約として型パラメーターを使用する方法が便利なのは、ごく限られた場合のみです。コンパイラでは、`System.Object` から派生したことを除き、型パラメーターに関して何も仮定できないためです。 2 つの型パラメーター間に継承関係を適用するシナリオには、ジェネリック クラスの制約として型パラメーターを使用してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Collections.Generic>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new 制約](../../../csharp/language-reference/keywords/new-constraint.md)
