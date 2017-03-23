---
title: "方法: Visual Basic でイベント ハンドラーを呼び出す |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
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
ms.openlocfilehash: c5b300feca3415d1283d24179795a4ae92c61e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>方法 : Visual Basic でイベント ハンドラーを呼び出す
*イベント*操作または発生は、-など、マウス クリックするか、与信限度を超えています: 認識コードを記述できる、いくつかのプログラム コンポーネントによって応答します。 *イベント ハンドラー*イベントに応答を記述するコードに示します。  
  
 イベント ハンドラーに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は、`Sub`プロシージャです。 ただし、通常呼び出さないことと同じ方法の`Sub`プロシージャです。 代わりに、イベントのハンドラーとプロシージャを識別します。 これを行うか、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句と[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)変数、または、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)します。 使用して、`Handles`句内のイベント ハンドラーを宣言する既定の方法は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。 これは、統合開発環境 (IDE) でプログラミングするときに、デザイナーによって、イベント ハンドラーが書き込まれる方法です。 `AddHandler`ステートメントが実行時に動的にイベントを発生させるために適しています。  
  
 イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的にイベント ハンドラーのプロシージャを呼び出します。 イベントにアクセスできる任意のコードは実行することによって発生するようを原因となる、 [RaiseEvent ステートメント](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)します。  
  
 同じイベントには、1 つ以上のイベント ハンドラーを関連付けることができます。 場合によっては、イベントからハンドラーを切り離すこともできます。 詳細については、次を参照してください。[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)です。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>ハンドルおよび WithEvents を使用してイベント ハンドラーを呼び出す  
  
1.  で、イベントが宣言されていることを確認、 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
2.  レベルを使用して、クラス、モジュールまたはオブジェクト変数を宣言、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)キーワードです。 `As`この変数は、イベントを発生させるクラスを指定する必要があります。  
  
3.  イベント処理の宣言で`Sub`の手順を追加、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句を指定する、`WithEvents`変数、およびイベント名。  
  
4.  イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を自動的に呼び出して、`Sub`プロシージャです。 コードを使用して、`RaiseEvent`ステートメントが発生するイベントをします。  
  
     次の例は、イベントを定義し、`WithEvents`イベントを発生させるクラスを参照する変数。 イベント処理`Sub`プロシージャは、`Handles`句クラスとイベントの処理を指定します。  
  
     [!code-vb[VbVbcnProcedures&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler を使用してイベント ハンドラーを呼び出す  
  
1.  で、イベントが宣言されていることを確認、`Event`ステートメントです。  
  
2.  実行、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)イベント処理を動的に接続する`Sub`イベントにプロシージャです。  
  
3.  イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を自動的に呼び出して、`Sub`プロシージャです。 コードを使用して、`RaiseEvent`ステートメントが発生するイベントをします。  
  
     次の例、`Sub`を処理する手順、<xref:System.Windows.Forms.Form.Closing>フォームのイベント</xref:System.Windows.Forms.Form.Closing>。 次を使用して、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)に関連付けるには、 `catchClose` <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>のイベント ハンドラーとプロシージャ  
  
     [!code-vb[VbVbcnProcedures&#5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     実行することによって、イベントからイベント ハンドラーを切り離すこともできます、 [RemoveHandler ステートメント](../../../../visual-basic/language-reference/statements/removehandler-statement.md)します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [方法: プロシージャを作成します。](./how-to-create-a-procedure.md)   
 [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
