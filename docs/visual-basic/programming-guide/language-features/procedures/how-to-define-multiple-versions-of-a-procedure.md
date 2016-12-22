---
title: "How to: Define Multiple Versions of a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "procedure overloading, multiple versions"
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define Multiple Versions of a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャは*オーバーロード*することによって、複数のバージョンを定義できます。オーバーロードでは各バージョンとも同じ名前を使用しますが、パラメーター リストはそれぞれ異なります。  プロシージャをオーバーロードする目的は、互いに密接な関係にある複数のバージョンのプロシージャを、名前で区別せずに定義することにあります。  
  
 詳細については、「[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
### プロシージャの複数のバージョンを定義するには  
  
1.  定義するプロシージャの各バージョンに、`Sub` 宣言ステートメントまたは `Function` 宣言ステートメントを記述します。  すべての宣言に同じプロシージャ名を使います。  
  
2.  各宣言の `Sub` キーワードまたは `Function` キーワードの前に、[Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) キーワードを指定します。  宣言内の `Overloads` の指定は省略可能ですが、いずれかの宣言に指定した場合、すべての宣言に指定することが必要になります。  
  
3.  各宣言ステートメントの後に、特定のケースを処理するプロシージャ コードを記述します。呼び出し元のコードで指定される引数が、そのバージョンのパラメーター リストと一致するようにしてください。  呼び出し元のコードでどのパラメーターが指定されたかを調べるコードは必要ありません。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] によって、一致するプロシージャのバージョンに制御が渡されます。  
  
4.  プロシージャの各バージョンを `End Sub` ステートメントまたは `End Function` ステートメントで適切に終了します。  
  
## 使用例  
 `Sub` プロシージャを定義し、顧客の残高に対してトランザクションをポストする例を次に示します。  `Overloads` キーワードを指定して、プロシージャのバージョンを 2 つ定義しています。1 つは顧客を名前で受け取り、もう 1 つは口座番号で受け取ります。  
  
 [!code-vb[VbVbcnProcedures#72](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 呼び出し元のコードでは、顧客 ID を文字列 \(`String`\) または数値 \(`Integer`\) で取得しますが、どちらの場合でも同じ呼び出しステートメントを使用できます。  
  
 これらのバージョンの `post` プロシージャを呼び出す方法については、「[How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)」を参照してください。  
  
## コードのコンパイル  
 オーバーロードされた各バージョンは、プロシージャ名は同じでもパラメーター リストが違う点に注意してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)