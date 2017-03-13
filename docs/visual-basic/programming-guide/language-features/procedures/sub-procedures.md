---
title: "Sub Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Sub procedures, about Sub procedures"
  - "statement blocks"
  - "Sub procedures, calling"
  - "procedures, calling"
  - "Sub procedures, syntax"
  - "Sub procedures"
  - "procedures, Sub"
  - "syntax, Sub procedures"
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Sub Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Sub` プロシージャは、`Sub` ステートメントと `End Sub` ステートメントで囲まれた一連の [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ステートメントです。  `Sub` プロシージャはタスクを実行した後、呼び出し元のコードに制御を返しますが、呼び出し元のコードに値を返すことはありません。  
  
 プロシージャが呼び出されるたびに、`Sub` ステートメント後の最初の実行可能なステートメントから、最初の `End Sub`、`Exit Sub`、または `Return` ステートメントまでの一連のステートメントが実行されます。  
  
 `Sub` プロシージャは、モジュール、クラス、および構造体に定義できます。  既定では `Public` に設定されます。つまり、プロシージャを定義したモジュール、クラス、または構造体へのアクセスが可能なアプリケーション内のどこからでも呼び出すことができます。  *メソッド*とは、それが定義されているモジュール、クラス、または構造体の外部からアクセスすることのできる `Sub` プロシージャまたは `Function` プロシージャのことです。  詳細については、「[Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)」を参照してください。  
  
 また、`Sub` プロシージャは、呼び出し元のコードによって渡される定数、変数、式などの引数を受け取ることができます。  
  
## 宣言の構文  
 `Sub` プロシージャを宣言する構文は次のとおりです。  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` にはアクセス レベルの他、オーバーロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。  詳細については、「[Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)」を参照してください。  
  
## パラメーター宣言  
 プロシージャの各パラメーターは、パラメーター名とデータ型を指定するという、変数を宣言するのと似た方法で宣言します。  また、引数渡しの方法およびパラメーターを省略できるかどうか、パラメーター配列かどうかも指定できます。  
  
 パラメーター リストの各パラメーターの構文は次のとおりです。  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 パラメーターを省略可能にする場合は、宣言内で既定値を指定する必要があります。  既定値を指定する構文は次のとおりです。  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### ローカル変数として扱われるパラメーター  
 制御がプロシージャに渡ると、各パラメーターはローカル変数として扱われます。  つまり、その有効期間はプロシージャの有効期間と同じで、スコープはプロシージャ全体になります。  
  
## 呼び出し構文  
 `Sub` プロシージャは、スタンドアロンの呼び出しステートメントを使って明示的に呼び出す必要があります。  式の中で名前を使って呼び出すことはできません。  省略できないすべての引数の値を指定し、引数リストをかっこで囲む必要があります。  指定する引数がない場合は、かっこを省略することもできます。  `Call` キーワードは省略できますが、指定することが推奨されています。  
  
 `Sub` プロシージャを呼び出す構文は次のとおりです。  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 `Sub` メソッドは、それが定義されているクラスの外部から呼び出すことができます。  まず、`New` キーワードを使用してクラスのインスタンスを作成するか、クラスのインスタンスを返すメソッドを呼び出す必要があります。  詳細については、「[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)」を参照してください。  その後、次の構文を使用することで、インスタンス オブジェクトの `Sub` メソッドを呼び出すことができます。  
  
 *Object*.*methodname*`[(`*argumentlist*`)]`  
  
### 宣言と呼び出しの説明  
 次の `Sub` プロシージャは、アプリケーションが実行しようとしているタスクとタイム スタンプを表示します。  アプリケーションでは、さまざまな場所から  `tellOperator`  を呼び出すことができるため、すべてのタスクの先頭にこのコードを複製する必要はありません。  呼び出し時には、引数  `task`  で文字列が渡されます。この文字列によって、開始されようとしているタスクが確認されます。  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 `tellOperator` を呼び出す一般的な例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [How to: Call an Event Handler in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)