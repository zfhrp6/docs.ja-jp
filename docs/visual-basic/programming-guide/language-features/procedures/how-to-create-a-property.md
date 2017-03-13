---
title: "How to: Create a Property (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "properties [Visual Basic]"
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティは `Property` ステートメントと `End Property` ステートメントで囲まれた部分に定義します。  この内部に、`Get` プロシージャか `Set` プロシージャ、またはその両方を定義します。  プロパティのコードは、すべてこれらのプロシージャの内部に作成します。  
  
 `Get` プロシージャはプロパティの値を取得し、`Set` プロシージャは値を格納します。  プロパティのアクセスを読み取り\/書き込みにする場合は、両方のプロシージャを定義する必要があります。  読み取り専用のプロパティにするには `Get` だけを定義し、書き込み専用のプロパティにするには `Set` だけを定義します。  
  
### プロパティを作成するには  
  
1.  プロパティやプロシージャの外側で [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) を記述し、続けて `End Property` ステートメントを記述します。  
  
2.  プロパティがパラメーターを受け取る場合は、`Property` キーワードの後ろにプロシージャ名を指定し、続けてパラメーター リストをかっこで囲んで記述します。  
  
3.  かっこの後ろに `As` 句を記述して、プロパティの値のデータ型を指定します。  データ型は、書き込み専用のプロパティの場合でも指定する必要があります。  
  
4.  `Get` プロシージャと `Set` プロシージャを、必要に応じて追加します。  方法については、以降を参照してください。  
  
### プロパティ値を取得する Get プロシージャを作成するには  
  
1.  `Property` ステートメントと `End Property` ステートメントの間に [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md) を記述し、続けて `End Get` ステートメントを記述します。  `Get` プロシージャにパラメーターを定義する必要はありません。  
  
2.  `Get` ステートメントと `End Get` ステートメントの間に、プロパティ値を取得するコードを定義します。  このコードには、プロパティ値を生成して返す処理の他に、計算を行ったりデータを操作したりする処理を含めることができます。  
  
3.  プロパティの値を呼び出し元のコードに返すには、`Return` ステートメントを使用します。  
  
 読み取り\/書き込みプロパティ、および読み取り専用プロパティを作成する場合は、`Get` プロシージャを記述する必要があります。  書き込み専用プロパティに `Get` プロシージャを定義することはできません。  
  
### プロパティ値を書き込む Set プロシージャを作成するには  
  
1.  `Property` ステートメントと `End Property` ステートメントの間に [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md) を記述し、続けて `End Set` ステートメントを記述します。  
  
2.  `Set` ステートメント内で、キーワード `Set` の後ろにパラメーター リストをかっこで囲んで指定します。  このパラメーター リストには、呼び出し元のコードから渡される値を受け取るための値パラメーターを、最低でも 1 つ定義する必要があります。  この値パラメーターの既定の名前は `Value` ですが、必要であれば別の名前を使うこともできます。  値パラメーターのデータ型は、プロパティ自体と同じであることが必要です。  
  
3.  `Set` ステートメントと `End Set` ステートメントの間に、値をプロパティに格納するコードを定義します。  このコードには、プロパティ値を検査して格納する処理の他に、計算を行ったりデータを操作したりする処理を含めることができます。  
  
4.  呼び出し元のコードから渡された値を受け取るには、値パラメーターを使用します。  この値は、代入ステートメントに直接格納することも、格納する値を内部的に計算するために式の中で使用することもできます。  
  
 読み取り\/書き込みプロパティ、および書き込み専用プロパティを作成する場合は、`Set` プロシージャを記述する必要があります。  読み取り専用プロパティに `Set` プロシージャを定義することはできません。  
  
## 使用例  
 次の例は、読み取り\/書き込みプロパティを作成して、ファースト ネームとラスト ネームの 2 つの部分で構成されるフル ネームを格納します。  呼び出しコードが `fullName` を読み込むと、`Get` プロシージャが 2 つの部分を組み合わせてフル ネームを返します。  呼び出しコードが新しいフル ネームを代入すると、`Set` プロシージャはそれを 2 つの部分に分割します。  フル ネームに空白が含まれない場合は、全体をファースト ネームとして格納します。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 `fullName` の Property プロシージャを呼び出す一般的な例は次のとおりです。  最初の呼び出しでプロパティ値が設定され、2 番目の呼び出しで値が取得されます。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)