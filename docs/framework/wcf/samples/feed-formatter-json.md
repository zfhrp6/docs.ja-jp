---
title: "フィード フォーマッタ (JSON)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d6e1a2fe05d041d28d897e8effab3dfddb98845
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="feed-formatter-json"></a>フィード フォーマッタ (JSON)
このサンプルでは、カスタムの <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> を使用することにより JSON (JavaScript Object Notation) 形式の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> クラスのインスタンスをシリアル化する方法を示します。  
  
## <a name="architecture-of-the-sample"></a>サンプルのアーキテクチャ  
 このサンプルは `JsonFeedFormatter` を継承する <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> という名前のクラスを実行します。 `JsonFeedFormatter` クラスは <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存し、JSON 形式でデータの読み取りと書き込みを行います。 内部的には、フォーマッタは `JsonSyndicationFeed` および `JsonSyndicationItem` という名前のデータ コントラクト型のカスタム セットを使用し、シリアライザによって生成される JSON データの形式を制御します。 これらの実装の詳細はエンド ユーザーには表示されず、標準的な <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationItem> クラスに対する呼び出しを行うことができます。  
  
## <a name="writing-json-feeds"></a>JSON フィードの書き込み  
 次のコード例に示すように、JSON フィードの書き込みは `JsonFeedFormatter` (このサンプルで実装) を <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と共に使用して実行できます。  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>JSON フィードの読み取り  
 次のコードに示すように、JSON 形式のデータのストリームからの <xref:System.ServiceModel.Syndication.SyndicationFeed> の取得は `JsonFeedFormatter` を使用して実行できます。  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a>関連項目
