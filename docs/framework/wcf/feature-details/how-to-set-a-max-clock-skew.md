---
title: "方法 : 時刻のずれの最大値を設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MaxClockSkew プロパティ"
  - "WCF, カスタム バインディング"
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 方法 : 時刻のずれの最大値を設定する
時刻が重要な要素となる機能は、2 台のコンピューターで時刻の設定が異なっていると失敗する可能性があります。  この可能性を減らすには、`MaxClockSkew` プロパティを <xref:System.TimeSpan> に設定します。  このプロパティは、次の 2 つのクラスで使用できます。  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  重要   セキュリティで保護されたメッセージ交換を行うために、`MaxClockSkew` プロパティへの変更は、サービスまたはクライアントがブートストラップされているときに行う必要があります。  これを行うには、 <xref:System.ServiceModel.Channels.SecurityBindingElement> によって返された <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A> に対してプロパティを設定する必要があります。  
  
 システム提供のバインディングの 1 つでこのプロパティを変更するには、バインディングのコレクションでセキュリティ バインド要素を見つけて、`MaxClockSkew` プロパティを新しい値に設定する必要があります。  <xref:System.ServiceModel.Channels.SecurityBindingElement> から派生される 2 つのクラスは、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> クラスおよび <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラスです。  コレクションからセキュリティ バインディングを取得する場合は、`MaxClockSkew` プロパティを正しく設定するために、これらの型のどちらかにキャストする必要があります。  次の例では、<xref:System.ServiceModel.WSHttpBinding> を使用していますが、これは <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> を使用します。  システム提供の各バインディングで使用するセキュリティ バインディングの型を示す一覧については、「[システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。  
  
### コードを使用して時刻のずれの新しい値を持つカスタム バインディングを作成するには  
  
1.  > [!WARNING]
    >  メモ   コード内の次の名前空間に参照先を追加してください。<xref:System.ServiceModel.Channels>、<xref:System.ServiceModel.Description>、<xref:System.Security.Permissions>、および <xref:System.ServiceModel.Security.Tokens>  
  
     <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、セキュリティ モードを <xref:System.ServiceModel.SecurityMode> に設定します。  
  
2.  <xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを呼び出して、<xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> クラスの新しいインスタンスを作成します。  
  
3.  <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> クラスの <xref:System.ServiceModel.Channels.BindingElementCollection> メソッドを使用して、セキュリティ バインド要素を検索します。  
  
4.  <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> メソッドを使用する場合には、実際の型にキャストします。  次の例では <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 型にキャストしています。  
  
5.  セキュリティ バインド要素の <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> プロパティを設定します。  
  
6.  適切なサービス型とベース アドレスを使用して、<xref:System.ServiceModel.ServiceHost> を作成します。  
  
7.  <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してエンドポイントを追加し、<xref:System.ServiceModel.Channels.CustomBinding> を含めます。  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### 構成で MaxClockSkew を設定するには  
  
1.  [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素セクションに [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を作成します。  
  
2.  [\<binding\>](../../../../docs/framework/misc/binding.md) 要素を作成し、`name` 属性を適切な値に設定します。  `MaxClockSkewBinding` に設定する方法の例を次に示します。  
  
3.  エンコーディング要素を追加します。  下の例では、[\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)を追加しています。  
  
4.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を追加し、`authenticationMode` 属性を適切に設定します。  次の例では、この属性を `Kerberos` に設定して、サービスが Windows 認証を使用するように指定しています。  
  
5.  [\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)を追加し、`maxClockSkew` 属性を `"##:##:##"` の書式の値に設定します。  次の例では 7 分に設定しています。  必要に応じて、[\<localServiceSettings\>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)を追加し、`maxClockSkew` 属性を適切に設定します。  
  
6.  transport 要素を追加します。  下の例では、[\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)を使用しています。  
  
7.  セキュリティで保護されたメッセージ交換を行うために、セキュリティ設定は、[\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 要素のブートストラップ時に行う必要があります。  
  
    ```  
  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    ```  
  
## 参照  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)