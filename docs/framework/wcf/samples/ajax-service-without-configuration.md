---
title: "構成を使用しない AJAX サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf0ed4e1c06bc464b8ebeffbf3be10de3064f479
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-service-without-configuration"></a>構成を使用しない AJAX サービス
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、構成設定を使用せずに基本的な ASP.NET AJAX (Asynchronous JavaScript and XML) サービス (Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。 このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、`ScriptManager` コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。 使用する例については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。、 [Ajax サンプル](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。 」の説明に従って、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルについては、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>サービスをホストするために使用します。  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。 構成の変更をエンドポイントに対して行う必要がない場合、\<システムです。ServiceModel > セクションは、サービスの Web.config ファイルから完全に削除することができます。 Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。 そうでない場合は、Web.config ファイル全体を削除できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  セットアップ手順を実行することを確認してください。 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションをビルドします ConfigFreeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
3.  http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx に移動します (プロジェクト ディレクトリからブラウザーで ConfigFreeClientPage.aspx を開かないでください)。  
  
> [!NOTE]
>  このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。 有効になっている場合は、Windows 認証を無効にしてください。 サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。  
  
## <a name="see-also"></a>関連項目  
 [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
