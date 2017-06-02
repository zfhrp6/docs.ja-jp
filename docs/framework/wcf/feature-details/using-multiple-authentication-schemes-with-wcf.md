---
title: "WCF での複数の認証方式の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF での複数の認証方式の使用
WCF では、単一のエンドポイントに複数の認証方式を指定できるようになりました。  さらに、Web ホスト サービスは、認証設定を IIS から直接継承できます。  自己ホスト型サービスは、使用可能な認証方式を指定できます。  IIS での認証設定の詳細については、「[IIS の認証](http://go.microsoft.com/fwlink/?LinkId=232458)」を参照してください。  
  
## IIS でホストされるサービス  
 IIS でホストされるサービスでは、IIS で使用する認証方式を設定します。  その後、サービスの web.config ファイル内のバインディング構成で、次の XML スニペットで示すように clientCredential の種類を "InheritedFromHost" として指定します。  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 ServiceAuthenticationBehavior または \<serviceAuthenticationManager\> 要素を使用して、認証方式のサブセットのみをサービスで使用するよう指定できます。  これをコードで構成する場合は、次のコード スニペットに示すように ServiceAuthenticationBehavior を使用します。  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
  
```  
  
 config ファイルでこれを構成する場合は、次の XML スニペットに示すように \<serviceAuthenticationManager\> 要素を使用します。  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 この結果、IIS で選択した内容に応じて、ここに示されている認証方式のサブセットに限り、サービス エンドポイントへの適用が検討されます。  つまり、開発者は serviceAuthenticationManager の一覧から基本認証を省略することによって、リストから基本認証を除外することができます。IIS で有効になっている場合でも、サービス エンドポイントには適用されません。  
  
## 自己ホスト型サービス  
 自己ホスト型サービスは、設定を継承する IIS がないため、構成方法が少し異なります。  ここで、\<serviceAuthenticationManager\> 要素または ServiceAuthenticationBehavior を使用して、継承される認証設定を指定します。  コード例を次に示します。  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
  
```  
  
 config では、次のようになります。  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 その後、次の XML スニペットに示すように、バインディング設定で InheritFromHost を指定できます。  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 または、次の構成スニペットに示すように、HTTP トランスポート バインド要素で認証方式を設定することにより、カスタム バインディングで認証方式を指定することもできます。  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
  
```  
  
## 参照  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)   
 [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)   
 [システムが提供するバインディングの構成](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)   
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)   
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)