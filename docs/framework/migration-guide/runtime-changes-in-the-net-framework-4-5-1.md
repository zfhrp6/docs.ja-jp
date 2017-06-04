---
title: ".NET Framework 4.5.1 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーションの互換性"
  - "ランタイムの変更点"
  - ".NET Framework 4.5.1"
ms.assetid: da880ad7-ba0a-4368-b340-705e3533c351
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework 4.5.1 におけるランタイムの変更点
まれに、実行時の変更は [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] または 4.5 を対象とする既存のアプリに影響を与える可能性がありますが、4.51 ランタイムで実行されます。 次の領域の変更が含まれています。  
  
-   [コア](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
 次の表の [スコープ] 列には、各変更の重要度を指定します。  
  
-   メジャー。 多数のアプリに影響するか、またはコードに大幅な変更が必要な、重大な変更。 ランタイムの変更はこのカテゴリに分類されないことに注意してください。  
  
-   マイナー。 少数のアプリに影響するか、またはコードにわずかな変更が必要な、変更。  
  
-   エッジ。 一般的ではない特定のシナリオでアプリに影響を与える変更。  
  
-   透過。 アプリの開発者やユーザーには大きな影響を及ぼさない変更。 アプリはこの変更のために変更を加える必要はありません。  
  
<a name="Core"></a>   
## <a name="core-runtime-changes"></a>コアでのランタイム変更  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>シリアル化</TKey, TValue>|A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>と .NET Framework 4.5 でシリアル化されたオブジェクト、 <xref:System.Runtime.Serialization.NetDataContractSerializer>型の内部の変更のためにのみ、.NET Framework 4.5.1 と 4.5.2 で逆シリアル化できません\</TKey, TValue>。<br /><br /> この変更は*いない*次のシナリオに適用します。<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>オブジェクトは、.NET Framework 4.5 でシリアル化されで逆シリアル化、 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]</TKey, TValue> 。 <xref:System.Runtime.Serialization.NetDataContractSerializer>で、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]オブジェクトを逆シリアル化することができます。<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>オブジェクトは、.NET Framework の以降のバージョンでシリアル化され、.NET Framework 4.5 で逆シリアル化します\</TKey, TValue>。 <xref:System.Runtime.Serialization.NetDataContractSerializer> .NET Framework 4.5 では、オブジェクトを逆シリアル化できません。<br /><br /> バージョン間のシリアル化および逆シリアル化、 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> .NET Framework 4.5 の後に .NET Framework のバージョン間でのオブジェクト</TKey, TValue>。 この変更は、.NET Framework 4.5 でシリアル化オブジェクトに適用されます*のみ*します。|2 つの解決策が利用できるは、シリアル化する必要がある場合、 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>オブジェクト、.NET Framework 4.5 および .NET Framework の以降のバージョンに逆シリアル化:\</TKey, TValue><br /><br /> 代替のシリアライザーを使用して、 <xref:System.Runtime.Serialization.DataContractSerializer>または<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>します。<br /><br /> アップグレード、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]の逆シリアル化をサポートする<xref:System.Collections.Concurrent.ConcurrentDictionary%602> .NET Framework 4.5 にシリアル化されたオブジェクト\</TKey, TValue>。|マイナー|  
|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>クラス|<xref:System.Diagnostics.Tracing.EventListener>埋め込み null ある文字列を切り捨てます。 は、null 文字はサポートされていない、 <xref:System.Diagnostics.Tracing.EventSource>クラスです。|使用するアプリケーションにのみ影響する変更<xref:System.Diagnostics.Tracing.EventListener>を読み取る<xref:System.Diagnostics.Tracing.EventSource>プロセス内のデータとは、区切り記号として null 文字を使用します。|エッジ|  
|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>クラス|ランタイムは、次を指定するコントラクトを強制するようになりました: から派生したクラス<xref:System.Diagnostics.Tracing.EventSource> ETW を定義するイベント メソッドは、基本クラスを呼び出す必要があります<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=fullName> ETW イベント メソッドに渡された同じ引数でイベント ID を持つメソッドの後にします。|<xref:System.IndexOutOfRangeException>例外がスローされます、 <xref:System.Diagnostics.Tracing.EventListener>読み取り<xref:System.Diagnostics.Tracing.EventSource>このコントラクトに違反するイベント ソースのプロセス内のデータです。<br /><br /> 参照してください[対応策: EventSource.WriteEvent メソッドの呼び出し](../../../docs/framework/migration-guide/mitigation-eventsource-writeevent-method-calls.md)|マイナー|  
|アプリケーション ドメイン間でのオブジェクトの逆シリアル化|場合によっては、アプリが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用すると、アプリ ドメイン間で論理呼び出しコンテキストのオブジェクトを逆シリアル化しようとして、例外がスローされます。|この問題は、固有のシナリオで発生します。 詳細と対応策は、「[対応策: 逆シリアル化のオブジェクト間でのアプリ ドメイン](../../../docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)します。|エッジ|  
|<xref:System.IO.Stream.Dispose%2A?displayProperty=fullName>メソッド|[!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]アプリ、[!INCLUDE[wrt](../../../includes/wrt-md.md)]ストリームのアダプターを呼び出して、 <xref:System.IO.Stream.FlushAsync%2A>メソッドから、 <xref:System.IO.Stream.Dispose%2A>メソッドです。|この変更は透過的である必要があります。 開発者は次のようなコードを記述して以前の動作を復元できます。<br /><br /> `using (System.IO.Stream stream = GetWindowsRuntimeStream() As Stream)  {     // do something     await stream.FlushAsync();   }`|透過的|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf-runtime-changes"></a>Windows Communication Foundation (WCF) ランタイム変更  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|[minFreeMemoryPercentageToActiveService](http://msdn.microsoft.com/library/ms731336.aspx)構成の設定|WCF サービスがアクティブになる前にサーバーで使用できる必要のある最小限のメモリを設定します。 防ぐために設計されています<xref:System.OutOfMemoryException>例外です。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、この設定は影響しません。 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] では、設定が確認されます。|Web サーバーで使用できる空きメモリが構成設定によって定義されたパーセンテージよりも小さい場合、例外が発生します。 制約されたメモリ環境で正常に開始し、実行された WCF サービスが今度は失敗することがあります。<br /><br /> 参照してください[対応策: minFreeMemoryPercentageToActiveService 構成の設定](../../../docs/framework/migration-guide/mitigation-minfreememorypercentagetoactiveservice-configuration-setting.md)します。|マイナー|  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.2 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)