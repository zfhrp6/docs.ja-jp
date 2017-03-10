---
title: "Differences Between Properties and Variables in Visual Basic | Microsoft Docs"
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
  - "property values"
  - "variables [Visual Basic]"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "variables [Visual Basic], definition"
  - "Visual Basic code, variables"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
  - "properties [Visual Basic], defined"
  - "variables [Visual Basic], and properties"
  - "properties [Visual Basic], and variables"
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Differences Between Properties and Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数とプロパティは、いずれもアクセス可能な値を表します。  しかし、格納と実装が異なります。  
  
## 変数  
 *変数*は、メモリ内の場所に直接対応します。  変数は、1 つの宣言ステートメントで定義します。  変数は、プロシージャ内で定義され、そのプロシージャ内でのみ使用できる*ローカル変数*と、モジュール、クラス、または構造体の中で定義され、プロシージャ内では定義されない*メンバー変数*のいずれかです。  メンバー変数は*フィールド*とも呼ばれます。  
  
## プロパティ  
 *プロパティ*は、モジュール、クラス、構造体で定義されるデータ要素です。  プロパティは、`Property` と `End Property` ステートメントの間のコード ブロックで定義します。  `Get` プロシージャか `Set` プロシージャ、またはこの両方を含むコード ブロックです。  これらのプロシージャは、*プロパティ プロシージャ*または *プロパティ アクセサー*と呼ばれます。  プロパティの値を取得および格納するだけでなく、アクセス カウンターの更新などのカスタム動作を実行することもできます。  
  
## 異なる点  
 次の表に、変数とプロパティの主な違いをまとめます。  
  
|異なる点|変数|プロパティ|  
|----------|--------|-----------|  
|宣言|1 つの宣言ステートメント|コード ブロック内の一連のステートメント|  
|実装|1 つの格納場所|実行可能コード \(プロパティ プロシージャ\)|  
|Storage|変数の値に直接関連付けられる|一般的に、プロパティに含まれるクラスまたはモジュールの外部からはアクセスできない内部ストレージを持つ<br /><br /> プロパティの値は 1 つの格納された要素として存在する場合もそうでない場合もある <sup>1</sup>|  
|実行可能コード|なし|最低でも 1 つのプロシージャを持つ必要がある|  
|読み取り\/書き込みアクセス|読み取り\/書き込みまたは読み取り専用|読み取り\/書き込み、読み取り専用、書き込み専用|  
|カスタム動作 \(値を受け取ったり返したりする操作以外\)|不可能|プロパティの値の設定または取得操作の一部として実行可能|  
  
 <sup>1</sup> 変数とは異なり、プロパティの値はストレージの単独のアイテムに直接対応しないこともあります。  ストレージが利便性やセキュリティのために分割されたり、値が暗号化されたフォームに格納されたりすることがあります。  このような場合、`Get` プロシージャが分割された部分をアセンブルしたり、格納された値を復号化したりし、`Set` プロシージャが新しい値を暗号化したり、値をストレージに分割したりします。  プロパティの値は、時刻のようにすぐ変わるものである場合もあります。このような場合、プロパティにアクセスすると、`Get` プロシージャが実行時に値を計算します。  
  
## 参照  
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)