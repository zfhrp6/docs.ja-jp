---
title: オーバー ロードされたプロパティとメソッド (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: c0aa7c4a13e049045743044a98020a1aab2cf1a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652195"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>オーバー ロードされたプロパティとメソッド (Visual Basic)

オーバー ロードは、1 つ以上のプロシージャ、インスタンス コンス トラクター、またはで同じ名前が異なる引数の型クラスのプロパティの作成です。  
  
## <a name="overloading-usage"></a>使用率をオーバー ロード

 オーバー ロードは、オブジェクト モデルで、別のデータ型を操作するプロシージャに同じ名前を使用しているときに特に便利です。 たとえば、いくつかの異なるデータ型を表示できるクラスがある`Display`次のような手順。  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 せず、オーバー ロードでもが同じで、次に示すよう各手順の種類の名前を作成する必要は。  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 オーバー ロードしやすくために使用できるデータ型の選択肢を提供するために、プロパティまたはメソッドを使用します。 たとえば、オーバー ロードされた`Display`説明以前メソッドに次のコード行のいずれか。  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 実行時に、Visual Basic は、指定したパラメーターのデータ型に基づいて適切なプロシージャを呼び出します。  
  
## <a name="overloading-rules"></a>オーバー ロードの規則

 クラスのオーバー ロードされたメンバーを作成するには、2 つ以上のプロパティまたは同じ名前のメソッドを追加します。 オーバー ロードされた派生メンバーを除く各オーバー ロードされたメンバーが異なるパラメーター リストを持つ必要があり、次の項目は、プロパティまたはプロシージャをオーバー ロードと区別する機能として使用できません。  
  
-   修飾子をなど`ByVal`または`ByRef`メンバー、またはメンバーのパラメーターに適用されています。  
  
-   パラメーターの名前  
  
-   プロシージャの戻り値の型  
  
 `Overloads`キーワード省略可能な時に、オーバー ロードはメンバーを使用していずれかのオーバー ロードされた場合、`Overloads`このキーワードはキーワード、その他のすべてのオーバー ロードされたメンバーと同じ名前で指定も必要があります。  
  
 派生クラスで同じパラメーターおよびパラメーターの型と呼ばれるプロセスをしているメンバーを持つ継承されたメンバー オーバー ロードできます*名前とシグネチャによるシャドウ*です。 場合、`Overloads`シャドウ名前とシグネチャで、メンバーの派生クラスの実装が、基底クラスで実装ではなく使用され、そのメンバーの他のすべてのオーバー ロードできるようにするのインスタンスとキーワードを使用して、派生クラスです。  
  
 場合、`Overloads`同一パラメーターとパラメーターの型を持つメンバーを持つ継承されたメンバー オーバー ロード時にキーワードを省略すると、オーバー ロードが呼び出された*名前によるシャドウ*です。 継承されたメンバーの実装を置き換える名前によるシャドウと他のすべてのオーバー ロードを置き換わります、派生クラスのインスタンスを使用できなくなります。  
  
 `Overloads`と`Shadows`修飾子両方では使用できません、同じプロパティまたはメソッドです。  
  
### <a name="example"></a>例

 次の例は、いずれかを受け取るオーバー ロードされたメソッドを作成、`String`または`Decimal`形式の金額と sales 税を含む文字列を返します。  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>この例を使用して、オーバー ロードされたメソッドを作成するには
  
1.  新しいプロジェクトを開き、という名前のクラスを追加`TaxClass`です。  
  
2.  `TaxClass` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  次の手順をフォームに追加します。  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  呼び出し、フォームにボタンを追加、`ShowTax`プロシージャから、`Button1_Click`ボタンのイベントです。  
  
5.  プロジェクトを実行し、オーバー ロードされたテストをフォーム上のボタンをクリックして`ShowTax`プロシージャです。  
  
 実行時に、コンパイラは、使用されているパラメーターに一致する適切なオーバー ロードされた関数を選択します。 ボタンをクリックすると、オーバー ロードされたメソッドが呼び出された最初、`Price`パラメーターを文字列と、メッセージは、"価格は、文字列です。 税が $$5.12"が表示されます。 `TaxAmount` 使用が呼び出される、`Decimal`値を 2 番目の時間と、メッセージ、"価格は 10 進数です。 税が $$5.12"が表示されます。  
  
## <a name="see-also"></a>関連項目

 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
