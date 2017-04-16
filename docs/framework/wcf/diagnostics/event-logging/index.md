---
title: "WCF のイベント ログ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント ログ [WCF]"
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# WCF のイベント ログ
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、Windows イベント ログで内部イベントをトレースします。  
  
## イベント ログの表示  
 イベント ログは、既定で自動的に有効になります。無効にする方法はありません。[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってログに記録されるイベントは、イベント ビューアーを使用して表示できます。このツールを起動するには、**\[スタート\]** ボタンをクリックし、**\[コントロール パネル\]** をクリックします。次に、**\[管理ツール\]** をダブルクリックし、**\[イベント ビューアー\]** をダブルクリックします。  
  
### アプリケーション イベント ログ  
 **アプリケーション イベント ログ**には、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によって生成されるイベントの大半が含まれています。このエントリの多くは、アプリケーションに関して特定の機能を起動できなかったことを示しています。ログの内容には次のような種類があります。  
  
-   メッセージのログ記録とトレース : [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では、トレースとメッセージのログ記録に失敗すると、イベント ログにイベントが記録されます。ただし、トレース エラーが発生するたびにイベントがトリガーされるわけではありません。イベント ログがトレース エラーでいっぱいになってしまう状況を回避するために、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では、このようなイベントに 10 分のブラックアウト期間を設けています。つまり、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] がトレース エラーをイベント ログに書き込んだ後、少なくとも 10 分間はトレース エラーのログ記録が行われません。  
  
-   共有リスナー : WCF TCP ポート共有サービスが開始に失敗すると、イベントがログに記録されます。  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: サービスが開始に失敗すると、イベントがログに記録されます。  
  
-   起動エラーやクラッシュなど、重大なエラー イベント。  
  
-   メッセージ ログの有効化 : メッセージ ログが有効化された場合に、イベントがログに記録されます。これには機密情報やアプリケーション固有の情報がメッセージのヘッダーや本文に記録されている可能性があることを管理者に知らせる目的があります。  
  
-   `machine.config` ファイルの `machineSettings` 要素で、`enableLoggingKnownPII` 属性が設定されている場合、イベントはログに記録されます。この属性は、コンピューター上で実行しているアプリケーションが、既知の個人を特定できる情報 \(PII\) をログに記録できるかどうかを指定します。  
  
-   特定のアプリケーションで PII ログを有効にするために、`app.config` ファイルまたは `web.config` ファイルの `logKnownPii` 属性が `true` に設定され、`machine.config` ファイルの `machineSettings` 要素で、`enableLoggingKnownPII` 属性が `false` に設定されている場合、イベントはログに記録されます。また、`logKnownPii` と `enableLoggingKnownPII` の両方が `true` に設定されている場合、イベントはログに記録されます。このような構成設定の詳細については、「[メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)」のセキュリティに関するセクションを参照してください。  
  
### セキュリティ イベント ログ  
 **セキュリティ イベント ログ**には、WCF によってログ記録されたセキュリティ監査イベントが書き込まれます。  
  
### システム イベント ログ  
 WCF では、**システム イベント ログ**に対する記録は行われません。  
  
### イベント ログ エントリ  
 イベントの**ソース**は、ログ エントリを生成するアセンブリの名前です。  
  
 イベント ログ エントリの型によって、イベントの重大度がわかります。各イベントは単一の型でなければなりません。アプリケーションがイベントをレポートする際には、そのイベントの型が示されます。イベント ビューアーは、この型を使用して、ログのリスト ビューに表示するアイコンを決定します。イベント ログ エントリで使用されるイベントの型については、「<xref:System.Diagnostics.EventLogEntryType>」を参照してください。  
  
 イベント ビューアーでイベントを表示しているときに "詳細な情報" をクリックすると、インターネット上に情報が送信される場合があります。詳細については、イベント ビューアーのヘルプを参照してください。  
  
## 参照  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [イベント一覧](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)