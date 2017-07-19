---
title: "WebContentTypeMapper のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WebContentTypeMapper のサンプル
このサンプルでは、新しいコンテンツ タイプを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] メッセージの本文の書式に割り当てる方法を示します。  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> 要素は、Web メッセージ エンコーダーをプラグインします。これによって、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、JSON、XML、または生のバイナリ メッセージを同じエンドポイントで受信できるようになります。このエンコーダは、要求の HTTP コンテンツ タイプを調べて、メッセージ本文の書式を決定します。このサンプルでは、コンテンツ タイプと本文書式との間の割り当てを制御するための <xref:System.ServiceModel.Channels.WebContentTypeMapper> クラスを示します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、各コンテンツ タイプの既定の割り当てが用意されています。たとえば、`application/json` は JSON に割り当てられ、`text/xml` は XML に割り当てられています。JSON または XML に割り当てられていないコンテンツ タイプは、生のバイナリ形式に割り当てられます。  
  
 場合によっては \(プッシュ スタイルの API など\)、クライアントによって返されるコンテンツ タイプがサービス開発者によって制御されないことがあります。たとえば、クライアントは `application/json` としてではなく `text/javascript` として JSON を返す場合があります。この場合、サービス開発者は、特定のコンテンツ タイプを正しく処理できるように、次のサンプル コードに示すような <xref:System.ServiceModel.Channels.WebContentTypeMapper> の派生型を指定する必要があります。  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
  
```  
  
 この派生型は、<xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> メソッドをオーバーライドする必要があります。このメソッドは、`contentType` 引数を評価して、<xref:System.ServiceModel.Channels.WebContentFormat>、<xref:System.ServiceModel.Channels.WebContentFormat>、<xref:System.ServiceModel.Channels.WebContentFormat>、または <xref:System.ServiceModel.Channels.WebContentFormat> のいずれかの値を返す必要があります。<xref:System.ServiceModel.Channels.WebContentFormat> の戻り値は、Web メッセージ エンコーダの既定の割り当てによって決まります。前のサンプル コードでは、`text/javascript` コンテンツ タイプが JSON に割り当てられ、その他のすべての割り当ては変わりません。  
  
 `JsonContentTypeMapper` クラスを使用するには、Web.config 内で次のコードを使用します。  
  
```  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper の使用要件を検証するには、Web.config ファイルから contentTypeMapper 属性を削除します。`text/javascript` を使用して JSON コンテンツを送信しようとすると、クライアント ページの読み込みに失敗します。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従って、ソリューション WebContentTypeMapperSample.sln をビルドします。  
  
3.  http:\/\/localhost\/ServiceModelSamples\/JCTMClientPage.htm に移動します \(プロジェクト ディレクトリ内からブラウザーで JCTMClientPage.htm を開かないでください\)。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## 参照