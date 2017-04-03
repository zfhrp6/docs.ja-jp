---
title: "インデクサー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b5ca4707903f03b6ab7138137fb3107cfb0cce2
ms.lasthandoff: 03/13/2017

---
# <a name="indexers-c-programming-guide"></a>インデクサー (C# プログラミング ガイド)

インデクサーを使用すると、配列と同じようにクラスまたは構造体のインスタンスにインデックスを作成することができます。 インデックス値は、型またはインスタンス メンバーの明示的な指定なしで設定または取得できます。 インデクサーは[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)と似ていますが、そのアクセサーがパラメーターを取る点が異なります。  
 
 次の例は、値の割り当てと取得を行う単純な [get](../../../csharp/language-reference/keywords/get.md) アクセサー メソッドと [set](../../../csharp/language-reference/keywords/set.md) アクセサー メソッドを持つジェネリック クラスを定義します。 `Program` クラスは、文字列の格納用にこのクラスのインスタンスを作成します。  
  
 [!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  その他の例については、「[関連セクション](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)」を参照してください。  
  
## <a name="expression-body-definitions"></a>式の本文の定義  
 
通常は、インデクサーの get または set アクセサーは、値を返すか値を設定する単一のステートメントで構成します。 式の本文のメンバーは、このシナリオをサポートする簡略化された構文を提供します。 C# 6 以降、読み取り専用インデクサーは、次の例のように、式の本文のメンバーとして実装することができます。

[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

式の本文は `=>` で導入され、`get` キーワードは使用されないことに注意してください。 

C# 7 以降、get アクセサーと set アクセサーのどちらも、式の本文のメンバーとして実装できます。 この場合、`get` キーワードと `set` キーワードの両方を使用する必要があります。 例:

[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>インデクサーの概要  
  
-   インデクサーを使用すると、配列と同じようにオブジェクトにインデックスを作成することができます。  
  
-   `get` アクセサーは値を返します。 `set` アクセサーは値を割り当てます。  
  
-   [this](../../../csharp/language-reference/keywords/this.md) キーワードは、インデクサーの定義に使用されます。  
  
-   [value](../../../csharp/language-reference/keywords/value.md) キーワードは、`set` インデクサーによって割り当てられる値の定義に使用されます。  
  
-   インデクサーは、整数値でインデックスを指定する必要はありません。個々の検索メカニズムの定義方法によります。  
  
-   インデクサーはオーバーロードすることができます。  
  
-   インデクサーには、2 次元配列にアクセスする場合など、複数の仮パラメーターを指定できます。  
  
##  <a name="BKMK_RelatedSections">関連セクション</a>  
  
-   [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [インターフェイスのインデクサー](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)
