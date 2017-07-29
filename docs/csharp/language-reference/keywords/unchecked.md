---
title: "unchecked (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
dev_langs:
- CSharp
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
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
ms.openlocfilehash: 5878a2412e6c85da85b1a3b8c2a8255b51e67137
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="unchecked-c-reference"></a>unchecked (C# リファレンス)
`unchecked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを抑制するために使用します。  
  
 unchecked コンテキストでは、式が変換先の型の範囲外の値を生成した場合に、オーバーフローが検出されません。 たとえば、次の例では、`unchecked` ブロックまたは式で計算が行われるため、結果が integer に対して大きすぎるという事実が無視され、`int1` には-2,147,483,639 の値が割り当てられます。  
  
 [!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 `unchecked` 環境が削除されると、コンパイル エラーが発生します。 式のすべての用語が定数なので、コンパイル時にはオーバーフローを検出できます。  
  
 非定数の用語を含む式は、実行時およびコンパイル時に既定ではチェックされません。 checked 環境を有効にする方法については、「[checked](../../../csharp/language-reference/keywords/checked.md)」をご覧ください。  
  
 オーバーフローのチェックには時間がかかるため、オーバーフローの危険性がない状況では、unchecked コードを使用することで、パフォーマンスを改善できる可能性があります。 ただし、オーバーフローの可能性がある場合は、checked 環境を使用してください。  
  
## <a name="example"></a>例  
 この例では、`unchecked` キーワードの使用方法を示します。  
  
 [!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)

