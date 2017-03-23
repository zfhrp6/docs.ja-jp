---
title: "オーバー ロードされたプロパティとメソッド (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f379f04ca9b75161baf2bf2c33e87f05a9edf97
ms.lasthandoff: 03/13/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a>オーバーロードされたプロパティとメソッド (Visual Basic)
オーバー ロードは、1 つ以上のプロシージャ、インスタンス コンス トラクターで異なる引数の型が同じ名前のクラスのプロパティの作成です。  
  
## <a name="overloading-usage"></a>使用率をオーバー ロード  
 オーバー ロードは、オブジェクト モデルで、別のデータ型を操作するプロシージャに同じ名前を使用しているときに便利です。 たとえば、複数のデータ型を表示できるクラスがある`Display`次のようにプロシージャ。  
  
 [!code-vb[VbVbalrOOP #&64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 せず、オーバー ロードどおり、次に示すように、同じ場合でも各プロシージャの種類の名前を作成する必要は。  
  
 [!code-vb[VbVbalrOOP #&65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 オーバー ロードすると、使用できるデータ型の選択肢を提供するために、プロパティまたはメソッドを使用しやすきます。 たとえば、オーバー ロードされた`Display`説明以前メソッドで次のコード行のいずれか。  
  
 [!code-vb[VbVbalrOOP #&66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 実行時に[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]するパラメーターのデータ型に基づき適切なプロシージャの呼び出しを指定します。  
  
## <a name="overloading-rules"></a>オーバー ロードの規則  
 クラスのオーバー ロードされたメンバーを作成するには、2 つ以上のプロパティまたは同じ名前を持つメソッドを追加します。 オーバー ロードの派生メンバーを除く各オーバー ロードされたメンバーは、異なるパラメーター リストを持つ必要があり、次の項目は、プロパティまたはプロシージャをオーバー ロードとの差別化機能として使用できません。  
  
-   修飾子など`ByVal`または`ByRef`メンバー、またはメンバーのパラメーターに適用されています。  
  
-   パラメーターの名前  
  
-   プロシージャの戻り値の型  
  
 `Overloads` 、オーバー ロードとは、キーワードは任意ですが、メンバーを使用していずれかのオーバー ロードされた場合、`Overloads`このキーワードはキーワード、その他のすべてのオーバー ロードされたメンバーと同じ名前で指定もする必要があります。  
  
 派生クラスで継承されたメンバーを同一パラメーターとパラメーターの型と呼ばれるプロセスを持つメンバーとオーバー ロードできます*名前とシグネチャによるシャドウ*します。 場合、`Overloads`名前とシグネチャによるシャドウ、メンバーの派生クラスの実装される基本クラスの実装ではなくとそのメンバーの他のすべてのオーバー ロードは、派生クラスのインスタンスに表示される場合に、キーワードを使用します。  
  
 場合、`Overloads`キーワードを省略して、継承されたメンバーと同じパラメーターとパラメーターの型を持つメンバーを持つオーバー ロードし、オーバー ロードが呼び出されます*名前によるシャドウ*します。 継承されたメンバーの実装を置き換える名前によるシャドウおよびその他のすべてのオーバー ロードを置き換わります、派生クラスのインスタンスを使用できなくなります。  
  
 `Overloads`と`Shadows`修飾子両方では使用できません同じプロパティまたはメソッドです。  
  
### <a name="example"></a>例  
 次の例では、いずれかを受け取るオーバー ロードされたメソッド、`String`または`Decimal`形式の金額と売上税が含まれている文字列を返します。  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>この例を使用して、オーバー ロードされたメソッドを作成するには  
  
1.  新しいプロジェクトを開き、という名前のクラスを追加`TaxClass`します。  
  
2.  `TaxClass` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP #&67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  フォームに次の手順を追加します。  
  
     [!code-vb[VbVbalrOOP #&68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  呼び出し、フォームにボタンを追加、`ShowTax`プロシージャから、`Button1_Click`ボタンのイベントです。  
  
5.  プロジェクトを実行し、オーバー ロードされたをテストするフォーム上のボタンをクリックして`ShowTax`プロシージャです。  
  
 実行時に、コンパイラは、使用されているパラメーターに一致する適切なオーバー ロードされた関数を選択します。 ボタンをクリックすると、オーバー ロードされたメソッドが呼び出された最初、`Price`パラメーターを文字列と、メッセージは、"価格は、文字列です。 税金が $$5.12"が表示されます。 `TaxAmount`呼び出された、`Decimal`値&2; 回目と、メッセージ、"価格は&10; 進数です。 税金が $$5.12"が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [シャドウ](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
