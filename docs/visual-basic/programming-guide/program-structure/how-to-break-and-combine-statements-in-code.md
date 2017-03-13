---
title: "方法: コード内でステートメントを分割および連結する (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb._"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "コロン (:)"
  - "行の連結"
  - "_ 行連結文字"
  - ": 行区切り記号"
  - "Visual Basic コード、コードでの改行"
  - "Visual Basic コード、改行"
  - "Visual Basic コード、行の連結"
  - "長い行のコード"
  - "行終端記号"
  - "行連結シーケンス"
  - "アンダースコア (_)、コードで"
  - "ステートメント [Visual Basic]、コードでの行の連結"
  - "改行、コードで"
  - "行連結文字"
  - "Visual Basic コード、コードでの行の連結"
  - "ステートメント [Visual Basic]、コードでの改行"
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# 方法: コード内でステートメントを分割および連結する (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コード エディターでコードを記述するときに、ステートメントが長くなりすぎて横スクロールが必要になることがあります。  これが方法には影響しないもののコードの実行、ディスプレイに表示されたときに、コードを読み取るために、またはのいずれかとことが困難になります。  このような場合は、単一の長いステートメントを複数行に分割することを検討する必要があります。  
  
### 単一のステートメントを複数行に分割するには  
  
-   行を分割する位置で、行連結文字つまりアンダースコア \(`_`\) を使用します。  アンダースコアは空間に直後され、行終端記号 \(復帰\) に続けて必要があります。  
  
    > [!NOTE]
    >  場合によっては行連結文字を省略した場合、Visual Basic コンパイラは、次のコード行のステートメントが暗黙的に継続されます。  、行連結文字を省略できる構文要素の一覧については [Statements](../../../visual-basic/programming-guide/language-features/statements.md)の "暗黙の行連結" を参照してください。  
  
     次の例では、最終行以外の末尾に行連結文字を指定して、1 つのステートメントを 4 行に分割しています。  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     行連結シーケンスを使用すると、オンラインの場合にも出力した場合にもコードが読みやすくなります。  
  
     行連結文字は行の最後の文字である必要があります。  同じ行のそれ以外でしょうか。また、それに従うことはできません。  
  
     制限事項は、行連結文字を場所に関して使用する方法です。; たとえば、引数名の途中で使用できません。  引数リストを行連結文字で分割することはできますが、個々の引数名は分割せずに残す必要があります。  
  
     行連結文字を使用してコメントを続行できません。  コンパイラは特別な意味のコメント文字をチェックしません。  複数行にコメントを記述する場合は、各行にコメント記号 \(`'`\) を繰り返し記述してください。  
  
 各ステートメントを別個の行に配置する方法をお勧めですが、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、同じ行に複数のステートメントを設定できるようになります。  
  
### 複数のステートメントを同じ行に配置するには  
  
-   次の例に示すように、ステートメントをコロン \(`:`\) で区切ります。  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## 参照  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)