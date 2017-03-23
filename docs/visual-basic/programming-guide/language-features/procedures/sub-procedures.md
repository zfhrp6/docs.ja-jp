---
title: "Sub プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
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
ms.openlocfilehash: d224fa3338ca707070ee431380578a8fdde47e07
ms.lasthandoff: 03/13/2017

---
# <a name="sub-procedures-visual-basic"></a>Sub プロシージャ (Visual Basic)
A`Sub`プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]で囲まれたステートメント、`Sub`と`End Sub`ステートメントです。 `Sub`呼び出し元のコードに値を返すことはできませんが、プロシージャは、タスクを実行し、呼び出し元のコードに制御を戻します。  
  
 そのステートメントで実行されるプロシージャが呼び出されるたびに後の最初の実行可能ステートメントで始まる、`Sub`ステートメントおよび&1; つ目で終了するまで`End Sub`、 `Exit Sub`、または`Return`ステートメントが発生しました。  
  
 定義する、`Sub`モジュール、クラス、および構造体のプロシージャです。 既定では`Public`、することができるから呼び出せる任意の場所をモジュール、クラス、または、定義された構造体へのアクセスを持つアプリケーションにします。 この言葉を*メソッド*、について説明します、`Sub`または`Function`プロシージャの定義の外部からアクセスされるモジュール、クラスまたは構造体。 詳細については、次を参照してください。[プロシージャ](./index.md)します。  
  
 A`Sub`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数を渡すことができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Sub`手順は、次のようにします。  
  
 `[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。 詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)します。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 同様にどのように変数を宣言する、パラメーター名とデータ型を指定するには、各プロシージャ パラメーターを宣言するとします。 引数渡しの方法を指定することも、パラメーターは省略可能かどうかや、パラメーター配列。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*データ型    *  
  
 パラメーターが省略可能な場合も、その宣言の一部として既定値を指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue        *  
  
### <a name="parameters-as-local-variables"></a>ローカル変数とパラメーター  
 コントロール、プロシージャに渡すと、各パラメーターは、ローカル変数として扱われます。 これは、そのスコープは、プロシージャ全体をその有効期間は、プロシージャのと同じことを意味します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Sub`プロシージャ スタンドアロン呼び出し元のステートメントを明示的にします。 式の中でその名前を使用して呼び出すことはできません。 省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。 使用、`Call`キーワードは任意ですがないことをお勧めします。  
  
 呼び出しの構文、`Sub`手順は、次のようにします。  
  
 `[Call]`  *subname* `[(` *argumentlist*`)]`  
  
 呼び出すことができます、`Sub`からこれを定義するクラスの外側のメソッドです。 最初に、使用する必要がある、`New`キーワードをクラスのインスタンスを作成またはメソッドを呼び出すには、クラスのインスタンスが返されます。 詳細については、次を参照してください。 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)します。 呼び出す次の構文を使用し、`Sub`インスタンス オブジェクトのメソッド。  
  
 *Object*.*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Sub`手順で実行しようとしてタスク、アプリケーション コンピューター演算子を説明し、タイムスタンプを表示します。 アプリケーションのすべてのタスクの開始時に、このコードを複製するのではなくはだけ`tellOperator`さまざまな場所からです。 各呼び出しで文字列を渡して、`task`開始されているタスクを識別する引数。  
  
 [!code-vb[VbVbcnProcedures&#2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`tellOperator`します。  
  
 [!code-vb[VbVbcnProcedures&#3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Function プロシージャ](./function-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [方法: 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)
