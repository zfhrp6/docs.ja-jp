---
title: "&lt;secureConversationBootstrap&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;secureConversationBootstrap&gt;
セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。  
  
## 構文  
  
```  
  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## 型  
 `Type`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`allowSerializedSigningTokenOnReply`|省略可能です。  シリアル化されたトークンを応答で使用できる場合に指定するブール値。  既定値は `false` です。  二重バインドを使用する場合、この設定の既定値は `true` に設定され、行った設定はすべて無視されます。|  
|`authenticationMode`|イニシエーターとレスポンダーの間で使用される SOAP 認証モードを指定します。<br /><br /> 既定値は sspiNegotiated です。<br /><br /> この属性は <xref:System.ServiceModel.Configuration.AuthenticationMode> 型です。|  
|`defaultAlgorithmSuite`|セキュリティ アルゴリズム スイートは、正規化、ダイジェスト、キーラップ、署名、暗号化、およびキー派生の各アルゴリズムなど、さまざまなアルゴリズムを定義します。  各セキュリティ アルゴリズム スイートは、これらのさまざまなパラメーターの値を定義します。  メッセージ ベースのセキュリティは、これらのアルゴリズムを使用して実現されます。<br /><br /> この属性は、既定とは異なるアルゴリズムのセットを選択する別のプラットフォームで操作するときに使用されます。  この設定を修正する場合、関連するアルゴリズムの強さと脆弱性に注意する必要があります。  この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。  既定値は、`Basic256` です。|  
|`includeTimestamp`|各メッセージにタイム スタンプが含まれるかどうかを指定するブール値です。  既定値は、`true` です。|  
|`keyEntropyMode`|メッセージをセキュリティで保護するキーを計算する方法を指定します。  キーは、クライアント キー マテリアルのみ、サービス キー マテリアルのみ、または両方の組み合わせに基づいて生成できます。  次の値を指定できます。<br /><br /> -   ClientEntropy: セッション キーは、クライアントから提供されるキー マテリアルに基づいています。<br />-   ServerEntropy: セッション キーは、サービスから提供されるキー マテリアルに基づいています。<br />-   CombinedEntropy: セッション キーは、クライアントとサービスから提供されるキー マテリアルに基づいています。<br /><br /> 既定値は CombinedEntropy です。<br /><br /> この属性は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 型です。|  
|`messageProtectionOrder`|メッセージ レベルのセキュリティ アルゴリズムをメッセージに適用する順序を設定します。  以下の値が有効です。<br /><br /> -   SignBeforeEncrypt: 最初に署名してから暗号化します。<br />-   SignBeforeEncryptAndEncryptSignature: 署名してから暗号化し、次に署名を暗号化します。<br />-   EncryptBeforeSign: 最初に暗号化してから署名します。<br /><br /> SignBeforeEncryptAndEncryptSignature は、WS\-Security 1.1 による相互証明書を使用する場合の既定値です。  SignBeforeEncrypt は、WS\-Security 1. 0 での既定値です。<br /><br /> この属性は <xref:System.ServiceModel.Security.MessageProtectionOrder> 型です。|  
|`messageSecurityVersion`|使用される WS\-Security のバージョンを設定します。  以下の値が有効です。<br /><br /> -   WSSecurityJan2004<br />-   WSSecurityXXX2005<br /><br /> 既定値は WSSecurityXXX2005 です。  この属性は <xref:System.ServiceModel.MessageSecurityVersion> 型です。|  
|`requireDerivedKeys`|キーを元の証明キーから派生できるかどうかを指定するブール値。  既定値は、`true` です。|  
|`requireSecurityContextCancellation`|セキュリティ コンテキストが不要になったときにそれをキャンセルして終了する必要があるかどうかを指定するブール値。  既定値は、`true` です。|  
|`requireSignatureConfirmation`|WS\-Security 署名確認を有効にするかどうかを指定するブール値です。  `true` に設定されている場合、メッセージ署名が応答側で確認されます。  既定値は、`false` です。<br /><br /> サービスが要求を完全に認識して応答していることを確認するために、署名確認を使用します。|  
|`securityHeaderLayout`|セキュリティ ヘッダーでの要素の順序を指定します。  次の値を指定できます。<br /><br /> -   Strict。  "使用前に宣言する" という一般的な方針に従って、項目がセキュリティ ヘッダーに追加されます。<br />-   Lax。  WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。<br />-   LaxWithTimestampFirst。  WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダーの最初の要素は wsse:Timestamp 要素である必要があります。<br />-   LaxWithTimestampLast。  WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダーの最後の要素は wsse:Timestamp 要素である必要があります。<br /><br /> 既定値は Strict です。<br /><br /> この要素は <xref:System.ServiceModel.Channels.SecurityHeaderLayout> 型です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|現在発行されているトークンを指定します。  この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement> 型です。|  
|[\<localClientSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|このバインディングのローカル クライアントのセキュリティ設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement> 型です。|  
|[\<localServiceSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|このバインディングのローカル サービスのセキュリティ設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|カスタム バインディングのセキュリティ オプションを指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>   
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>   
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [カスタム バインディング セキュリティ](../../../../../docs/framework/wcf/samples/custom-binding-security.md)