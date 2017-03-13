---
title: "Overload Resolution (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "overload resolution"
  - "procedures, overloading"
  - "procedures, calling"
  - "procedure overloading, overload resolution"
  - "signatures, procedure"
  - "overloads, resolution"
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Overload Resolution (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オーバーロードされたバージョンが複数定義されているプロシージャが呼び出された場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のコンパイラは、どのオーバーロードを呼び出すのかを判断する必要があります。  この判断は、次の手順で行われます。  
  
1.  **アクセシビリティ。**呼び出し元のコードから呼び出すことができないアクセス レベルを持つオーバーロードを除外します。  
  
2.  **パラメーターの数。**呼び出しで指定されている数と異なる数のパラメーターが定義されているオーバーロードを除外します。  
  
3.  **パラメーターのデータ型。**コンパイラは、拡張メソッドよりインスタンス メソッドを優先します。  インスタンス メソッドが、プロシージャの呼び出しに一致するためには拡大変換のみが必要だと判断された場合、すべての拡張メソッドはドロップされ、コンパイラはインスタンス メソッドの候補のみに対して操作を続行します。  このようなインスタンス メソッドが見つからなかった場合には、インスタンス メソッドと拡張メソッドの両方に対して操作が続行されます。  
  
     呼び出し元の引数のデータ型を定義されているパラメーター型に変換できないオーバーロードが、ここで除外されます。  
  
4.  **縮小変換。**呼び出し元の引数の型から定義されているパラメーターの型への縮小変換が必要なオーバーロードを除外します。  これは型チェックのスイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) が `On` でも `Off` でも同じです。  
  
5.  **最小の拡大。**残りのオーバーロードをペアと見なします。  各ペアごとに、定義されているパラメーターのデータ型を比較します。  一方のオーバーロードのすべての型がもう一方のオーバーロードの対応する型に拡大変換される場合は、後者を除外します。  つまり、拡大変換が最も少なくて済むオーバーロードが残されます。  
  
6.  **1 つの候補。**残りのオーバーロードが 1 つだけになるまでこの比較を続け、残った 1 つのオーバーロードへの呼び出しを解決します。  コンパイラがオーバーロードを 1 つに絞りきれない場合は、エラーが発生します。  
  
 次の図は、オーバーロードされたバージョンの、どのセットを呼び出すかを判断するプロセスを示しています。  
  
 ![オーバーロードの解決プロセスのフロー ダイアグラム](../../../../visual-basic/programming-guide/language-features/procedures/media/overloadres.gif "OverloadRes")  
オーバーロードされたバージョンの解決  
  
 次の例は、上で説明したオーバーロード解決のプロセスを示しています。  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 1 回目の呼び出しでは、コンパイラは最初のオーバーロードを除外します。1 つ目の引数の型 \(`Short`\) が、対応するパラメーターの型 \(`Byte`\) よりも大きいからです。  次に、3 番目のオーバーロードを除去します。2 番目のオーバーロードの各引数型 \(`Short` と `Single`\) よりも、3 番目のオーバーロードで対応する引数型 \(`Integer` と `Single`\) の方が大きいからです。  2 番目のオーバーロードの方が拡大変換が少なくて済むため、コンパイラは 2 番目を使用して呼び出します。  
  
 2 回目の呼び出しでは、コンパイラは引数の型が大きすぎるという理由でオーバーロードを除外できません。  3 番目のオーバーロードは、1 回目の呼び出しのときと同じ理由で除外されます。2 番目のオーバーロードを呼び出した方が引数の型の拡大変換が少なくて済むからです。  しかし、コンパイラは 1 番目と 2 番目のオーバーロードのいずれかに解決できません。  どちらにも、対応する型に拡大変換されるパラメーター型が 1 つ定義されています \(`Byte` から `Short`、そして `Single` から `Double`\)。  このため、オーバーロード解決エラーが生成されます。  
  
## オーバーロードされた Optional 引数と ParamArray 引数  
 プロシージャの 2 つのオーバーロードのシグネチャが同じで、唯一の違いが最後のパラメーターの宣言 \(一方が [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) で、他方は [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)\) である場合、コンパイラはそのプロシージャの呼び出しを次の方法で解決します。  
  
|||  
|-|-|  
|呼び出しの最後の引数|コンパイラがオーバーロードの呼び出しを解決するときの最後の引数の宣言|  
|値なし \(引数を省略\)|`Optional`|  
|単一の値|`Optional`|  
|コンマで区切られた複数の値のリスト|`ParamArray`|  
|任意の長さの配列 \(空の配列を含む\)|`ParamArray`|  
  
## 参照  
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)