---
title: "How to: Overload a Procedure that Takes Optional Parameters (Visual Basic) | Microsoft Docs"
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
  - "procedures, parameters"
  - "procedure overloading, optional parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャに 1 つ以上の [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) パラメーターがある場合、いずれかの暗黙のオーバーロードに対応するオーバーロードされたバージョンを定義することはできません。  詳細については、「[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)」の「省略可能なパラメーターの暗黙のオーバーロード」を参照してください。  
  
## 省略可能なパラメーターが 1 つの場合  
  
#### 省略可能なパラメーターを 1 つ取るプロシージャをオーバーロードするには  
  
1.  パラメーター リストに省略可能なパラメーターを含む `Sub` または `Function` の宣言ステートメントを記述します。  このオーバーロードされたバージョンでは `Optional` キーワードを使用しないでください。  
  
2.  `Sub` または `Function` キーワードの前に [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) キーワードを指定します。  
  
3.  呼び出し元のコードが省略可能な引数を渡してきた場合に実行するプロシージャ コードを記述します。  
  
4.  状況に応じて `End Sub` ステートメントか `End Function` ステートメントでプロシージャを終了します。  
  
5.  2 つ目の宣言ステートメントは、パラメーター リストに省略可能なパラメーターを含めず、その他は最初の宣言と同じように記述します。  
  
6.  呼び出し元のコードが省略可能な引数を渡さなかった場合に実行するプロシージャ コードを記述します。  状況に応じて `End Sub` ステートメントか `End Function` ステートメントでプロシージャを終了します。  
  
     次の例では、省略可能なパラメーターを使用するよう定義されたプロシージャ、オーバーロードされた同等の 2 つのプロシージャ、そして最後に、無効なオーバーロードされたバージョンと有効なオーバーロードされたバージョンを示します。  
  
     [!code-vb[VbVbcnProcedures#59](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_1_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_1_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_1_3.vb)]  
  
## 省略可能なパラメーターが複数ある場合  
 省略可能なパラメーターが複数あるパラメーターの場合、通常は 2 つ以上のオーバーロードされたバージョンが必要です。  たとえば、省略可能なパラメーターが 2 つあり、呼び出し元のコードがいずれかのパラメーターを渡すか渡さないかを、もう 1 つのパラメーターの有無に関係なく決める場合、オーバーロードされたバージョンは 4 つ \(渡される引数の組み合わせの数\) 必要です。  
  
 省略可能なパラメーターの数が増えると、オーバーロードはより複雑になります。  渡される引数の組み合わせの中にあり得ないものはないとすると、省略可能なパラメーターの数が N のとき、オーバーロードされたバージョンは 2 ^ N 個必要です。  オーバーロードされたバージョンをすべて定義する意味があるかどうかは、プロシージャの性質によって判断します。  
  
#### 省略可能なパラメーターを複数取るプロシージャをオーバーロードするには  
  
1.  省略可能な引数を、どのような組み合わせで受け取ることができるかをプロシージャのロジックから判断します。  1 つの省略可能なパラメーターが、他の省略可能なパラメーターに依存している場合、受け入れられない組み合わせが出てくることがあります。  たとえば、配偶者の名前を受け取るパラメーターと、配偶者の年齢を受け取るパラメーターがある場合、年齢は含まれるが名前が含まれない組み合わせは受け入れられません。  
  
2.  省略可能な引数の、受け入れ可能な組み合わせそれぞれに対し、対応するパラメーター リストを定義する `Sub` または `Function` 宣言ステートメントを記述します。  `Optional` キーワードは使用しないでください。  
  
3.  各定義では、`Sub` または `Function` キーワードの前に [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) キーワードを指定します。  
  
4.  各宣言に続いて、呼び出し元のコードが、宣言のパラメーター リストに対応する引数のリストを渡してきた場合に実行するプロシージャ コードを記述します。  
  
5.  状況に応じて `End Sub` ステートメントか `End Function` ステートメントで各プロシージャを終了します。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)