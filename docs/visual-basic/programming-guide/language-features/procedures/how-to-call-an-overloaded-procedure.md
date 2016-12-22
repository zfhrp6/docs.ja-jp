---
title: "How to: Call an Overloaded Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, overloading"
  - "procedures, calling"
  - "procedures, multiple versions"
  - "procedure calls, overloaded"
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Call an Overloaded Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プロシージャのオーバーロードの利点は、呼び出しの柔軟性にあります。  呼び出しを行うコードは、どの引数を渡す場合でも、プロシージャに渡すために必要な情報を取得し、単一のプロシージャ名で呼び出すことができます。  
  
### 複数の形式が定義されたプロシージャを呼び出すには  
  
1.  呼び出しを行うコードで、プロシージャにどのデータを渡すかを決定します。  
  
2.  プロシージャ呼び出しを通常の方法で作成し、引数リストにデータを定義します。  プロシージャに定義されている、いずれかの形式のパラメーター リストと一致するように、引数を指定してください。  
  
3.  どの形式のプロシージャを呼び出すかを判断する必要はありません。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] によって、引数リストと一致する形式に制御が渡されます。  
  
     [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md) で宣言した `post` プロシージャを呼び出す例を次に示します。  顧客 ID を取得して、それが文字列型 \(`String`\) か整数型 \(`Integer`\) かを判断し、どちらの場合でも同じプロシージャを呼び出します。  
  
     [!code-vb[VbVbcnProcedures#56](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)