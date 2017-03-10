---
title: "How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic) | Microsoft Docs"
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
  - "procedure overloading, indefinite number of parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, overloading"
  - "procedures, multiple versions"
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャに [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) パラメーターがある場合、パラメーター配列として 1 次元配列を使用するオーバーロードされたバージョンを定義することはできません。  詳細については、「[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)」の「パラメーター ParamArray の暗黙のオーバーロード」を参照してください。  
  
### 可変数のパラメーターを持つプロシージャをオーバーロードするには  
  
1.  プロシージャと呼び出し元のコード ロジックが、`ParamArray` パラメーターよりもオーバーロードされたバージョンを有効に活用していることを確認します。  「[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)」の「オーバーロードと ParamArray」を参照してください。  
  
2.  パラメーター リストの可変部分で、プロシージャが受け取る値の数を確認します。  これには、値がない場合も、単独の 1 次元配列の場合も含まれます。  
  
3.  受け入れ可能な値のそれぞれの数に対し、対応するパラメーター リストを定義する `Sub` または `Function` 宣言ステートメントを記述します。  このオーバーロードされたバージョンでは `Optional` または `ParamArray` キーワードを使用しないでください。  
  
4.  各定義では、`Sub` または `Function` キーワードの前に [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) キーワードを指定します。  
  
5.  各宣言に続いて、呼び出し元のコードが、宣言のパラメーター リストに対応する値を渡してきた場合に実行するプロシージャ コードを記述します。  
  
6.  状況に応じて `End Sub` ステートメントか `End Function` ステートメントで各プロシージャを終了します。  
  
## 使用例  
 次の例では、[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) パラメーターで定義されたプロシージャを示し、これに相当する一連のオーバーロードされたプロシージャを示します。  
  
 [!code-vb[VbVbcnProcedures#69](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_0_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_0_2.vb)]  
  
 このようなプロシージャは、パラメーター配列として 1 次元配列を受け取るパラメーター リストではオーバーロードできません。  ただし、他の暗黙のオーバーロードのシグネチャは使用できます。  次の宣言はこのことを示しています。  
  
 [!code-vb[VbVbcnProcedures#71](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-overload-a-proced_0_3.vb)]  
  
 オーバーロードされたバージョンのコードでは、呼び出し元のコードが `ParamArray` パラメーターに 1 つ以上の値を渡しているか、また、いくつ渡しているかをテストする必要はありません。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は呼び出し元の引数リストに一致するバージョンにコントロールを渡します。  
  
## コードのコンパイル  
 `ParamArray` パラメーターを持つプロシージャは、一連のオーバーロードされたバージョンと同等なので、このプロシージャを、これらの暗黙のオーバーロードのいずれかに対応するパラメーター リストでオーバーロードすることはできません。  詳細については、「[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)」を参照してください。  
  
## .NET Framework セキュリティ  
 無限に増大する配列を扱う場合、アプリケーション内部の容量を超過してしまう可能性があります。  パラメーターの配列を受け取る場合、呼び出し元のコードが渡す配列の長さをテストし、アプリケーションに対して大きすぎるようであれば、適切な手順を実行してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)