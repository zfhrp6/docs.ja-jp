---
title: "Object or class does not support the set of events | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID459"
dev_langs: 
  - "VB"
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Object or class does not support the set of events
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンポーネントで `WithEvents` 変数を使おうとしましたが、そのコンポーネントは指定されたイベント セットのイベント ソースとして使用できません。  たとえば、オブジェクトのイベントをシンクしてから、最初のオブジェクトを `Implements` で実装する別のオブジェクトを作成する場合があります。  実装したオブジェクトからこのイベントをシンクできると考えることもできますが、常にシンクできるとは限りません。  `Implements` では、メソッドおよびプロパティ用のインターフェイスのみが実装されます。  `WithEvents` は、プライベートな `UserControls` をサポートしていません。`ObjectEvent` を発生させるために必要な型情報がランタイム時には利用できないためです。  
  
### このエラーを解決するには  
  
1.  イベントの発生元ではないコンポーネントのイベントはシンクできません。  
  
## 参照  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)