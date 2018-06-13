---
title: Sub プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 3286df1a5babfcf7d6b759ff5c9a920bb44f51ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652566"
---
# <a name="sub-procedures-visual-basic"></a>Sub プロシージャ (Visual Basic)
A`Sub`プロシージャは、一連の Visual Basic ステートメントで囲まれた、`Sub`と`End Sub`ステートメントです。 `Sub`呼び出しコードに値を返さないが、プロシージャは、タスクを実行し、呼び出し元のコードにコントロールを返します。  
  
 プロシージャが呼び出されるたびにそのステートメントが実行される後の最初の実行可能ステートメントで始まる、`Sub`ステートメントと最初で終了するまで`End Sub`、 `Exit Sub`、または`Return`ステートメントが発生しました。  
  
 定義することができます、`Sub`モジュール、クラス、および構造体」の手順です。 既定では`Public`、することができる呼び出すことができます、どこからでも、モジュール、クラス、またはそれを定義する構造体へのアクセス権を持つアプリケーションでします。 用語、*メソッド*、について説明します、`Sub`または`Function`プロシージャの定義の外部からアクセスされるモジュール、クラスまたは構造体。 詳細については、「[プロシージャ](./index.md)」を参照してください。  
  
 A`Sub`プロシージャは、定数、変数、または式で、呼び出し元のコードに渡されるなどの引数を渡すことができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Sub`手順のとおりです。  
  
 `[` *修飾子* `] Sub` *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウ処理に関する情報を指定できます。 詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)です。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 同様に宣言する方法、変数、パラメーター名とデータ型を指定するには、各プロシージャ パラメーターを宣言するとします。 引き渡し方法を指定することも、パラメーターは省略可能かどうかや、パラメーター配列。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*データ型*  
  
 パラメーターが省略可能な場合は、宣言の一部として既定値も指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>ローカル変数としてパラメーター  
 コントロール、プロシージャに渡すと、各パラメーターは、ローカル変数として扱われます。 これは、その有効期間は、プロシージャのと同じことと、そのスコープは、プロシージャ全体を意味します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Sub`プロシージャ、スタンドアロンの呼び出し元ステートメントを明示的にします。 式の中でその名前を使用して呼び出すことはできません。 省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。 使用、`Call`キーワードは任意ですがないことをお勧めします。  
  
 呼び出しの構文、`Sub`手順のとおりです。  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 呼び出すことができます、`Sub`からそれを定義するクラスの外側のメソッドです。 最初に、使用する必要がある、`New`キーワードをクラスのインスタンスを作成またはメソッドを呼び出すには、クラスのインスタンスが返されます。 詳細については、次を参照してください。 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)です。 呼び出して、次の構文を使用する、`Sub`インスタンス オブジェクトのメソッド。  
  
 *オブジェクト*.*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Sub`の手順では、コンピューターの演算子、アプリケーションは、実行しようとしているタスクともタイムスタンプが表示されます。 すべてのタスクの開始時にこのコードを複製するには、代わりに、アプリケーションだけを呼び出す`tellOperator`さまざまな場所からします。 呼び出しごとに文字列を渡して、`task`開始されているタスクを識別する引数。  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`tellOperator`です。  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [方法: Visual Basic では、イベント ハンドラーを呼び出します](./how-to-call-an-event-handler.md)
