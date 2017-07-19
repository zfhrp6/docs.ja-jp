---
title: "ASP.NET クライアントでのデータ バインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# ASP.NET クライアントでのデータ バインディング
このサンプルでは、一般的な [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスによって返されたデータを Web フォーム アプリケーションにバインドする方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、要求\/応答通信パターンを定義するコントラクトを実装するサービスを示します。このサンプルは、ブラウザからアクセスできるクライアントの Web フォーム アプリケーションと、インターネット インフォメーション サービス \(IIS\) によってホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスとで構成されています。  
  
 サービスは、要求\/応答通信パターンを定義するコントラクトを実装します。コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] クライアントの .aspx ページには DataGrid Web コントロールが定義されています。このコントロールには、サービスによって返されるデータのグラフィック表示が含まれます。.aspx ページのコードによって気象データ用の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが呼び出され、そのデータは `WeatherData` オブジェクトの配列に返されます。DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。このすべてのコードは .`aspx` ページの `Page_Load` メソッドに格納されています。したがって、ブラウザのページが更新されるたびに DataGrid 内のデータも更新されます。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。開発用 Web サーバーを起動するには、コマンド プロンプトで「`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`」と入力します。次に、http:\/\/localhost:8000\/client に移動します。このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## 参照