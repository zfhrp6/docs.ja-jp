---
title: "方法 : クライアントの資格情報の種類を指定する | Microsoft Docs"
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
  - "セキュリティ資格情報, SOAP メッセージへの追加"
  - "WCF, セキュリティ"
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : クライアントの資格情報の種類を指定する
セキュリティ モード \(トランスポートまたはメッセージ\) を設定してから、クライアント資格情報の種類を指定することができます。このプロパティでは、クライアントが認証時にサービスに提供する必要のある資格情報の種類を指定します。セキュリティ モードの設定 \(クライアントの資格情報の種類を設定する前に必要な手順\) [!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[方法 : セキュリティ モードを設定する](../../../docs/framework/wcf/how-to-set-the-security-mode.md)」を参照してください。  
  
### コードでクライアント資格情報の種類を設定するには  
  
1.  サービスで使用されるバインドのインスタンスを作成します。この例では、<xref:System.ServiceModel.WSHttpBinding> バインドを使用します。  
  
2.  <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティに適切な値を設定します。この例では、メッセージ モードを使用します。  
  
3.  <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> プロパティに適切な値を設定します。この例では、Windows 認証 \(<xref:System.ServiceModel.MessageCredentialType>\) を使用するように設定します。  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### 構成でクライアント資格情報の種類を設定するには  
  
1.  [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 要素を構成ファイルに追加します。  
  
2.  子要素として [\<bindings\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素を追加します。  
  
3.  適切なバインドを追加します。この例では、[\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 要素を使用します。  
  
4.  [\<binding\>](../../../docs/framework/misc/binding.md) 要素を追加し、`name` 属性に適切な値を設定します。この例では、"SecureBinding" という名前を使用します。  
  
5.  `<security>` バインドを追加します。`mode` 属性を適切な値に設定します。この例では、`"Message"` に設定します。  
  
6.  セキュリティ モードによって、`<message>` 要素と `<transport>` 要素のどちらかを追加します。`clientCredentialType` 属性を適切な値に設定します。この例では、`"Windows"` を使用します。  
  
    ```  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## 参照  
 [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)   
 [方法 : セキュリティ モードを設定する](../../../docs/framework/wcf/how-to-set-the-security-mode.md)