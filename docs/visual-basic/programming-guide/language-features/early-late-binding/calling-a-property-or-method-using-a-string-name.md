---
title: "Calling a Property or Method Using a String Name (Visual Basic) | Microsoft Docs"
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
  - "passing operators"
  - "strings [Visual Basic], passing new operators as"
  - "objects [Visual Basic], setting properties"
  - "setting properties, object properties at run time"
  - "method calls, strings"
  - "methods [Visual Basic], calling with string names"
  - "calling methods, string names"
  - "properties [Visual Basic], setting at run time"
  - "CallByName function"
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Calling a Property or Method Using a String Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ほとんどの場合、デザイン時にオブジェクトのプロパティとメソッドを調べ、オブジェクトに適切なコードを記述できます。  ただし、オブジェクトのプロパティとメソッドをあらかじめ確認できない場合があります。また、実行時にプロパティの指定やメソッドの実行ができるような、柔軟なコードを記述する必要がある場合もあります。  
  
## CallByName 関数  
 たとえば、COM コンポーネントに演算子を渡すことによってユーザーが入力した式を評価する、クライアント アプリケーションなどが考えられます。  新しい演算子を必要とするコンポーネントに新しい関数を繰り返し追加するとします。  標準のオブジェクト アクセス方法を使用する場合は、クライアント アプリケーションの再コンパイルと再配布を行って、新しい演算子を使用できるようにする必要があります。  これを避けるには、`CallByName` 関数を使用します。この関数を使用すると、アプリケーションを変更せずに、新しい演算子を文字列として渡すことができます。  
  
 `CallByName` 関数を使用すると、実行時にプロパティやメソッドを文字列で指定できます。  `CallByName` 関数の使用方法を次に示します。  
  
 *Result* \= `CallByName`\(*Object*, *ProcedureName*, *CallType*, *Arguments*\(\)\)  
  
 1 番目の引数 *Object* には、対象とするオブジェクトの名前を指定します。  引数 *ProcedureName* には、呼び出すメソッドまたはプロパティ プロシージャの名前を文字列で指定します。  引数 *CallType* には、呼び出すプロシージャの型を表す定数を指定します。メソッド呼び出しプロシージャの場合は `Microsoft.VisualBasic.CallType.Method`、プロパティ取得プロシージャの場合は `Microsoft.VisualBasic.CallType.Get`、プロパティ設定プロシージャの場合は `Microsoft.VisualBasic.CallType.Set` を指定します。  任意で指定する引数 *Arguments* には、プロシージャに渡す引数を格納している `Object` 型の配列を指定します。  
  
 `CallByName` 関数は、現在のソリューションのクラスに対して使用できますが、一般的には、COM オブジェクトまたは [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] アセンブリのオブジェクトにアクセスするときに使用します。  
  
 たとえば、次のコードに示すように、新しい関数 `SquareRoot` を持つ `MathClass` クラスを含むアセンブリへの参照を追加するとします。  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#53)]  
  
 アプリケーションは、テキスト ボックス コントロールを使用して、呼び出すメソッドとその引数を制御できます。  たとえば、`TextBox1` に評価する式を入力し、`TextBox2` に関数の名前を入力する場合は、次のコードを使用して `TextBox1` の式に対して `SquareRoot` 関数を呼び出します。  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#54)]  
  
 `TextBox1` に「64」を入力し、`TextBox2` に「SquareRoot」を入力してから、`CallMath` プロシージャを呼び出した場合は、`TextBox1` の数値の平方根が評価されます。  この例のコードは `SquareRoot` 関数を呼び出し、`TextBox1` に "8" \(64 の平方根\) を返します。この関数の引数は必須で、評価する式を含む文字列を指定します。  `TextBox2` に不正な文字列を入力した場合、文字列にメソッドではなくプロパティの名前を指定した場合、またはメソッドに渡す必須引数が不足していた場合は、ランタイム エラーが発生します。  `CallByName` 関数を使用する場合は、信頼性の高いエラー処理コードを追加して、このようなエラーに対処する必要があります。  
  
> [!NOTE]
>  `CallByName` 関数を使用すると便利な場合もありますが、`CallByName` 関数を使用したプロシージャ呼び出しは、遅延バインディングによる呼び出しよりも速度が若干遅くなります。この関数を使用する場合には、利便性と性能面への影響とを比較検討する必要があります。  ループ内などで、繰り返し実行される関数を呼び出す場合は、`CallByName` 関数の使用によってパフォーマンスが大幅に低下する可能性があります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)