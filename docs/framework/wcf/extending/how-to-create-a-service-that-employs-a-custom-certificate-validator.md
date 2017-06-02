---
title: "方法 : カスタム証明書検証を使用するサービスを作成する | Microsoft Docs"
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
  - "WCF, 認証"
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : カスタム証明書検証を使用するサービスを作成する
このトピックでは、カスタム証明書検証を実装する方法、クライアントまたはサービスの資格情報の設定により、既定の証明書検証機能を、カスタム証明書検証で置き換える方法について解説します。  
  
 X.509 証明書を使ってクライアントやサービスを認証する場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の既定では、Windows 証明書ストアと Crypto API を使用して証明書が検証され、信頼できるかどうかが確認されます。  ただし、組み込みの検証機能では不十分で、処理内容を変更する必要がある場合もあります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザーがカスタムの証明書検証機能を追加して、検証ロジックを簡単に変更できます。  カスタムの証明書検証機能が指定されている場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、組み込みの検証機能ではなく、カスタムの検証処理のみが使用されます。  
  
## 手順  
  
#### カスタムの証明書検証機能を作成するには  
  
1.  <xref:System.IdentityModel.Selectors.X509CertificateValidator> から派生する新しいクラスを定義します。  
  
2.  抽象メソッドである <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> を実装します。  検証対象の証明書が、引数としてこのメソッドに渡されます。  検証処理の結果、証明書が無効であると判断されると、このメソッドは、<xref:System.IdentityModel.Tokens.SecurityTokenValidationException> という例外をスローします。  有効であればそのまま呼び出し元に制御を返します。  
  
    > [!NOTE]
    >  クライアントに認証エラーを返すには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドで <xref:System.ServiceModel.FaultException> をスローします。  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### サービス構成でカスタム検証処理を指定するには  
  
1.  [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素に [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素と [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) を追加します。  
  
2.  [\<behavior\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)を追加し、`name` 属性に適切な値を設定します。  
  
3.  [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を `<behavior>` 要素に追加します。  
  
4.  `<clientCertificate>` 要素を `<serviceCredentials>` 要素に追加します。  
  
5.  `<clientCertificate>` 要素に [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) を追加します。  
  
6.  `customCertificateValidatorType` 属性に検証処理の型を設定します。  この属性に型の名前空間と名前を設定する例を以下に示します。  
  
7.  `certificateValidationMode` 属性を `Custom` に設定します。  
  
    ```  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### クライアント側の設定でカスタム証明書検証を指定するには  
  
1.  [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素に [\<behaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素と [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) を追加します。  
  
2.  [\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) 要素を追加します。  
  
3.  `<behavior>` 要素を追加し、`name` 属性に適切な値を設定します。  
  
4.  [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 要素を追加します。  
  
5.  [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) を追加します。  
  
6.  次の例に示すように、[\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) を追加します。  
  
7.  `customCertificateValidatorType` 属性に検証処理の型を設定します。  
  
8.  `certificateValidationMode` 属性を `Custom` に設定します。  この属性に型の名前空間と名前を設定する例を以下に示します。  
  
    ```  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### サービス側のコードでカスタム証明書検証を指定するには  
  
1.  <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> プロパティの値としてカスタム証明書検証を指定します。  サービスの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。  
  
2.  <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode> に設定します。  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### クライアント側のコードでカスタム証明書検証を指定するには  
  
1.  カスタム証明書検証を、<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> プロパティを使って指定します。  クライアントの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。  [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) によって生成されるクライアント クラスは、常に <xref:System.ServiceModel.ClientBase%601> クラスから派生したものです。  
  
2.  <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode> に設定します。  
  
## 例  
  
### 説明  
 カスタム証明書検証を実装し、サービス側で使用する例を以下に示します。  
  
### コード  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## 参照  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>