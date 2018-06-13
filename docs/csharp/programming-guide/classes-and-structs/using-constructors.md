---
title: コンストラクターの使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 5fe6f10e3842c0c0aac4b2669f8ca367fa8c3be2
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172333"
---
# <a name="using-constructors-c-programming-guide"></a>コンストラクターの使用 (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)を作成する際には、コンストラクターが呼び出されます。 コンストラクターの名前はクラスまたは構造体と同じで、通常は、このコンストラクターによって、新しいオブジェクトのデータ メンバーが初期化されます。  
  
 次の例では、`Taxi` というクラスが、簡単なコンストラクターを使用して定義された後、 [new](../../../csharp/language-reference/keywords/new.md) 演算子によってインスタンス化されます。 `Taxi` コンストラクターは、新しいオブジェクトに対してメモリが割り当てられるとすぐに、`new` 演算子によって呼び出されます。  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 パラメーターを取らないコンストラクターを "*既定のコンストラクター*" と呼びます。 `new` 演算子を使用してオブジェクトがインスタンス化される際に `new` に引数が渡されないと、この既定のコンストラクターが呼び出されます。 詳細については、「[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)」を参照してください。  
  
 クラスが[静的](../../../csharp/language-reference/keywords/static.md)である場合を除き、コンストラクターが存在しないクラスには、クラスをインスタンス化できるように、パブリックな既定のコンストラクターが C# コンパイラによって割り当てられます。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 次のようにコンストラクターをプライベートにすれば、クラスがインスタンス化されないようにできます。  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 詳細については、「[プライベート コンストラクター](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)」を参照してください。  
  
 [struct](../../../csharp/language-reference/keywords/struct.md) 型のコンストラクターはクラス コンストラクターに似ていますが、`structs` には、明示的な既定のコンストラクターを含めることができません。既定のコンストラクターは、コンパイラによって自動的に提供されるためです。 このコンストラクターは、`struct` 内の各フィールドを既定値に初期化します。 詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。 ただし、この既定のコンストラクターは、`struct` が `new` によってインスタンス化される場合にのみ呼び出されます。 たとえば、次のコードでは、<xref:System.Int32> の既定のコンストラクターが使用されるため、整数が確実に初期化されます。  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 ただし、次のコードでは `new` が使用されておらず、コードは初期化されていないオブジェクトの使用を試みるため、コンパイラ エラーが発生します。  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 これに対して、`structs` をベースにしたオブジェクト (組み込みのすべての数値型など) は、次の例のように、初期化または代入してから使用できます。  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 このため、値型の既定のコンストラクターを呼び出す必要はありません。  
  
 クラスと `structs` のどちらも、パラメーターを受け取るコンストラクターを定義できます。 パラメーターを受け取るコンストラクターは、`new` ステートメントまたは [base](../../../csharp/language-reference/keywords/base.md) ステートメントを使用して呼び出す必要があります。 クラスと `structs` は複数のコンストラクターを定義することもできます。また、どちらも、既定のコンストラクターの定義には必要ありません。 例:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 このクラスは、次のいずれかのステートメントを使用して作成できます。  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 コンストラクターでは、`base` キーワードを使用して、基底クラスのコンストラクターを呼び出すことができます。 例:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 この例では、コンストラクターのブロックを実行する前に、基底クラスのコンストラクターを呼び出しています。 `base` キーワードは、パラメーターの有無に関係なく使用できます。 コンストラクターのパラメーターは、`base` のパラメーターまたは式の一部として使用できます。 詳細については、「[base](../../../csharp/language-reference/keywords/base.md)」を参照してください。  
  
 派生クラスで基底クラスのコンストラクターが `base` キーワードを使用して明示的に呼び出されていない場合、既定のコンストラクター (存在する場合) は暗黙的に呼び出されます。 つまり、次に示すコンストラクターの宣言は実質的に同じです。  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 基底クラスが既定のコンストラクターを提供しない場合、派生クラスでは、`base` を使って基本コンストラクターを明示的に呼び出す必要があります。  
  
 コンストラクターで [this](../../../csharp/language-reference/keywords/this.md) キーワードを使用すると、同じオブジェクトで別のコンストラクターを呼び出すことができます。 `base` と同様、`this` もパラメーターの有無に関係なく使用でき、コンストラクターのパラメーターはいずれも `this` のパラメーターとしても、式の一部としても使用できます。 たとえば、上の例の 2 番目のコンストラクターは `this` を使用して次のように書き直すことができます。  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 上の例で `this` キーワードを使用すると、このコンストラクターが呼び出されます。  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 コンストラクターは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) または [private protected](../../../csharp/language-reference/keywords/private-protected.md) としてマークできます。 こうしたアクセス修飾子により、クラスのユーザーによるクラスの作成方法が定義されます。 詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 コンストラクターは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的として宣言できます。 静的コンストラクターは、静的フィールドがアクセスされる直前に自動的に呼び出され、通常は静的なクラス メンバーを初期化するために使用されます。 詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)
