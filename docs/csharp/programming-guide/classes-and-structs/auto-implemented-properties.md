---
title: 自動実装するプロパティ (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 756e235dacc3fcb2bf741d1d426e8dfcb53bf19b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="auto-implemented-properties-c-programming-guide"></a>自動実装するプロパティ (C# プログラミング ガイド)
C# 3.0 以降では、自動実装プロパティを使用することで、プロパティ アクセサーに追加のロジックが必要ない場合は、プロパティをより簡潔に宣言できます。 これにより、クライアント コードでオブジェクトを作成することも可能になります。 次の例に示すようにプロパティを宣言する場合、コンパイラによって、プロパティの `get` および `set` アクセサーを介してのみアクセスできる、プライベートの匿名バッキング フィールドが作成されます。  
  
## <a name="example"></a>例  
 次の例に、自動実装プロパティを持つ簡単なクラスを示します。  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 C# 6 以降では、フィールドと同様に自動実装プロパティを初期化することができます。  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 前の例に示したクラスは、変更可能です。 クライアント コードは、オブジェクト内の値を作成後に変更できます。 データだけでなく、重要な動作 (メソッド) も含まれる複雑なクラスでは、多くの場合、パブリック プロパティが必要です。 ただし、値 (データ) のセットをカプセル化しているだけで、動作をほとんど、またはまったく含まない小さなクラスや構造体の場合は、set アクセサーを [private](../../../csharp/language-reference/keywords/private.md) (コンシューマーからは変更できない) として宣言するか、または get アクセサー (コンストラクターを除くすべての場所で変更できない) のみを宣言することで、オブジェクトを変更不可能にする必要があります。  詳細については、「[方法: 自動実装するプロパティを使用して簡易クラスを実装する](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」を参照してください。  
  
 属性は、自動実装プロパティでは使用できますが、ソース コードからアクセスできないバッキング フィールドでは、当然使用できません。 プロパティのバッキング フィールドで属性を使用する必要がある場合は、標準プロパティを作成してください。  
  
## <a name="see-also"></a>参照  
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)
