---
title: "サービス デバッグ動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04520eda9fe7ce2cd461e094fe2cec76d52ccc7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="service-debug-behavior"></a>サービス デバッグ動作
このサンプルでは、サービス デバッグ動作の設定を構成する方法を示します。 サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を実装する、`ICalculator`サービス コントラクト。 このサンプルは、サービス デバッグ動作を構成ファイルで明示的に定義します。 コードで強制的に定義することもできます。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サーバーの Web.config ファイルでは、次のサンプルに示すように、ヘルプ ページと例外処理を有効にするサービス デバッグ動作を定義します。  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)サービス デバッグ動作プロパティの変更を許可する構成要素です。 ユーザーはこの動作を変更して、次を実現することができます。  
  
-   例外が <xref:System.ServiceModel.FaultContractAttribute> を使用して宣言されていない場合でも、サービスでは、アプリケーション コードによってスローされる例外を返すことができます。 これを行うには、`includeExceptionDetailInFaults` を `true` に設定します。 この設定は、サーバーが予期しない例外をスローしている場合のデバッグ時に役立ちます。  
  
    > [!IMPORTANT]
    >  この設定を本運用環境で有効にすると、セキュリティが不十分になります。 サーバーの予期しない例外には、クライアントを対象としていない情報が含まれる場合があるため、`includeExceptionDetailsInFaults` を `true` に設定すると、情報の漏えいが発生する可能性があります。  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)ユーザーを有効にするにまたは、ヘルプ ページを無効にすることもできます。 各サービスは、サービスの WSDL を取得するエンドポイントなど、サービスに関する情報が含まれるヘルプ ページをオプションで公開できます。 これを有効にするには、`httpHelpPageEnabled` プロパティを `true` に設定します。 これにより、サービスのベース アドレスへの GET 要求に対して、ヘルプ ページを返すことができます。 このアドレスは、別の属性 `httpHelpPageUrl` を設定して変更できます。 HTTP の代わりに HTTPS を使用すると、このアドレスをセキュリティ保護できます。 これを行うには、`httpsHelpPageEnabled` と `httpsHelpPageUrl` を設定します。  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 最初の 3 つの操作 (加算、減算、乗算) が正常に行われる必要があります。 最後の操作 (除算) は、0 による除算の例外によってエラーとなります。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>関連項目
