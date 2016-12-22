---
title: "End &lt;keyword&gt; Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.EndDefinition"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "End keyword"
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End &lt;keyword&gt; Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

追加のキーワードを続けて記述すると、そのキーワードが指定されたステートメント ブロックの定義を終了します。  
  
## 構文  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## 指定項目  
 `End`  
 必ず指定します。  プログラミング要素の定義を終了します。  
  
 `AddHandler`  
 カスタムの [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) で、対応する `AddHandler` ステートメントによって開始された `AddHandler` アクセサーを終了する場合に必要です。  
  
 `Class`  
 対応する [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) によって開始されたクラス定義を終了する場合に必要です。  
  
 `Enum`  
 対応する [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) によって開始された列挙値の定義を終了する場合に必要です。  
  
 `Event`  
 対応する [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) によって開始された `Custom` イベントの定義を終了する場合に必要です。  
  
 `Function`  
 対応する [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) によって開始された `Function` プロシージャの定義を終了する場合に必要です。  `End` `Function` ステートメントが実行されると、呼び出しコードに制御が返されます。  
  
 `Get`  
 対応する [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) によって開始された `Property` プロシージャの定義を終了する場合に必要です。  `End` `Get` ステートメントが実行されると、プロパティの値を要求したステートメントに制御が返されます。  
  
 `If`  
 対応する `If` ステートメントによって開始された `If`...`Then`...`Else` ブロックの定義を終了する場合に必要です。  [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md) を参照してください。  
  
 `Interface`  
 対応する [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) によって開始されたインターフェイス定義を終了する場合に必要です。  
  
 `Module`  
 対応する [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md) によって開始されたモジュール定義を終了する場合に必要です。  
  
 `Namespace`  
 対応する [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) によって開始された名前空間定義を終了する場合に必要です。  
  
 `Operator`  
 対応する [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) によって開始された演算子の定義を終了する場合に必要です。  
  
 `Property`  
 対応する [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) によって開始されたプロパティ定義を終了する場合に必要です。  
  
 `RaiseEvent`  
 カスタムの [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) で、対応する `RaiseEvent` ステートメントによって開始された `RaiseEvent` アクセサーを終了する場合に必要です。  
  
 `RemoveHandler`  
 カスタムの [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) で、対応する `RemoveHandler` ステートメントによって開始された `RemoveHandler` アクセサーを終了する場合に必要です。  
  
 `Select`  
 対応する `Select` ステートメントによって開始された `Select`...`Case` ブロックの定義を終了する場合に必要です。  [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) を参照してください。  
  
 `Set`  
 対応する [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) によって開始された `Property` プロシージャの定義を終了する場合に必要です。  `End` `Set` ステートメントが実行されると、プロパティの値を設定するステートメントに制御が返されます。  
  
 `Structure`  
 対応する [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) によって開始された構造体定義を終了する場合に必要です。  
  
 `Sub`  
 対応する [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) によって開始された `Sub` プロシージャの定義を終了する場合に必要です。  `End` `Sub` ステートメントが実行されると、呼び出しコードに制御が返されます。  
  
 `SyncLock`  
 対応する `SyncLock` ステートメントによって開始された `SyncLock` ブロックの定義を終了する場合に必要です。  [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md) を参照してください。  
  
 `Try`  
 対応する `Try` ステートメントによって開始された `Try`...`Catch`...`Finally` ブロックの定義を終了する場合に必要です。  [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) を参照してください。  
  
 `While`  
 対応する `While` ステートメントによって開始された `While` ループの定義を終了する場合に必要です。  [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) を参照してください。  
  
 `With`  
 対応する `With` ステートメントによって開始された `With` ブロックの定義を終了する場合に必要です。  [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) を参照してください。  
  
## 解説  
 追加のキーワードを指定しないで [End Statement](../../../visual-basic/language-reference/statements/end-statement.md) を使うと、コードの実行がすぐに終了します。  
  
 シャープ記号 \(`#`\) を前に付けると、`End` キーワードは対応するディレクティブが指定したプリプロセス ブロックを終了します。  
  
 `#End`  
 必ず指定します。  プリプロセス ブロックの定義を終了します。  
  
 `#ExternalSource`  
 対応する [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) によって開始された外部ソース ブロックを終了する場合に必要です。  
  
 `#If`  
 対応する `#If` ディレクティブによって開始された条件付きコンパイル ブロックを終了する場合に必要です。  [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) を参照してください。  
  
 `#Region`  
 対応する [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) によって開始されたソース領域ブロックを終了する場合に必要です。  
  
## スマート デバイス開発者のためのメモ  
 追加のキーワードを指定しない `End` ステートメントは、サポートされていません。  
  
## 参照  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)