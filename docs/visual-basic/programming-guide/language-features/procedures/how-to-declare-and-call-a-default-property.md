---
title: '方法: 既定のプロパティを宣言して呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 7805ee4dcd4bad0d0624c97ccc25232e9bc31ba4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650996"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>方法: 既定のプロパティを宣言して呼び出す (Visual Basic)
A*既定プロパティ*クラスまたは構造体のプロパティで指定することがなく、コードにアクセスできます。 呼び出し元のコードは、クラスまたは構造体がない、プロパティ、およびコンテキスト プロパティへのアクセスを許可、Visual Basic が存在する場合に、そのクラスまたは構造体の既定のプロパティにアクセスを解決します。  
  
 クラスまたは構造体は最大で 1 つの既定プロパティをできます。 ただし、既定のプロパティをオーバー ロードして、という 2 つ以上のバージョンであります。  
  
 詳細については、次を参照してください。[既定](../../../../visual-basic/language-reference/modifiers/default.md)です。  
  
### <a name="to-declare-a-default-property"></a>既定のプロパティを宣言するには  
  
1.  通常の方法でプロパティを宣言します。 指定しない、`Shared`または`Private`キーワード。  
  
2.  含める、`Default`プロパティ宣言でキーワード。  
  
3.  プロパティの 1 つ以上のパラメーターを指定します。 少なくとも 1 つの引数を取らない既定のプロパティを定義することはできません。  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>既定のプロパティを呼び出す  
  
1.  それを含むクラスまたは構造体の型の変数を宣言します。  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  プロパティ名を通常含めるは式の中だけで、変数名を使用します。  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  かっこ内に引数リストを持つ変数の名前に従います。 既定のプロパティは、少なくとも 1 つの引数を受け取る必要があります。  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  プロパティの既定値を取得するには、引数リスト、または等しい、次の式で指定した変数の名前を使用 (`=`) 代入ステートメントにサインインします。  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  既定のプロパティ値を設定するには、代入ステートメントの左側にある、引数リストを持つという名前の変数を使用します。  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  他のプロパティにアクセスする場合と同様、という名前の変数と共に既定のプロパティ名を必ず指定することができます。  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>例  
 次の例では、クラスを既定のプロパティを宣言します。  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>例  
 次の例では、既定のプロパティを呼び出して`myProperty`クラス`class1`です。 次の 3 つの代入ステートメントで値を格納する`myProperty`、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼び出しは、値を読み取ります。  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 既定のプロパティの最も一般的な用途は、<xref:Microsoft.VisualBasic.Collection.Item%2A>さまざまなコレクション クラスのプロパティです。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 既定のプロパティは、ソース コードの文字のわずかな低下につながるが行えるコード読みにくくなります。 クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合は指定できません特定その参照が、クラスまたは構造体自体、または既定のプロパティにアクセスするかどうか。 これは、コンパイラ エラーまたは実行時の微妙な論理エラーを可能性があります。  
  
 常を使用して既定のプロパティのエラーの可能性を低くことができます多少、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)をチェックインするコンパイラ タイプを設定する`On`です。  
  
 使用を計画して、定義済みのクラスまたは構造体、コード内を決定する必要がありますを既定のプロパティがあるかどうかと、その場合、どのような名前です。  
  
 これらの欠点のためには、既定のプロパティを定義しないを検討してください。 コードの読みやすさも常にすべてのプロパティを明示的に参照を検討も既定のプロパティする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [既定値](../../../../visual-basic/language-reference/modifiers/default.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
