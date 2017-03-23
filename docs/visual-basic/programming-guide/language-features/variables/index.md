---
title: "Variables in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic]"
  - "values [Visual Basic], storing"
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で計算を実行するときに、しばしば値を格納する必要が生じます。  たとえば、複数の値を計算、比較し、比較の結果に応じて異なる処理を実行する場合があります。  値を比較するためは、値を保持する必要があります。  
  
## 使用方法  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、ほとんどのプログラミング言語と同様に、変数を使って値を格納します。  *変数*には、変数に格納されている値を参照するときに使用する「名前」があります。  変数はデータ型も持っています。これにより、変数に格納できるデータの種類が決まります。  密接な関係を持つ一連のデータ項目にインデックスを付けて格納する必要がある場合は、変数を配列として使用することもできます。  
  
 ローカル型の推定により、データ型を明示的に指定せずに変数を宣言できます。  その代わりに、コンパイラは変数の型を初期化式の型から推測します。  詳細については、「[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」および「[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。  
  
## 値の代入  
 計算を実行して結果を変数に代入するには、次の例のように、代入ステートメントを使用します。  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  この例で使用されている等号 \(`=`\) は、等値演算子ではなく代入演算子です。  値は変数 `applesSold` に代入されます。  
  
 詳細については、「[How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)」を参照してください。  
  
## 変数とプロパティ  
 項目がこのコレクション ビューに含まれている場合は 。それ以外の場合は 。  ただし、プロパティは変数よりも複雑です。  プロパティはコード ブロックを使用して、プロパティの値を設定および取得する方法を制御します。  詳細については、「[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)」を参照してください。  
  
## 参照  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [変数のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)