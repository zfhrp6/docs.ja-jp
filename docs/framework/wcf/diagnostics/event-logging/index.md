---
title: WCF のイベント ログ
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: ea0e6f3dc66bf40d631077c0dce20ea46f3a6688
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804944"
---
# <a name="event-logging-in-wcf"></a>WCF のイベント ログ
Windows Communication Foundation (WCF) では、Windows イベント ログで内部イベントをトレースします。  
  
## <a name="viewing-event-logs"></a>イベント ログの表示  
 イベント ログは、既定で自動的に有効になります。無効にする方法はありません。 イベント ビューアーを使用して、WCF によって記録されたイベントを表示できます。 このツールを起動する をクリックして**開始**、 をクリックして**コントロール パネルの **をダブルクリックして**管理ツール**、順にダブルクリック**イベント ビューアー**.  
  
### <a name="application-event-log"></a>アプリケーション イベント ログ  
 **アプリケーション イベント ログ**WCF によって生成されたイベントのほとんどが含まれています。 このエントリの多くは、アプリケーションに関して特定の機能を起動できなかったことを示しています。 その例は次のとおりです。  
  
-   メッセージ ログ記録とトレース: WCF するトレースとメッセージ ログが失敗したときにイベントがイベント ログに書き込みます。 ただし、トレース エラーが発生するたびにイベントがトリガーされるわけではありません。 イベント ログがトレース エラーでいっぱいになってしまうことを防ぐためには、WCF は、このようなイベントの 10 分のブラック アウト期間を実装します。 これは、する場合は、イベント ログに書き込むトレース エラーは WCF、しません。 ここでも少なくとも 10 分間のことを意味します。  
  
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
 [イベント一覧](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
