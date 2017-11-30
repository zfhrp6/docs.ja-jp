---
title: "オブジェクトの型の決定 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a>オブジェクトの型の決定 (Visual Basic)
汎用オブジェクト変数 (つまり、変数として宣言する`Object`) 任意のクラスからオブジェクトを保持できます。 型の変数を使用するときに`Object`オブジェクトのクラスに基づいて異なるアクションを実行する必要があります。 たとえば、一部のオブジェクト可能性がありますサポートされていません、特定のプロパティまたはメソッドです。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]オブジェクト変数に保存するオブジェクトの種類を決定する 2 つの手段を提供します。、`TypeName`関数および`TypeOf...Is`演算子。  
  
## <a name="typename-and-typeofis"></a>TypeName および TypeOf しています.します。  
 `TypeName`関数は、文字列を返し、最適な選択肢は、次のコード フラグメントで示すように、オブジェクトのクラス名を表示または保存する必要がある場合。  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is`と等価な文字列比較を使用して、高速になっているために、演算子は、オブジェクトの型をテストするための最適な選択肢`TypeName`です。 次のコード フラグメントを使用して`TypeOf...Is`内で、`If...Then...Else`ステートメント。  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 警告は due します。 `TypeOf...Is`演算子を返します`True`オブジェクトを特定の種類、または特定の型から派生した場合。 ほとんどの場合と[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]は、通常文字列や整数などのオブジェクトと考えるいくつかの要素を含め、オブジェクトが含まれます。 これらのオブジェクトから派生するためのメソッドを継承<xref:System.Object>です。 渡されたときに、`Integer`を評価および`Object`、`TypeOf...Is`演算子を返します`True`です。 次の例では、レポートをパラメーター`InParam`は両方とも、`Object`と`Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 次の例では、両方は使用して`TypeOf...Is`と`TypeName`内で渡されるオブジェクトの種類を判断する、`Ctrl`引数。 `TestObject`プロシージャ呼び出し`ShowType`3 つの異なる種類のコントロールとします。  
  
#### <a name="to-run-the-example"></a>例を実行するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成し、追加、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.CheckBox>コントロール、および<xref:System.Windows.Forms.RadioButton>をフォームにコントロールです。  
  
2.  フォーム上のボタンから呼び出し、`TestObject`プロシージャです。  
  
3.  次のコードをフォームに追加します。  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [文字列名によるプロパティまたはメソッドの呼び出し](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [If...Then...Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
