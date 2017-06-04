---
title: "WSHttpBinding | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WS プロファイル バインディング"
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
caps.latest.revision: 39
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 39
---
# WSHttpBinding
このサンプルでは、一般的なサービスと一般的なクライアントを、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して実装する方法を示します。このサンプルは、クライアント コンソール プログラム \(client.exe\) と、インターネット インフォメーション サービス \(IIS\) によってホストされるサービス ライブラリで構成されています。サービスは、要求\/応答通信パターンを定義するコントラクトを実装します。このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 \(加算、減算、乗算、および除算\) を公開しています。クライアントは指定された算術演算を同期要求し、サービスは結果と共に応答します。クライアント アクティビティは、コンソール ウィンドウに表示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用して `ICalculator` コントラクトを公開します。このバインディングの構成は、次のように Web.config ファイルで展開されています。  
  
```  
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 ベース `binding` 要素で `maxReceivedMessageSize` 値を使用すると、受信メッセージの最大サイズ \(バイト単位\) を構成できます。`hostNameComparisonMode` 値を使用すると、メッセージの非多重化を行ってサービスに変換する際にホスト名を考慮するかどうかを構成できます。`messageEncoding` 値を使用すると、メッセージのテキスト エンコーディングまたは MTOM エンコーディングを使用するかどうかを構成できます。`textEncoding` 値を使用すると、メッセージの文字エンコーディングを構成できます。`bypassProxyOnLocal` 値を使用すると、ローカル通信に HTTP プロキシを使用するかどうかを構成できます。現在のトランザクションをフローするかどうかは、`transactionFlow` 値で構成されます \(操作がトランザクション フロー用に構成されている場合\)。  
  
 [\<reliableSession\>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) 要素では、信頼できるセッションが有効かどうかは、ブール値 enabled で構成されます。メッセージの順序が保持されるかどうかは、`ordered` 値で構成されます。エラーになる前の、セッションのアイドル状態の期間は、`inactivityTimeout` 値で構成されます。  
  
 [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)では、使用するセキュリティ モードは `mode` 値で構成されます。このサンプルでは、メッセージ セキュリティが使用されており、このため [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)が [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)の内側で指定されています。  
  
 このサンプルを実行する場合は、操作要求および応答はクライアントのコンソール ウィンドウに表示されます。クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
  
    ```  
  
2.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
3.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  単一コンピュータ構成か複数コンピュータ構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照