---
title: 管理と診断
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa5256f543a99618e00dc88e085dfee4ac76ebab
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="administration-and-diagnostics"></a>管理と診断
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、アプリケーションのライフサイクルのさまざまな段階を監視できるようにする豊富な機能が用意されています。 たとえば、展開時に構成を使用してサービスとクライアントを設定できます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、アプリケーションのパフォーマンス測定に役立つ多数のパフォーマンス カウンターが備わっています。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WMI (Windows Management Instrumentation) プロバイダーを介して実行時のサービスの検査データを公開します。 アプリケーションにエラーが発生したり、適切に動作しなくなったりした場合は、イベント ログを使用して、何か重大なことが発生していないかを確認できます。 メッセージ ログとトレースを使用して、アプリケーションでどのようなイベントが発生しているのかをエンドツーエンドで確認することもできます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションが正常に動作しなくなった場合、開発者や IT 専門家は、これらの機能を使用してトラブルシューティングを行うことができます。  
  
> [!NOTE]
>  有効にする必要があります明確な詳細情報なしでエラーを受信している場合、`includeExceptionDetailInFaults`の属性、 [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)構成要素。 これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は例外に関する詳細をクライアントに送信するようになり、より詳しい診断を行わなくても多くの一般的な問題を検出できるようになります。 詳細については、次を参照してください。[送信と受信エラー](../../../../docs/framework/wcf/sending-and-receiving-faults.md)です。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF に用意された診断機能  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、次の診断機能が用意されています。  
  
-   エンド ツー エンドのトレースは、デバッガーを使用せずにアプリケーションのトラブルシューティングを行うためのインストルメンテーション データを提供します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、処理マイルストーンのトレースとエラー メッセージを出力します。 これには、チャネル ファクトリのオープンやサービス ホストによるメッセージの送受信が含まれます。 実行中のアプリケーションに対してトレースを有効にすると、その進行状況を監視できます。 詳細については、次を参照してください。、[トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)トピックです。 どのようにできるトレースを使用するアプリケーションをデバッグする詳細については、次を参照してください。、 [、アプリケーションのトラブルシューティングを使用してトレース](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)トピックです。  
  
-   メッセージ ログを使用すると、送信前と送信後の両方のメッセージを確認できます。 詳細については、次を参照してください。、[メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)トピックです。  
  
-   イベント トレースは、すべての重大な問題に関連するイベントをイベント ログに書き込みます。 後でイベント ビューアーを使用して異常を調査できます。 詳細については、次を参照してください。、[イベント ログ](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)トピックです。  
  
-   パフォーマンス モニターを介して公開されるパフォーマンス カウンターを使用すると、アプリケーションとシステムの状態を監視できます。 詳細については、次を参照してください。、[パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)トピックです。  
  
-   <xref:System.ServiceModel.Configuration> 名前空間を使用すると、構成ファイルを読み込んでサービスまたはクライアント エンドポイントを設定できます。 多数のコンピューターに更新を展開する必要がある場合は、オブジェクト モデルを使用して、さまざまなアプリケーションに対する変更をスクリプトで処理できます。 また、使用することができます、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) GUI ウィザードを使用して、構成設定を編集します。 詳細については、次を参照してください。、 [、アプリケーションを構成する](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)トピックです。  
  
-   WMI を使用すると、コンピューター上でリッスン中のサービスと使用しているバインディングを確認できます。 詳細については、次を参照してください。、[診断の Windows Management Instrumentation を使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)トピックです。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの作成、展開、および管理を容易にする GUI ツールとコマンド ライン ツールも用意されています。 詳細については、次を参照してください。 [Windows Communication Foundation ツール](../../../../docs/framework/wcf/tools.md)です。 たとえば、使用することができます、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)を作成および編集[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]構成設定の XML を直接編集ではなく、ウィザードを使用します。 使用することも、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)を表示、グループ、およびトレース メッセージをフィルター処理を診断することができるため、修復、および問題を確認してください[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]services です。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションの構成](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [サービスの配置](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [例外リファレンス](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [イベント ログ](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [ServiceModel 登録ツール](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [診断用の WMI (Windows Management Instrumentation) の使用](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Windows Communication Foundation ツール](../../../../docs/framework/wcf/tools.md)
