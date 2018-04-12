---
title: 終了&lt;キーワード&gt;ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>終了&lt;キーワード&gt;ステートメント (Visual Basic)
その他のキーワードの後に、そのキーワードによって導入されるステートメント ブロックの定義を終了します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="parts"></a>指定項目  
 `End`  
 必須です。 プログラミング要素の定義を終了します。  
  
 `AddHandler`  
 終了するために必要な`AddHandler`、対応する開始アクセサー`AddHandler`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
 `Class`  
 クラスの定義を対応する終了を終了するために必要な[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)です。  
  
 `Enum`  
 対応する開始列挙の定義を終了するために必要な[Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。  
  
 `Event`  
 終了するために必要な`Custom`イベントの定義を対応する終了[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
 `Function`  
 終了するために必要な`Function`プロシージャの定義が、対応する開始[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。 実行されると、`End``Function`ステートメントでは、呼び出し元のコードに制御が戻ります。  
  
 `Get`  
 終了するために必要な`Property`プロシージャの定義が、対応する開始[Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)です。 実行されると、`End``Get`ステートメントでは、プロパティの値を要求したステートメントに制御が戻ります。  
  
 `If`  
 終了するために必要な`If`しています.`Then`...`Else`ブロック定義が、対応する開始`If`ステートメントです。 参照してください[場合.そうしたら。。。Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)です。  
  
 `Interface`  
 開始されて、対応するインターフェイス定義を終了するために必要な[インターフェイス ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)です。  
  
 `Module`  
 開始されて、対応するモジュールの定義を終了するために必要な[モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)です。  
  
 `Namespace`  
 開始されて、対応する名前空間の定義を終了するために必要な[Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)です。  
  
 `Operator`  
 開始されて、対応する演算子の定義を終了するために必要な[Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)です。  
  
 `Property`  
 開始されて、対応するプロパティの定義を終了するために必要な[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)です。  
  
 `RaiseEvent`  
 終了するために必要な`RaiseEvent`、対応する開始アクセサー`RaiseEvent`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
 `RemoveHandler`  
 終了するために必要な`RemoveHandler`、対応する開始アクセサー`RemoveHandler`カスタム ステートメント[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
 `Select`  
 終了するために必要な`Select`しています.`Case`ブロック定義が、対応する開始`Select`ステートメントです。 参照してください[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)です。  
  
 `Set`  
 終了するために必要な`Property`プロシージャの定義が、対応する開始[Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)です。 実行されると、`End``Set`ステートメントでは、プロパティの値を設定するステートメントに制御が戻ります。  
  
 `Structure`  
 開始されて、対応する構造体の定義を終了するために必要な[Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)です。  
  
 `Sub`  
 終了するために必要な`Sub`プロシージャの定義が、対応する開始[Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)です。 実行されると、`End``Sub`ステートメントでは、呼び出し元のコードに制御が戻ります。  
  
 `SyncLock`  
 終了するために必要な`SyncLock`ブロック定義が、対応する開始`SyncLock`ステートメントです。 参照してください[SyncLock ステートメント](../../../visual-basic/language-reference/statements/synclock-statement.md)です。  
  
 `Try`  
 終了するために必要な`Try`しています.`Catch`...`Finally`ブロック定義が、対応する開始`Try`ステートメントです。 参照してください[を再試行してください.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。  
  
 `While`  
 終了するために必要な`While`ループの定義を対応する終了`While`ステートメントです。 参照してください[中.While ステートメント終了](../../../visual-basic/language-reference/statements/while-end-while-statement.md)です。  
  
 `With`  
 終了するために必要な`With`ブロック定義が、対応する開始`With`ステートメントです。 参照してください[としています.ステートメントで終了して](../../../visual-basic/language-reference/statements/with-end-with-statement.md)です。  
  
## <a name="remarks"></a>コメント  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)、追加のキーワードをせずにすぐに実行を終了します。  
  
 番号記号に続く場合 (`#`) では、`End`キーワードが、対応するディレクティブによって導入されるプリプロセッサのブロックを終了します。  
  
 `#End`  
 必須です。 処理前のブロックの定義を終了します。  
  
 `#ExternalSource`  
 開始されて、対応する外部のソース ブロックを終了するために必要な[#ExternalSource ディレクティブ](../../../visual-basic/language-reference/directives/externalsource-directive.md)です。  
  
 `#If`  
 対応する開始条件付きコンパイル ブロックを終了するために必要な`#If`ディレクティブです。 参照してください[#If しています.Then... #Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)です。  
  
 `#Region`  
 開始されて、対応するソース領域ブロックを終了するために必要な[#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)です。  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 `End`その他のキーワードを使用せず、ステートメントはサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
