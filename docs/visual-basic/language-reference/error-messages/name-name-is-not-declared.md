---
title: "Name &#39;&lt;name&gt;&#39; is not declared | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30451"
  - "vbc30451"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30451"
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Name &#39;&lt;name&gt;&#39; is not declared
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

1 つのステートメントでプログラミング要素を参照していますが、指定された名前に完全に一致する要素をコンパイラが見つけることができません。  
  
 **Error ID:** BC30451  
  
### このエラーを解決するには  
  
1.  参照元のステートメントで名前のスペルを確認します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、大文字と小文字を区別しませんが、その他の違いがあった場合にはまったく異なる名前であると見なします。  アンダースコア \(`_`\) も名前の一部であり、スペルに含まれます。  
  
2.  オブジェクトとメンバーの間にメンバー アクセス演算子 \(`.`\) を指定していることを確認します。  たとえば、<xref:System.Windows.Forms.TextBox> の `TextBox1` という名前のコントロールがある場合、このコントロールの <xref:System.Windows.Forms.TextBoxBase.Text%2A> プロパティにアクセスするには、「`TextBox1.Text`」と入力する必要があります。  代わりに「`TextBox1Text`」と入力した場合、別の名前と見なされます。  
  
3.  スペルが正しく、オブジェクト メンバー アクセスの構文が正しい場合は、その要素が宣言されていることを確認します。  詳細については、「[Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)」を参照してください。  
  
4.  プログラミング要素が宣言されている場合は、その要素がスコープ内にあることを確認します。  プログラミング要素が宣言されている領域の外側にあるステートメントからこの要素を参照している場合は、要素名を修飾しなければならない可能性があります。  詳細については、「[Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
## 参照  
 [Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)