---
title: リソース消費の制御とパフォーマンスの向上
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: ee94ae7c570156d870b93311365ad52b815f12d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805526"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>リソース消費の制御とパフォーマンスの向上
このトピックでは、リソースの消費量をコントロールに正常に機能し、パフォーマンス メトリックに影響する Windows Communication Foundation (WCF) アーキテクチャのさまざまな領域にさまざまなプロパティについて説明します。  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF でのリソース消費を制約するプロパティ  
 Windows Communication Foundation (WCF) では、セキュリティまたはパフォーマンスのためのプロセスの特定の種類の制約が適用されます。 これらの制約には、クォータとスロットルという 2 つの主要な形式があります。 *クォータ*数に達しましたまたは超えた場合に、システムのある時点で即時例外をトリガーする制限します。 *調整*をスローする例外が直ちに発生しない制限します。 スロットル制限に達すると、例外がスローされる代わりに、そのスロットル値によって設定された制限の範囲内で処理が続行されます。 この制限された処理によって他の場所で例外が発生する可能性がありますが、これはアプリケーションに依存します。  
  
 クォータとスロットルの違いに加え、シリアル化レベル、トランスポート レベル、およびアプリケーション レベルにも制約を加えるプロパティがあります。 たとえば、システム提供のすべてのトランスポート バインディング要素によって実装されるクォータである <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> は、既定で 65,536 バイトに設定されます。これは、悪意のあるクライアントがサービスに対して、大量のメモリを消費させるサービス拒否攻撃を実行することを防ぐための措置です  (通常は、この値を下げることによってパフォーマンスを向上できます)。  
  
 シリアル化のクォータの例としては、<xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> プロパティがあります。このプロパティは、シリアライザーが <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> メソッドの 1 回の呼び出しでシリアル化または逆シリアル化するオブジェクトの最大数を指定します。 アプリケーション レベルのスロットルの例としては、<xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> プロパティがあります。このプロパティは、既定で、セッションフル チャネルの同時接続の最大数を 10 に制限します  (クォータとは異なり、このスロットル値に達しても、アプリケーションは処理を続行しますが、新しいセッションフル チャネルは受け入れません。つまり、他のセッションフル チャネルのいずれかが終了するまで、新しいクライアントは接続できません)。  
  
 これらの制御は、特定の種類の攻撃に対してすぐに使用できる軽減策を提供し、メモリの占有領域や起動時間などのパフォーマンス メトリックを向上するように設計されています。 ただし、アプリケーションによっては、これらの制御によってサービス アプリケーションのパフォーマンスが低下したり、アプリケーションがまったく動作しなくなったりする可能性があります。 たとえば、ビデオ ストリーミング用に設計されたアプリケーションは、既定の <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> プロパティをすぐに超える可能性があります。 このトピックでは、さまざまなコントロールの概要については、WCF のすべてのレベルでのアプリケーションに適用、設定が、アプリケーションを低下させているかどうかについて情報を取得するさまざまな方法について説明し、さまざまな問題を解決する方法について説明を提供します。 ほとんどのスロットルおよび一部のクォータは、基本プロパティがシリアル化またはトランスポートの制約である場合でも、アプリケーション レベルで利用できます。 たとえば、サービス クラスの <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> を使用して、<xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> プロパティを設定できます。  
  
> [!NOTE]
>  かどうかは、特定の問題がある、最初にお読みください、 [WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)を一覧表示されているかどうかの問題 (とソリューション) があります。  
  
 シリアル化プロセスが制限されているプロパティの一覧は[データのセキュリティに関する考慮事項](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)です。 トランスポートに関連するリソースの消費を制限するプロパティの一覧は[トランスポート クォータ](../../../docs/framework/wcf/feature-details/transport-quotas.md)です。 アプリケーション層でリソースの消費を制限するプロパティは、<xref:System.ServiceModel.Dispatcher.ServiceThrottle> クラスのメンバーです。  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>クォータ設定に関連するアプリケーションとパフォーマンスの問題の検出  
 上記の値の既定値は、一般的なセキュリティの問題に対する基本的な保護を提供しながら、さまざまなアプリケーションで基本的なアプリケーション機能を使用できるように選択されたものです。 ただし、アプリケーション デザインによっては、1 つ以上のスロットル設定を超えてしまったためにアプリケーションがセキュリティで保護されなかったり、設計どおりに動作しなかったりする場合があります。 その場合は、超過したスロットル値とそのレベルを特定し、アプリケーションのスループットを向上するための適切な手順を決定する必要があります。  
  
 通常、アプリケーションを作成してデバッグする際には、構成ファイルまたはプログラムで <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティを `true` に設定します。 これは、WCF サービス例外のスタック トレースを表示するためにクライアント アプリケーションに返されるを指示します。 この機能により、ほとんどのアプリケーション レベルの例外が報告され、問題が発生している場合に、どのクォータ設定が関係しているかを表示できます。  
  
 実行時に発生する一部の例外はアプリケーション層から見えないため、このメカニズムでは返されません。このため、カスタムの <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> 実装で処理できないことがあります。 Microsoft Visual Studio などの開発環境で作業している場合は、これらの例外のほとんどは自動的に表示されます。 開発環境の設定など、いくつかの例外をマスクするただし、[マイ コードのみ](http://go.microsoft.com/fwlink/?LinkId=82174)Visual Studio 2005 で設定します。  
  
 開発環境の機能に関係なくには、すべての例外をデバッグし、アプリケーションのパフォーマンスをチューニングする WCF トレースとメッセージ ログ記録の機能を使用できます。 詳細については、次を参照してください。[トレースを使用して、アプリケーションのトラブルシューティングを](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)です。  
  
## <a name="performance-issues-and-xmlserializer"></a>パフォーマンスの問題と XmlSerializer  
 <xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するサービスおよびクライアント アプリケーションは、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルします。このため、起動時のパフォーマンスが低下することがあります。  
  
> [!NOTE]
>  生成済みシリアル化コードはクライアント アプリケーションでのみ使用できます。サービスでは使用できません。  
  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)アプリケーションのコンパイル済みアセンブリから、必要なシリアル化コードを生成することによってこれらのアプリケーションの起動時のパフォーマンスを向上させることができます。 詳細については、次を参照してください。[する方法: スタートアップ時間の WCF クライアント アプリケーション、XmlSerializer を使用してを向上させる](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)です。  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>ASP.NET で WCF サービスをホストする場合のパフォーマンスの問題  
 WCF サービスを IIS および ASP.NET でホストする場合、IIS と ASP.NET の構成設定が WCF サービスのスループットやメモリの占有領域に影響する場合があります。  ASP.NET のパフォーマンスに関する詳細については、次を参照してください。 [ASP.NET のパフォーマンスを向上させる](http://go.microsoft.com/fwlink/?LinkId=186462)です。  予想外の結果を引き起こす可能性のある設定の 1 つに、<xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> があります。これは、<xref:System.Web.Configuration.ProcessModelSection> のプロパティです。 アプリケーションのクライアントが固定数または少数である場合、<xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> を 2 に設定すると、CPU の使用率が 100% に近いマルチプロセッサ コンピューターのスループットが向上する場合があります。 このパフォーマンスの向上にはコストが伴います。つまり、メモリの使用率も増加するため、スケーラビリティが低下する場合があります。  
  
## <a name="see-also"></a>関連項目  
 [管理と診断](../../../docs/framework/wcf/diagnostics/index.md)  
 [大規模データとストリーミング](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
