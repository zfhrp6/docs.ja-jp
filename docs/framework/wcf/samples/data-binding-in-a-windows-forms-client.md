---
title: "Windows フォーム クライアントのデータ バインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Windows フォーム クライアントのデータ バインディング
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスによって返されたデータを Windows フォーム アプリケーションでバインドする方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。  
  
 このサンプルでは、要求\/応答通信パターンを定義するコントラクトを実装するサービスを示します。このサンプルは、クライアントの Windows フォーム アプリケーション \(.exe\) と、インターネット インフォメーション サービス \(IIS\) によってホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で構成されています。  
  
 コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 データ バインディングは、Windows フォーム アプリケーションのクライアントで発生します。`DataGridView` は Windows フォーム デザイナで定義し、データをグラフィック表示します。さらに、`BindingSource` という中継局も作成されます。`BindingSource` のデータ ソースは、サービスによって返されるデータ配列に設定されます。`BindingSource` の目的は、データとデータ ビュー間を間接化するレイヤを提供することです。データとの対話 \(移動、並べ替え、フィルタ処理、更新など\) はすべて、`BindingSource` コンポーネントを呼び出すことによって実行します。`DataGridView` へのデータ バインディングを行うには、`DataGridView` の `datasource` を `BindingSource` オブジェクトに設定します。これで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから返されるすべてのデータがユーザーに対してグラフィック表示されます。ユーザーがボタンをクリックするたびに、返されたデータはデータ バインドされた `DataGridView` で自動的に更新されます。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## 参照