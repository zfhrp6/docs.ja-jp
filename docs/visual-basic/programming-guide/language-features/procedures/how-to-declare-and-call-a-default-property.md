---
title: "How to: Declare and Call a Default Property in Visual Basic | Microsoft Docs"
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
  - "defaults, properties"
  - "properties [Visual Basic], default"
  - "procedures, defining"
  - "default properties, in Visual Basic"
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "default properties"
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare and Call a Default Property in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*既定のプロパティ* は、コードで指定しなくてもアクセスできる、クラスまたは構造体のプロパティです。  呼び出し元のコードでクラスや構造体を指定し、プロパティを指定しなければ、コンテキストにおいてプロパティへのアクセスが許可された場合に [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] がそのクラスや構造体の既定のプロパティ \(存在する場合\) にアクセスを解決します。  
  
 クラスや構造体には、既定のプロパティを 1 つまで定義できます。  ただし、既定のプロパティはオーバーロードできるので、複数の形式の定義が可能です。  
  
 詳細については、「[Default](../../../../visual-basic/language-reference/modifiers/default.md)」を参照してください。  
  
### 既定のプロパティを宣言するには  
  
1.  通常の方法でプロパティを宣言します。  キーワード `Shared` または `Private` を指定しないでください。  
  
2.  宣言に `Default` キーワードを含めます。  
  
3.  プロパティにパラメーターを少なくとも 1 つ指定します。  引数を 1 つも受け取らない既定のプロパティは定義できません。  
  
     [!code-vb[VbVbcnProcedures#17](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### 既定のプロパティを呼び出すには  
  
1.  既定のプロパティを含むクラスや構造体の型を使って変数を宣言します。  
  
     [!code-vb[VbVbcnProcedures#16](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  通常はプロパティ名を指定する式に、変数名だけを指定します。  
  
     [!code-vb[VbVbcnProcedures#21](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  変数名に続けて、引数をかっこで囲んで記述します。  既定のプロパティは、少なくとも 1 つの引数を受け取る必要があります。  
  
     [!code-vb[VbVbcnProcedures#20](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  既定のプロパティの値を取得するには、引数リストを指定した変数名を式の中に記述する、つまり代入ステートメントの等号 \(`=`\) 記号の後に記述します。  
  
     [!code-vb[VbVbcnProcedures#15](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  既定のプロパティに値を設定するには、引数リストを指定した変数名を代入ステートメントの左側に記述します。  
  
     [!code-vb[VbVbcnProcedures#14](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  既定のプロパティ名は、他のプロパティにアクセスする場合と同じように、変数名を使っていつでも指定できます。  
  
     [!code-vb[VbVbcnProcedures#19](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## 使用例  
 クラスに既定のプロパティを宣言するコード例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#12](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## 使用例  
 `class1` クラスの既定のプロパティ `myProperty` を呼び出す方法は、次の例のようになります。  3 つの代入ステートメントが `myProperty` に値を格納し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> の呼び出しによって値が読み込まれます。  
  
 [!code-vb[VbVbcnProcedures#13](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 既定のプロパティが最もよく使用されるのは、さまざまなコレクション クラスの <xref:Microsoft.VisualBasic.Collection.Item%2A> プロパティです。  
  
## 信頼性の高いプログラミング  
 既定のプロパティを使用すると、ソース コードに記述する文字の量が少し減りますが、コードの読みやすさが低下します。  呼び出しコードからクラスや構造体が明確に区別できない場合にクラス名または構造体名を使って参照すると、その参照がクラスと構造体のどちらに対するものなのか、また既定のプロパティを参照しているかどうかもはっきりしません。  このような場合、コンパイル エラーまたはランタイムの論理エラーが発生する可能性があります。  
  
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)を使ってコンパイラの型チェックを常に `On` に設定しておくことで、既定のプロパティのエラーが発生する可能性をいくらか低下できます。  
  
 定義済みのクラスまたは構造体を使ってコードを作成する場合には、既定のプロパティが設定されているかどうかを調べ、設定されていればその名前を確認しておくことが必要です。  
  
 以上のような難点があるため、既定のプロパティは定義しないことをお勧めします。  コードの読みやすさの点からも、すべてのプロパティを、既定のプロパティであっても明示的に参照することを心がけてください。  
  
## 参照  
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Default](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)