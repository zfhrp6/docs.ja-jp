---
title: ".NET Framework アプリケーションでのキャッシュ | Microsoft Docs"
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
  - "ASP.NET のキャッシュ"
  - "キャッシュ [.NET Framework]"
  - "キャッシュ [ASP.NET]"
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
caps.latest.revision: 26
author: "tdykstra"
ms.author: "tdykstra"
manager: "wpickett"
caps.handback.revision: 26
---
# .NET Framework アプリケーションでのキャッシュ
キャッシュを使用するとメモリにデータを格納しておくことができるのですぐにアクセスできます。  データに再度アクセスするとき、アプリケーションは元のソースからデータを取得する代わりにキャッシュからデータを取得できます。  これにより、パフォーマンスとスケーラビリティが向上します。  さらにキャッシュを使用するとデータ ソースが一時的に使用できない場合もデータが使用可能になります。  
  
 .NET Framework のキャッシュ機能を使用すると、Windows のクライアント アプリケーションとサーバー アプリケーション \(ASP.NET を含む\) の両方のパフォーマンスとスケーラビリティが向上します。  
  
> [!NOTE]
>  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 以前のバージョンでは、ASP.NET の <xref:System.Web.Caching> 名前空間にメモリ内キャッシュの実装が含まれていました。  以前のバージョンの [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、<xref:System.Web> 名前空間でしかキャッシュを使用できないため、ASP.NET クラスに対する依存関係が必要になります。  .NET Framework 4 では、<xref:System.Runtime.Caching> 名前空間に、Web アプリケーションでも Web アプリケーション以外でも使用できるように設計された API が用意されています。  
  
## キャッシュされたデータ  
 情報のキャッシュは、<xref:System.Runtime.Caching> 名前空間のクラスを使用して行うことができます。  この名前空間のキャッシュ クラスには次の機能があります。  
  
-   カスタム キャッシュ実装を作成する基盤となる抽象型  
  
-   メモリ内オブジェクト キャッシュの具象実装  
  
 抽象基本キャッシュ クラス \(<xref:System.Runtime.Caching.ObjectCache>\) で、次のキャッシュ操作を定義します。  
  
-   キャッシュ エントリの作成と管理  
  
-   有効期限と削除の情報の指定  
  
-   キャッシュ エントリの変更に応答して発生するイベントのトリガー  
  
 <xref:System.Runtime.Caching.MemoryCache> クラスは、<xref:System.Runtime.Caching.ObjectCache> クラスのメモリ内オブジェクト キャッシュの実装です。  <xref:System.Runtime.Caching.MemoryCache> クラスを使用して、ほとんどのキャッシュ操作を実行できます。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> クラスは、<xref:System.Web.Caching> 名前空間で定義される ASP.NET キャッシュ オブジェクトを原型としています。  そのため、内部キャッシュ ロジックは、以前のバージョンの ASP.NET のロジックに似ています。  
  
 WPF アプリケーションでキャッシュを使用する方法の例については、「[チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)」を参照してください。  
  
## ASP.NET アプリケーションにおけるキャッシュ  
 <xref:System.Runtime.Caching> 名前空間のキャッシュ クラスには、ASP.NET でデータをキャッシュするための機能が用意されています。  
  
> [!NOTE]
>  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 以前のバージョンを対象とするアプリケーションの場合は、<xref:System.Web.Caching> 名前空間に定義されているキャッシュ クラスを使用する必要があります。  詳細については、「[ASP.NET Caching Overview](../Topic/ASP.NET%20Caching%20Overview.md)」を参照してください。  
  
> [!NOTE]
>  新しいアプリケーションを開発するときは、<xref:System.Runtime.Caching.MemoryCache> クラスを使用することをお勧めします。  <xref:System.Runtime.Caching> 名前空間の API は、<xref:System.Web.Caching.Cache> 名前空間の API に似ています。  そのため、以前のバージョンの ASP.NET でキャッシュを使用したことがあれば、この API もすぐに理解できます。ASP.NET アプリケーションでキャッシュを使用する方法の例については、「[Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md)」を参照してください。  
  
### 出力のキャッシュ  
 アプリケーション データを手動でキャッシュするには、ASP.NET の <xref:System.Runtime.Caching.MemoryCache> クラスを使用します。ASP.NET では、出力キャッシュもサポートされており、ページ、コントロール、および HTTP 応答の生成された出力をメモリに格納することができます。  出力キャッシュを構成するには、ASP.NET Web ページで宣言するか、Web.config ファイルの設定を使用します。  詳細については、「[caching の outputCache 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/47cd2b47-316f-4dfd-bbf8-539be3066fee)」を参照してください。  
  
 ASP.NET では、カスタム出力キャッシュ プロバイダーを作成して出力キャッシュを拡張できます。  カスタム プロバイダーを使用することで、キャッシュされた内容を、ディスク、クラウド ストレージ、分散キャッシュ エンジンなどの他のストレージ デバイスに格納することができます。  カスタム出力キャッシュ プロバイダーを作成するには、<xref:System.Web.Caching.OutputCacheProvider> クラスから派生するクラスを作成し、そのカスタム出力キャッシュ プロバイダーを使用するようにアプリケーションを構成します。  
  
## WCF REST サービスにおけるキャッシュ  
 .NET Framework では、WCF REST サービスに、ASP.NET で提供されている宣言による出力キャッシュを利用できます。このため、WCF REST サービス操作からの応答をキャッシュできます。  キャッシュ用に構成されているサービスに対してユーザーが HTTP GET 要求を送信すると、ASP.NET はキャッシュされた応答を送り返し、サービス メソッドは呼び出されません。  キャッシュの有効期限が切れると、次にユーザーが HTTP GET 要求を送信したときに、サービス メソッドが呼び出され、応答が再度キャッシュされます。  
  
 .NET Framework では、条件付き HTTP GET キャッシュを実装することもできます。  そのほかのシナリオでは、"に説明されているように、インテリジェントな HTTP キャッシュを実装するために、HTTP GET の要求がサービスでよく使用 [HTTP 固有](http://go.microsoft.com/fwlink/?LinkId=165800)されます。  詳細については、参照します [WCF Web HTTP サービスのキャッシュ サポート](http://go.microsoft.com/fwlink/?LinkId=184598)。  
  
## .NET Framework のキャッシュの拡張  
 .NET Framework のキャッシュは拡張できるように設計されています。  <xref:System.Runtime.Caching.ObjectCache> クラスを使用して、カスタム キャッシュ実装を作成することができます。  このクラスには、Windows フォーム、Windows Presentation Foundation \(WPF\)、Windows Communications Foundation \(WCF\) などのあらゆるマネージ アプリケーションで使用できるメンバーが用意されています。  キャッシュの拡張は、別のストレージ機構を使用するキャッシュ クラスを作成したり、キャッシュ操作を詳しく制御したりする場合に行います。  
  
 キャッシュを拡張するには、次の操作を行います。  
  
-   <xref:System.Runtime.Caching.ObjectCache> クラスから派生するカスタム クラスを作成し、その派生クラスにカスタム キャッシュを実装します。  
  
-   <xref:System.Runtime.Caching.MemoryCache> クラスから派生するクラスを作成し、その派生クラスをカスタマイズまたは拡張します。  その方法の例については、"を参照してください [ASP.NET アプリケーションの Caching Application Data by Using Multiple Cache オブジェクト](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx)。  
  
-   <xref:System.Web.Caching.OutputCacheProvider> クラスから派生するクラスを作成し、そのカスタム出力キャッシュ プロバイダーを使用するようにアプリケーションを構成します。  
  
 詳細については、Scott Guthrie のブログ [ASP.NET 4 の Extensible Output Caching \(and .NET 2010 対 4.0 のシリーズ\)](http://go.microsoft.com/fwlink/?LinkId=185772) のエントリを参照します。  
  
## 参照  
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching.MemoryCache>   
 [チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)   
 [Walkthrough: Caching Application Data in ASP.NET](../Topic/Walkthrough:%20Caching%20Application%20Data%20in%20ASP.NET.md)