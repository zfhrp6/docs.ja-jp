---
title: "オブジェクトの種類 (Visual Basic) を決定する |Microsoft ドキュメント"
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
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 2486d989801fc4866a50747aa963b509a627994d
ms.lasthandoff: 03/13/2017

---
# <a name="determining-object-type-visual-basic"></a>オブジェクトの型の決定 (Visual Basic)
汎用オブジェクト変数 (つまり、変数として宣言する`Object`) 任意のクラスからオブジェクトを保持できます。 型の変数を使用するときに`Object`オブジェクトのクラスに基づいて異なるアクションを実行する必要があります。 たとえば、いくつかのオブジェクトがありますをサポートしません特定のプロパティまたはメソッドです。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オブジェクト変数に保存するオブジェクトの種類を決定する&2; つの手段を提供します。、`TypeName`関数および`TypeOf...Is`演算子。  
  
## <a name="typename-and-typeofis"></a>型名および TypeOf.します。  
 `TypeName`関数は、文字列が返され、最適な選択肢は、次のコード フラグメントで示すように、表示、オブジェクトのクラス名を保管する必要がある場合。  
  
 [!code-vb[VbVbalrOOP #&92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is`演算子には、オブジェクトの型をテストするための最適な選択肢があると等価な文字列比較を使用して、高速であるため`TypeName`です。 次のコード片では`TypeOf...Is`内で、`If...Then...Else`ステートメント。  
  
 [!code-vb[VbVbalrOOP #&93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 注意事項はここで原因です。 `TypeOf...Is`演算子が返す`True`オブジェクトは、特定の種類のまたは特定の型から派生した場合。 ほとんどすべての作業で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オブジェクトは、通常は文字列や整数などのオブジェクトの一種と考えるいくつかの要素を含めることができます。 これらのオブジェクトから派生し、 <xref:System.Object>。</xref:System.Object>からメソッドを継承 渡されるときに、`Integer`と評価された、 `Object`、`TypeOf...Is`演算子を返します`True`します。 次の例では、レポートをパラメーター`InParam`は両方とも、`Object`と`Integer`:  
  
 [!code-vb[VbVbalrOOP #&94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 次の例では、両方は使用して`TypeOf...Is`と`TypeName`内で渡されるオブジェクトの種類を決定する、`Ctrl`引数。 `TestObject`プロシージャ呼び出し`ShowType`3 つの異なる種類のコントロールにします。  
  
#### <a name="to-run-the-example"></a>例を実行するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成し、追加、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.CheckBox>コントロール、および<xref:System.Windows.Forms.RadioButton>コントロールをフォーム</xref:System.Windows.Forms.RadioButton></xref:System.Windows.Forms.CheckBox></xref:System.Windows.Forms.Button>。  
  
2.  フォームのボタンから呼び出して、`TestObject`プロシージャです。  
  
3.  次のコードをフォームに追加します。  
  
     [!code-vb[VbVbalrOOP #&95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [プロパティまたは文字列の名前を使用して、メソッドの呼び出し](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [もし。。。そうしたら。。。Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
