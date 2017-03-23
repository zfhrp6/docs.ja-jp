---
title: "Default (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Default"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "defaults, properties"
  - "properties [Visual Basic], default"
  - "default properties, in Visual Basic"
  - "Default keyword [Visual Basic]"
  - "default properties"
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Default (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティがクラス、構造体、またはインターフェイスの既定のプロパティであることを示すキーワードです。  
  
## 解説  
 クラス、構造体、インターフェイスでは、最大で 1 つのプロパティを*既定のプロパティ*として定義できます。ただし、そのプロパティは 1 つ以上のパラメーターを受け取るものであることが必要です。  Visual Basic で、メンバーを指定せずにクラスや構造体を参照するコードを作成すると、既定のプロパティを参照していると判断されます。  
  
 既定のプロパティを使用すると、ソース コードに記述する文字の量が少し減りますが、コードの読みやすさが低下します。  呼び出しコードからクラスや構造体が明確に区別できない場合にクラス名または構造体名を使って参照すると、その参照がクラスと構造体のどちらに対するものなのか、また既定のプロパティを参照しているかどうかもはっきりしません。  このような場合、コンパイル エラーまたはランタイムの論理エラーが発生する可能性があります。  
  
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)を使ってコンパイラの型チェックを常に `On` に設定しておくことで、既定のプロパティのエラーが発生する可能性をいくらか低下できます。  
  
 定義済みのクラスまたは構造体を使ってコードを作成する場合には、既定のプロパティが設定されているかどうかを調べ、設定されていればその名前を確認しておくことが必要です。  
  
 以上のような難点があるため、既定のプロパティは定義しないことをお勧めします。  コードの読みやすさの点からも、すべてのプロパティを、既定のプロパティであっても明示的に参照することを心がけてください。  
  
 `Default` 修飾子は次の構文で使用します。  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 参照  
 [How to: Declare and Call a Default Property in Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)