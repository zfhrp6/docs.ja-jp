---
title: "WCF のイベント ログ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ccdecb1aae193ffecdd6ec1d4eae4289f6ac7eb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="event-logging-in-wcf"></a>WCF のイベント ログ
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、Windows イベント ログで内部イベントをトレースします。  
  
## <a name="viewing-event-logs"></a>イベント ログの表示  
 イベント ログは、既定で自動的に有効になります。無効にする方法はありません。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってログに記録されるイベントは、イベント ビューアーを使用して表示できます。 このツールを起動する をクリックして**開始**、 をクリックして**コントロール パネルの **をダブルクリックして**管理ツール**、順にダブルクリック**イベント ビューアー**.  
  
### <a name="application-event-log"></a>アプリケーション イベント ログ  
 **アプリケーション イベント ログ**によって生成されたイベントの大半が含ま[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]です。 このエントリの多くは、アプリケーションに関して特定の機能を起動できなかったことを示しています。 次に例を示します。  
  
-   メッセージのログ記録とトレース : [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では、トレースとメッセージのログ記録に失敗すると、イベント ログにイベントが記録されます。 ただし、トレース エラーが発生するたびにイベントがトリガーされるわけではありません。 イベント ログがトレース エラーでいっぱいになってしまう状況を回避するために、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では、このようなイベントに 10 分のブラックアウト期間を設けています。 つまり、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] がトレース エラーをイベント ログに書き込んだ後、少なくとも 10 分間はトレース エラーのログ記録が行われません。  
  
-   共有リスナー : WCF TCP ポート共有サービスが開始に失敗すると、イベントがログに記録されます。  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: サービスが開始に失敗すると、イベントがログに記録されます。  
  
-   起動エラーやクラッシュなど、重大なエラー イベント。  
  
-   メッセージ ログの有効化 : メッセージ ログが有効化された場合に、イベントがログに記録されます。 これには機密情報やアプリケーション固有の情報がメッセージのヘッダーや本文に記録されている可能性があることを管理者に知らせる目的があります。  
  
-   `enableLoggingKnownPII` ファイルの `machineSettings` 要素で、`machine.config` 属性が設定されている場合、イベントはログに記録されます。 この属性は、コンピューター上で実行しているアプリケーションが、既知の個人を特定できる情報 (PII) をログに記録できるかどうかを指定します。  
  
-   特定のアプリケーションで PII ログを有効にするために、`logKnownPii` ファイルまたは `app.config` ファイルの `web.config` 属性が `true` に設定され、`enableLoggingKnownPII` ファイルの `machineSettings` 要素で、`machine.config` 属性が `false` に設定されている場合、イベントはログに記録されます。 また、`logKnownPii` と `enableLoggingKnownPII` の両方が `true` に設定されている場合、イベントはログに記録されます。 これらの構成設定の詳細については、の [セキュリティ] セクションを参照してください、[メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)トピックです。  
  
### <a name="security-event-log"></a>セキュリティ イベント ログ  
 **セキュリティ イベント ログ**WCF によってログに記録されるセキュリティ監査イベントが含まれています。  
  
### <a name="system-event-log"></a>システム イベント ログ  
 WCF ログに記録しないもの、**システム イベント ログ**です。  
  
### <a name="event-log-entries"></a>イベント ログ エントリ  
 **ソース**イベントのログ エントリを生成するアセンブリの名前です。  
  
 イベント ログ エントリの型によって、イベントの重大度がわかります。 各イベントは単一の型でなければなりません。アプリケーションがイベントをレポートする際には、そのイベントの型が示されます。 イベント ビューアーは、この型を使用して、ログのリスト ビューに表示するアイコンを決定します。 イベント ログ エントリで使用されるイベントの型については、「<xref:System.Diagnostics.EventLogEntryType>」を参照してください。  
  
 「詳細」をクリックすると、イベント ビューアーがインターネット経由で情報を送信可能性があります、イベント ビューアでイベントを表示するときにします。 詳細については、イベント ビューアーのヘルプを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [イベントの一般的なリファレンス](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
