---
title: '方法 : カスタム証明書検証を使用するサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: cc768f5e5086e6eba1ccac9d969eac14e14ceb2f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808144"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>方法 : カスタム証明書検証を使用するサービスを作成する
このトピックでは、カスタム証明書検証を実装する方法、クライアントまたはサービスの資格情報の設定により、既定の証明書検証機能を、カスタム証明書検証で置き換える方法について解説します。  
  
 X.509 証明書がクライアントまたはサービスの認証に使用されている場合既定で Windows Communication Foundation (WCF) を使用して、Windows 証明書ストアと Crypto API 証明書を検証し、信頼されていることを確認してください。 ただし、組み込みの検証機能では不十分で、処理内容を変更する必要がある場合もあります。 WCF には、ユーザーがカスタム証明書検証を追加することで、検証ロジックを変更する簡単な方法が用意されています。 カスタム証明書検証が指定されている場合、WCF は組み込みの証明書の検証ロジックを使用しませんが、代わりにカスタムの検証に依存します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-create-a-custom-certificate-validator"></a>カスタムの証明書検証機能を作成するには  
  
1.  <xref:System.IdentityModel.Selectors.X509CertificateValidator> から派生する新しいクラスを定義します。  
  
2.  抽象メソッドである <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> を実装します。 検証対象の証明書が、引数としてこのメソッドに渡されます。 検証処理の結果、証明書が無効であると判断されると、このメソッドは、<xref:System.IdentityModel.Tokens.SecurityTokenValidationException> という例外をスローします。 有効であればそのまま呼び出し元に制御を返します。  
  
    > [!NOTE]
    >  クライアントに認証エラーを返すには、<xref:System.ServiceModel.FaultException> メソッドで <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> をスローします。  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>サービス構成でカスタム検証処理を指定するには  
  
1.  追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素、および[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)を[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素。  
  
2.  追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)設定と、`name`属性を適切な値にします。  
  
3.  追加、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を`<behavior>`要素。  
  
4.  `<clientCertificate>` 要素を `<serviceCredentials>` 要素に追加します。  
  
5.  追加、 [\<認証 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)を`<clientCertificate>`要素。  
  
6.  `customCertificateValidatorType` 属性に検証処理の型を設定します。 この属性に型の名前空間と名前を設定する例を以下に示します。  
  
7.  `certificateValidationMode` 属性を `Custom` に設定します。  
  
    ```xml  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>クライアント側の設定でカスタム証明書検証を指定するには  
  
1.  追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素、および[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)を[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素。  
  
2.  追加、 [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)要素。  
  
3.  `<behavior>` 要素を追加し、`name` 属性に適切な値を設定します。  
  
4.  追加、 [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。  
  
5.  追加、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)です。  
  
6.  追加、 [\<認証 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)次の例に示すようにします。  
  
7.  `customCertificateValidatorType` 属性に検証処理の型を設定します。  
  
8.  `certificateValidationMode` 属性を `Custom` に設定します。 この属性に型の名前空間と名前を設定する例を以下に示します。  
  
    ```xml  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>サービス側のコードでカスタム証明書検証を指定するには  
  
1.  <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> プロパティの値としてカスタム証明書検証を指定します。 サービスの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。  
  
2.  <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> に設定します。  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>クライアント側のコードでカスタム証明書検証を指定するには  
  
1.  カスタム証明書検証を、<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> プロパティを使って指定します。 クライアントの資格情報には、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> プロパティを使用してアクセスできます。 (によって生成されたクライアント クラス[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)から派生して常に、<xref:System.ServiceModel.ClientBase%601>クラスです)。  
  
2.  <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> に設定します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 カスタム証明書検証を実装し、サービス側で使用する例を以下に示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
