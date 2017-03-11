---
title: "マウスのホイールが存在しません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# マウスのホイールが存在しません
`My.Computer.Mouse.WheelScrollLines` プロパティが呼び出されましたが、マウスにスクロール ホイールがありません。  
  
### このエラーを解決するには  
  
-   `My.Computer.Mouse.WheelScrollLines` プロパティを呼び出す前に `My.Computer.Mouse.WheelExists` プロパティを調べて、マウスにスクロール ホイールがあることを確認します。  
  
     または  
  
-   スクロール ホイールのあるマウスをコンピュータにインストールします。  
  
## 参照  
 [My.Computer.Mouse.WheelScrollLines プロパティ](http://msdn.microsoft.com/ja-jp/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [My.Computer.Mouse.WheelExists プロパティ](http://msdn.microsoft.com/ja-jp/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)