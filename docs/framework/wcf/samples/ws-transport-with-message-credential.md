---
title: "メッセージ資格情報付き WS トランスポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# メッセージ資格情報付き WS トランスポート
このサンプルでは、メッセージに含まれるクライアント資格情報と組み合わせて SSL トランスポート セキュリティを使用する例を示します。このサンプルでは、`wsHttpBinding` バインディングを使用します。  
  
 既定で、`wsHttpBinding` バインディングは HTTP 通信を実現します。トランスポート セキュリティ用に構成すると、バインディングは HTTPS 通信をサポートします。HTTPS により、通信回線を介して送信されるメッセージについての機密性および整合性の保護が実現します。ただし、サービスに対するクライアントの認証に使用できる一連の認証機構は、HTTPS トランスポートのサポート範囲に限定されます。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、この制限を克服するためにデザインされた、`TransportWithMessageCredential` セキュリティ モードが用意されています。このセキュリティ モードが構成されると、送信メッセージの機密性および整合性を実現してサービス認証を実行する、トランスポート セキュリティが使用されます。ただし、クライアント認証は、クライアント資格情報をメッセージに直接格納することによって実行されます。これにより、トランスポート セキュリティ モードでのパフォーマンス上の利点を保持しながら、クライアント認証のメッセージ セキュリティ モードでサポートされる、任意の資格情報の種類を使用できます。  
  
 このサンプルでは、サービスに対するクライアントの認証に `UserName` 資格情報が使用されます。  
  
 このサンプルは、電卓サービスを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。`wsHttpBinding` バインディングは、クライアントとサービスのアプリケーション構成ファイルに指定され、構成されます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サンプル内のプログラム コードは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」サービスのプログラム コードとほとんど同じです。`GetCallerIdentity` サービス コントラクトによって追加された操作が 1 つあります。この操作は、呼び出し元の ID の名前を呼び出し元に返します。  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 このサンプルをビルドして実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。次に示すクライアント用構成の例のように、構成ファイル設定でエンドポイントとバインディングを定義すると、`TransportWithMessageCredential` セキュリティ モードが有効になります。  
  
```  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 アドレス指定では https:\/\/ スキームを使用しています。このバインディング構成により、セキュリティ モードが `TransportWithMessageCredential` に設定されます。同じセキュリティ モードが、サービスの Web.config ファイルで指定される必要があります。  
  
 このサンプルで使用する証明書は Makecert.exe で作成されたテスト証明書なので、ブラウザで https:\/\/localhost\/servicemodelsamples\/service.svc のような https: アドレスにアクセスしようとするとセキュリティ警告が表示されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントがテスト証明書に対して問題なく動作するようにするには、クライアントにコードを追加して、セキュリティ警告を非表示にする必要があります。そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
  
```  
  
 このサンプルを実行する場合は、操作要求および応答はクライアントのコンソール ウィンドウに表示されます。クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### サンプルをセットアップしてビルドし、実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  「[インターネット インフォメーション サービス \(IIS\) サーバー証明書インストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)」が実行済みであることを確認します。  
  
3.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  単一コンピュータ構成か複数コンピュータ構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照