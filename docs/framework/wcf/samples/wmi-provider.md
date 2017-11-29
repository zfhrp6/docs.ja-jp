---
title: "WMI プロバイダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a0a64516bea4204eb782013e718c2fa26c6024b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="wmi-provider"></a>WMI プロバイダー
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に組み込まれている Windows Management Instrumentation (WMI) プロバイダーを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのデータを実行時に収集する方法を示します。 また、このサンプルでは、ユーザー定義の WMI オブジェクトをサービスに追加する方法も示します。 サンプル用の WMI プロバイダーをアクティブ化、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)からデータを収集する方法を説明し、`ICalculator`実行時にサービス。  
  
 WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。 WMI SDK の詳細については、次を参照してください。 [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx)です。 WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は WMI プロバイダーを実装しています。これは、WBEAM と互換性のあるインターフェイスを通して実行時にインストルメンテーションを公開するコンポーネントです。 管理ツールは、実行時にインターフェイスを介してサービスに接続できます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、アドレス、バインディング、動作、リスナーなどのサービスの属性を公開します。  
  
 組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにされます。 これには、`wmiProviderEnabled`の属性、 [\<診断 >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)で、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションで、次の例のように構成:  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 この構成エントリには、WMI インターフェイスが開示されます。 管理アプリケーションはこのインターフェイスを通して接続し、アプリケーションの Management Instrumentation にアクセスできるようになります。  
  
## <a name="custom-wmi-object"></a>カスタム WMI オブジェクト  
 WMI オブジェクトをサービスに追加すると、組み込みの WMI プロバイダーの情報と共にユーザー定義の情報を開示できます。 これは、Installutil.exe アプリケーションを使用してサービスのスキーマを WMI に公開することによって実現されます。 これを行うための手順および詳細情報は、このトピックの最後のセットアップ手順で示します。  
  
## <a name="accessing-wmi-information"></a>WMI 情報へのアクセス  
 WMI データには、複数の異なる方法でアクセスできます。 マイクロソフトは、スクリプト用、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] アプリケーション用、C++ アプリケーション用、および [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用の WMI API を提供しています (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp)。  
  
 このサンプルでは、2 つの Java スクリプトを使用します。1 つ目は、コンピューター上で実行されているサービスとその一部のプロパティを列挙するスクリプトで、2 つ目はユーザー定義の WMI データを表示するスクリプトです。 スクリプトは、WMI プロバイダーへの接続を開き、データを解析し、収集されたデータを表示します。  
  
 サンプルを開始して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実行中インスタンスを作成します。 サービスの実行中は、コマンド プロンプトで次のコマンドを入力することによって、それぞれの Java スクリプトを実行してください。  
  
```  
cscript EnumerateServices.js  
```  
  
 スクリプトは、サービスに含まれているインストルメンテーションにアクセスし、次の出力を生成します。  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 次に、2 つ目の Java スクリプトを実行して、ユーザー定義の WMI データを表示します。  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 スクリプトは、サービスに含まれているユーザー定義のインストルメンテーションにアクセスし、次の出力を生成します。  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 この出力は、コンピューター上で 1 つのサービスが実行中であることを示しています。 サービスは、`ICalculator` コントラクトを実装する 1 つのエンドポイントを公開します。 このエンドポイントによって実装されている動作とバインディングの設定は、メッセージ スタックの個々の要素の合計として表示されます。  
  
 WMI は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャの Management Instrumentation を公開するだけではありません。 独自のドメイン固有のデータ アイテムを、同じ機構を使用して公開できます。 WMI は、Web サービスの検査と制御のための統一された機構です。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  確実に実行する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  サービス スキーマを WMI に公開します。これを行うには、ホスト ディレクトリ内の service.dll ファイルに対して、InstallUtil.exe (既定の場所は "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") を実行します。 この手順を実行する必要があるのは、service.dll ファイルを変更した場合のみです。 詳細については、「アプリケーションのインストルメント化による管理情報の提供」(http://msdn2.microsoft.com/library/ms186147.aspx) の「方法: インストルメント化されたアプリケーションの WMI にスキーマを公開する」セクションを参照してください。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
    > [!NOTE]
    >  ASP.NET のインストール後に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をインストールした場合は、"%WINDIR%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x を実行し、ASPNET アカウントに WMI オブジェクトを公開する権限を付与する必要がある場合があります。  
  
5.  コマンド `cscript EnumerateServices.js` または `cscript EnumerateCustomObjects.js` を使用して、WMI を通じて示されるサンプルのデータを表示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
