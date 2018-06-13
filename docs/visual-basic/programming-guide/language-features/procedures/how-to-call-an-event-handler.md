---
title: '方法 : Visual Basic でイベント ハンドラーを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 4e6aeaee8027e462dcdf80cae34b4b246fd58cf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652683"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>方法 : Visual Basic でイベント ハンドラーを呼び出す
*イベント*アクションまたはイベントの発生は、-、マウスなどクリックやクレジットの上限を超えています: 認識によってプログラム コンポーネントによって、コードを記述できます応答します。 *イベント ハンドラー*イベントに応答を記述するコードです。  
  
 Visual Basic でイベント ハンドラーは、`Sub`プロシージャです。 ただし、通常呼び出さないことと同じ方法とその他の`Sub`プロシージャです。 代わりに、イベントのハンドラーとしてプロシージャを識別します。 これを行うか、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句と[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)変数、または、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)です。 使用して、`Handles`句は、Visual Basic では、イベント ハンドラーを宣言する既定の方法です。 これは、統合開発環境 (IDE) でプログラミングするときにイベント ハンドラーが、デザイナーによって書き込まれる方法です。 `AddHandler`ステートメントが実行時に動的にイベントを発生させるために適しています。  
  
 イベントが発生すると、Visual Basic は自動的にイベント ハンドラーのプロシージャを呼び出します。 イベントへのアクセスを持つあらゆるコードそれが原因で実行することによって発生する、 [RaiseEvent ステートメント](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)です。  
  
 同じイベントには、1 つ以上のイベント ハンドラーを関連付けることができます。 場合によっては、イベントからハンドラーを切り離すこともできます。 詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>ハンドルおよび WithEvents を使用して、イベント ハンドラーを呼び出す  
  
1.  必ず、イベントが、 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
2.  レベルを使用して、クラス、モジュールまたはオブジェクト変数を宣言、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)キーワード。 `As`この変数は、イベントを発生させるクラスを指定する必要があります。  
  
3.  イベント処理の宣言で`Sub`の手順を追加、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句を指定する、`WithEvents`変数、およびイベント名。  
  
4.  Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャです。 コードを使用して、`RaiseEvent`ステートメントに発生するイベントです。  
  
     次の例は、イベントを定義し、`WithEvents`イベントを発生させるクラスを参照する変数。 イベント処理`Sub`プロシージャの使用、`Handles`句をクラスと処理イベントを指定します。  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler を使用して、イベント ハンドラーを呼び出す  
  
1.  必ず、イベントが、`Event`ステートメントです。  
  
2.  実行、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)イベント処理を動的に接続する`Sub`イベントを持つプロシージャ。  
  
3.  Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャです。 コードを使用して、`RaiseEvent`ステートメントに発生するイベントです。  
  
     次の例では定義、`Sub`を処理するプロシージャ、<xref:System.Windows.Forms.Form.Closing>フォームのイベントです。 次を使用して、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)に関連付けるには、`catchClose`のイベント ハンドラーとプロシージャ<xref:System.Windows.Forms.Form.Closing>です。  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     実行することによってイベントからイベント ハンドラーの関連付けを解除することができます、 [RemoveHandler ステートメント](../../../../visual-basic/language-reference/statements/removehandler-statement.md)です。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [方法 : プロシージャを作成する](./how-to-create-a-procedure.md)  
 [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
