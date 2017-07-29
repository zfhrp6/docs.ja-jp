---
title: "プロパティ (C# プログラミング ガイド)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.properties
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 127299a617cacee15f87964a12bb3877a2586204
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="properties-c-programming-guide"></a>プロパティ (C# プログラミング ガイド)

プロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行う、柔軟な機構が用意されたメンバーです。 プロパティは、パブリック データのメンバーと同様に使用できますが、実際は*アクセサー*という特殊なメソッドです。 メソッドの安全性と柔軟性を高めながら、簡単にデータにアクセスできます。  

## <a name="properties-overview"></a>プロパティの概要  
  
- プロパティを使えば、実装や検査コードを隠したままで、値の取得と設定についてパブリックな方法をクラスが公開できます。  
  
- [get](../../../csharp/language-reference/keywords/get.md) プロパティ アクセサーはプロパティ値を取得するために使用し、[set](../../../csharp/language-reference/keywords/set.md) プロパティ アクセサーは新しい値を割り当てるために使用します。 これらのアクセサーには異なるアクセス レベルを指定できます。 詳細については、「[アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。  
  
- `set` アクセサーで割り当てる値は [value](../../../csharp/language-reference/keywords/value.md) キーワードを使用して定義します。  
- プロパティの種類には、*読み取り/書き込み* (`get` アクセサーと `set` アクセサーの両方を備える)、*読み取り専用* (`get` アクセサーのみで `set` アクセサーはない)、*書き込み専用* (`set` アクセサーのみで `get` アクセサーはない) があります。 書き込み専用のプロパティの使用頻度は低く、ほとんどの場合、機密データへのアクセスを制限するために使用されます。

- カスタムのアクセサー コードを必要としない単純なプロパティは、式本体の定義として、または[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)として実装できます。
 
## <a name="properties-with-backing-fields"></a>バッキング フィールドを持つプロパティ

プロパティを実装する基本的な手法の 1 つとして、プロパティ値の設定と取得にプライベート バッキング フィールドを使用する方法があります。 この方法では、`get` アクセサーはプライベート フィールドの値を返します。`set` アクセサーはプライベート フィールドに値を割り当てる前にデータ検証を実行できます。 また、どちらのアクセサーも、データの変換や計算を行ってから、データを格納したり返したりすることができます。

このパターンを説明する例を下に示します。 この例では、`TimePeriod` クラスは時間間隔を表しています。 クラスの内部では、`seconds` という名前のプライベート フィールドに時間間隔が秒単位で格納されます。 `Hours` という読み取り/書き込みプロパティでは、ユーザーが時間間隔を時間単位で指定できます。 `get` アクセサーと `set` アクセサーの両方で、必要に応じて時間と秒の変換が実行されます。 また、`set` アクセサーは、データを検証し、時間数が無効である場合に @System.ArgumentOutOfRangeException をスローします。 
   
 [!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>式本体の定義  

 プロパティ アクセサーは、通常、式の結果を割り当てるか返すだけの 1 行のステートメントで構成されます。 プロパティは、本体が式形式のメンバーとして実装できます。 式本体の定義は、`=>` 記号の後に、プロパティに割り当てるかプロパティから取得するための式を続けて構成します。

 C# 6 以降では、読み取り専用プロパティに `get` アクセサーを式形式のメンバーとして実装できます。 この場合、`get` アクセサー キーワードと `return` キーワードはどちらも使用しません。 次の例では、読み取り専用 `Name` プロパティを式形式のメンバーとして実装しています。

 [!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 C# 7 以降では、`get` アクセサーと `set` アクセサーのどちらも、式形式のメンバーとして実装できます。 この場合、`get` キーワードと `set` キーワードを使用する必要があります。 両方のアクセサーに式本体の定義を使用する例を次に示します。 `get` アクセサーで `return` キーワードが使用されていない点に注意してください。
 
  [!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>自動実装プロパティ

ロジックを追加しなくても、プロパティの `get` アクセサーと `set` アクセサーはバッキング フィールドに値を割り当てたりバッキング フィールドから取得したりすることができます。 この自動実装プロパティを使用すると、C# コンパイラによってバッキング フィールドが透過的に提供されるため、コードを簡略化できます。 

プロパティが `get` アクセサーと `set` アクセサーの両方を備えている場合は、両方を自動実装する必要があります。 自動実装プロパティを定義するには、実装を省略して `get` キーワードと `set` キーワードを使用します。 次の例は前の例と似ていますが、`Name` と `Price` が自動実装プロパティである点が異なります。 この例では、パラメーター化されたコンストラクターも削除されているため、`SaleItem` オブジェクトが既定のコンストラクターの呼び出しと[オブジェクト初期化子](object-and-collection-initializers.md)を使用して初期化されています。

  [!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>関連項目  
  
-   [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [et キーワード](../../../csharp/language-reference/keywords/get.md)    
 [set キーワード](../../../csharp/language-reference/keywords/set.md)    

