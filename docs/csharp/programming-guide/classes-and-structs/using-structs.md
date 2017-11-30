---
title: "構造体の使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94181c42ce913dc76c9a074e4bcbb8240764c896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-structs-c-programming-guide"></a>構造体の使用 (C# プログラミング ガイド)
`struct` 型は、 `Point`、 `Rectangle`、 `Color`などの軽量のオブジェクトを表すのに適しています。 点を表すには [自動実装プロパティ](../../../csharp/language-reference/keywords/class.md) がある [クラス](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)を使用するのと同じくらい便利ですが、シナリオによっては [構造体](../../../csharp/language-reference/keywords/struct.md) を使用する方がより効率的です。 たとえば、1,000 個の `Point` オブジェクトから成る配列を宣言する場合は、各オブジェクトの参照用に追加のメモリを割り当てます。この場合、構造体であれば処理上の負荷を抑えることができます。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] には <xref:System.Drawing.Point>という名前のオブジェクトが含まれているため、この例の構造体には代わりに "CoOrds" という名前が付けられています。  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 構造体に既定の (パラメーターなしの) コンストラクターを定義するとエラーになります。 また、構造体の本体のインスタンス フィールドを初期化した場合もエラーになります。 外部からアクセスできる構造体のメンバーを初期化するには、パラメーター化されたコンス トラクターが暗黙的な既定のコンス トラクターを使用してのみ、[オブジェクトの初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)、または構造体が宣言された後にメンバーを個別にアクセスすることによってです。 プライベートまたはアクセスできないメンバーはコンス トラクターの使用のみが必要です。
  
 使用して struct オブジェクトを作成する場合、[新しい](../../../csharp/language-reference/keywords/new.md)演算子を作成およびに従って適切なコンス トラクターが呼び出されます、[コンス トラクターのシグネチャ](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax)です。 クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。 このような場合、コンストラクターの呼び出しが行われないため、割り当てがより効率的になります。 ただし、各フィールドは未割り当てのままになり、すべてのフィールドが初期化されるまではオブジェクトを使用できません。 これには、取得または自動実装プロパティを使用して値を設定することができないが含まれます。
 
 よると、すべてのメンバーが割り当てられた、既定のパラメーターなしコンス トラクターを使用して、構造体オブジェクトをインスタンス化する場合、[既定値](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)です。
  
 構造体のパラメーターを持つコンス トラクターを記述する場合は、すべてのメンバーを明示的に初期化する必要があります。それ以外の場合 1 つまたは複数のメンバーは未割り当てのままし、コンパイラ エラー CS0171 が生成した、構造体を使用することはできません。  
  
 クラスには継承がありますが、構造体には継承がありません。 構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。 ただし、構造体は、基本クラス <xref:System.Object>から継承します。 構造体は、クラスの場合とまったく同じ方法でインターフェイスを実装できます。  
  
 `struct`キーワードを使用してクラスを宣言することはできません。 C# では、クラスと構造体は、意味が異なります。 構造体は値型ですが、クラスは参照型です。 詳細については、「 [Value Types (値型)](../../../csharp/language-reference/keywords/value-types.md)」を参照してください。  
  
 参照型の機能が必要な場合以外は、小さいクラスを構造体として宣言した方が、システムによってより効率的に処理される可能性があります。  
  
## <a name="example-1"></a>例 1  
  
### <a name="description"></a>説明  
 既定のコンストラクターとパラメーター化されたコンストラクターの両方を使用した `struct` の初期化の例を次に示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>例 2  
  
### <a name="description"></a>説明  
 構造体に固有の機能を次の例に示します。 この例では、 `new` 演算子を使用せずに CoOrds オブジェクトを作成しています。 `struct` を `class`という単語に置き換えた場合、プログラムはコンパイルされません。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)
