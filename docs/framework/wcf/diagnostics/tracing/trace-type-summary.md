---
title: "トレースの種類の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# トレースの種類の概要
「[SourceLevels](http://go.microsoft.com/fwlink/?LinkID=94943)」には、Critical、Error、Warning、Information、および Verbose の各トレース レベルの定義に加えて、`ActivityTracing` フラグの説明が記載されています。これは、トレースの境界とアクティビティ転送イベントの出力を切り替えるためのフラグです。  
  
 また、「[TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169)」には、<xref:System.Diagnostics> から出力できるトレースの種類が記載されています。  
  
 最も重要な種類を次の表に示します。  
  
|トレースの種類|説明|  
|-------------|--------|  
|Critical|致命的なエラーまたはアプリケーションのクラッシュ。|  
|Error|回復可能なエラー。|  
|警告|情報メッセージ。|  
|情報|重大ではない問題。|  
|詳細|トレースのデバッグ。|  
|\[開始\]|処理の論理単位の開始。|  
|Suspend|処理の論理単位の中断。|  
|Resume|処理の論理単位の再開。|  
|Stop|処理の論理単位の停止。|  
|転送|相関 ID の変更。|  
  
 アクティビティは、上記のトレースの種類の組み合わせとして定義されます。  
  
 ローカル \(トレース ソース\) スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 これは、アクティビティが次の条件を満たす必要があることを意味します。  
  
-   アクティビティは、Start トレースによって開始し、Stop トレースによって停止する必要があります。  
  
-   Suspend トレースまたは Resume トレースの直前に Transfer トレースが必要です。  
  
-   Suspend トレースと Resume トレースが存在する場合、これらのトレースの間にトレースが存在することはできません。  
  
-   上記の条件を満たしている限り、Critical\/Error\/Warning\/Information\/Verbose\/Transfer の各トレースはいくつでも含めることができます。  
  
 グローバル スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。  
  
```  
R+   
```  
  
 R はローカル スコープのアクティビティを表す正規表現です。  これは、次のようになります。  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```