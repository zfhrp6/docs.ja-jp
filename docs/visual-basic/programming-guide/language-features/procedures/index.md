---
title: "Procedures in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, structured code"
  - "Visual Basic code, procedures"
  - "procedures, types of"
  - "structured code, procedures"
  - "procedures"
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*プロシージャ*は、宣言ステートメント \(`Function`、`Sub`、`Operator`、`Get`、`Set`\) とそれに対応する `End` 宣言に囲まれた [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ステートメントのブロックです。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、すべての実行可能なステートメントはプロシージャ内部に収める必要があります。  
  
## プロシージャの呼び出し  
 プロシージャは、コード内の他の場所で呼び出します。  これを*プロシージャ呼び出し*と呼びます。  実行が完了すると、そのプロシージャを呼び出したコードに制御を返します。このコードは、*呼び出し元のコード*と呼ばれます。  呼び出し元のコードは、ステートメント、またはステートメント内の式であり、プロシージャを名前で指定して制御を渡します。  
  
## プロシージャからの復帰  
 プロシージャは、実行の終了時に制御を呼び出し元のコードに返します。  これを行うには、[Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md)、プロシージャの適切な [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) ステートメント、またはプロシージャの [End \<keyword\> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) ステートメントを使用します。  呼び出し元のコードのプロシージャ呼び出しの直後に制御が返されます。  
  
-   `Return` ステートメントを使うと、制御はすぐに呼び出し元のコードに返されます。  `Return` ステートメントの後にあるステートメントは実行されません。  同じプロシージャ内に、複数の `Return` ステートメントを定義できます。  
  
-   `Exit Sub` ステートメントまたは `Exit Function` を使うと、制御はすぐに呼び出し元のコードに返されます。  `Exit` ステートメントの後にあるステートメントは実行されません。  同じプロシージャに複数の `Exit` ステートメントを定義できます。また、`Return` ステートメントと `Exit` ステートメントを同じプロシージャに混在させることもできます。  
  
-   プロシージャに `Return` ステートメントまたは `Exit` ステートメントがない場合、プロシージャ本体にある最後のステートメントの後に `End Sub` または `End Function`、`End Get`、または `End Set` が追加されます。  `End` ステートメントは、すぐに制御を呼び出し元のコードに返します。  プロシージャ内には `End` ステートメントを 1 つだけ指定できます。  
  
## パラメーターと引数  
 ほとんどの場合、プロシージャは、呼び出されるたびに異なるデータを操作する必要があります。  この情報は、プロシージャ呼び出しの一部としてプロシージャに渡します。  プロシージャには 0 個以上の*パラメーター*を定義します。各パラメーターは、プロシージャに渡す値を表します。  プロシージャ定義における各パラメーターに対応するのが、プロシージャ呼び出しにおける*引数*です。  引数は、プロシージャ呼び出しでそれに対応するパラメーターに渡す値を表します。  
  
## プロシージャの種類  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で使用されるプロシージャには、次の種類があります。  
  
-   [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) は、アクションを実行しますが、呼び出し元のコードに値を返すことはありません。  
  
-   イベント処理プロシージャは、`Sub` プロシージャの一種であり、ユーザーによる操作やプログラムの動作によって発生したイベントに応答して実行されます。  
  
-   [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) は、呼び出し元のコードに値を返します。  呼び出し元に戻る前に、他のアクションを実行できます。  
  
-   [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) は、オブジェクトまたはモジュールのプロパティの値を取得および設定します。  
  
-   [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) は、オペランドの 1 つまたは両方が新しく定義されたクラスまたは構造体である場合に、標準の動作を定義します。  
  
-   [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) では、通常のパラメーターに加え、1 つ以上の*型パラメーター*が定義されるため、呼び出し元のコードでは呼び出しのたびに特定のデータ型を渡すことができます。  
  
## プロシージャと構造化コード  
 アプリケーションの実行可能コードのすべての行は、なんらかのプロシージャ \(`Main`、`calculate`、`Button1_Click` など\) の中に記述する必要があります。  大きなプロシージャがある場合は、いくつかに分割すると、アプリケーションのコードが読みやすくなります。  
  
 プロシージャは、頻繁に使用される計算、テキストやコントロールの操作、データベースの操作など、繰り返し実行されるタスクや共有されているタスクを実行するのに便利です。  プロシージャは、コード内のさまざまな場所から呼び出すことができるため、アプリケーションの基本的な構成要素として使用できます。  
  
 プロシージャでコードを構成すると、次の利点があります。  
  
-   プロシージャを使うと、プログラムを個別の論理単位に分割できます。  プロシージャごとにデバッグする方が、プロシージャに分割されていないプログラム全体をデバッグするよりも簡単です。  
  
-   あるプログラム用に開発したプロシージャは、多くの場合、ほとんど変更せずに他のプログラムで使用できます。  同じコードを何度も書かなくて済みます。  
  
## 参照  
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)