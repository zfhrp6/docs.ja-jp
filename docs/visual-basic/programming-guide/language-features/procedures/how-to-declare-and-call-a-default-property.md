---
title: "方法: 宣言し、Visual Basic では、既定のプロパティを呼び出して |Microsoft ドキュメント"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: ce98e7fe72a395f6c4cde481feaa60be28c6fcc3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>方法: 既定のプロパティを宣言して呼び出す (Visual Basic)
A*既定プロパティ*クラスまたは構造体のプロパティで、指定しなくても、コードにアクセスできます。 クラスまたは構造体がプロパティではなく、名前のコードを呼び出すと、コンテキスト プロパティへのアクセスを許可する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]が存在する場合に、そのクラスまたは構造体の既定のプロパティにアクセスを解決します。  
  
 クラスまたは構造体が多くて&1; つの既定のプロパティです。 ただし、という&2; つ以上のバージョンがあるし、を既定のプロパティをオーバー ロードすることができます。  
  
 詳細については、次を参照してください。[既定](../../../../visual-basic/language-reference/modifiers/default.md)します。  
  
### <a name="to-declare-a-default-property"></a>既定のプロパティを宣言するには  
  
1.  通常の方法でプロパティを宣言します。 指定しない、`Shared`または`Private`キーワードです。  
  
2.  含める、`Default`プロパティの宣言でキーワードです。  
  
3.  プロパティの&1; つ以上のパラメーターを指定します。 少なくとも&1; つの引数を取らない既定のプロパティを定義することはできません。  
  
     [!code-vb[VbVbcnProcedures&17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>既定のプロパティを呼び出す  
  
1.  含むクラスまたは構造体の型の変数を宣言します。  
  
     [!code-vb[VbVbcnProcedures&#16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  プロパティ名を通常は式の中だけで、変数名を使用します。  
  
     [!code-vb[VbVbcnProcedures #&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  かっこで囲まれた引数リストを持つ変数名に従います。 既定のプロパティは、少なくとも&1; つの引数を受け取る必要があります。  
  
     [!code-vb[VbVbcnProcedures&#20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  プロパティの既定値を取得するには、式の中で、または等しい、次の引数リストを含む、名前の変数を使用 (`=`)、代入ステートメントにサインインします。  
  
     [!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  プロパティの既定値を設定するには、代入ステートメントの左側にある、引数リストを含むという名前の変数を使用します。  
  
     [!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  その他のプロパティにアクセスする場合と同様には、必ずという名前の変数と共に既定のプロパティ名を指定することができます。  
  
     [!code-vb[VbVbcnProcedures&#19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>例  
 次の例では、クラスを既定のプロパティを宣言します。  
  
 [!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>例  
 次の例では、既定のプロパティを呼び出して`myProperty`クラスに`class1`します。 次の&3; つの代入ステートメント内の値を格納する`myProperty`、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼び出しは、値を読み取ります</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。  
  
 [!code-vb[VbVbcnProcedures&#13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 既定のプロパティの最も一般的な用途は、<xref:Microsoft.VisualBasic.Collection.Item%2A>さまざまなコレクション クラスのプロパティ</xref:Microsoft.VisualBasic.Collection.Item%2A>。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 既定のプロパティは、ソース コードの文字のわずかな低下につながるはできるコード読み取るが困難です。 クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合は使用できません特定その参照は、クラスまたは構造体そのものを既定のプロパティにアクセスするかどうか。 コンパイラ エラーまたはランタイム ロジックの微妙なエラーにつながります。  
  
 常を使用して、既定のプロパティのエラーの可能性を低くことができます多少、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックのコンパイラ タイプを設定する`On`です。  
  
 使用を計画して、定義済みのクラスまたは構造体コードでは、決定する必要があります、既定のプロパティがあるかどうか、およびその場合、どのような名前です。  
  
 このような短所は、ためには、既定のプロパティを定義しないことを考慮する必要があります。 コードを読みやすくは、常に明示的に参照するすべてのプロパティについても考慮も既定のプロパティ必要があります。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ プロシージャ](./property-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [既定値](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)   
 [方法: プロパティを作成します。](./how-to-create-a-property.md)   
 [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)   
 [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)   
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
