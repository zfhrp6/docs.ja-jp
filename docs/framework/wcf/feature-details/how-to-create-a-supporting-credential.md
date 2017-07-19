---
title: "方法 : サポート資格情報を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 方法 : サポート資格情報を作成する
カスタムのセキュリティ スキームでは、複数の資格情報が必要になることがあります。  たとえば、サービスが、ユーザー名とパスワードだけでなく、クライアントが 18 歳以上であることを証明する資格情報もクライアントに要求することがあります。  この 2 番目の資格情報を*サポート資格情報*と呼びます。  ここでは、このような資格情報を [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントで実装する方法について説明します。  
  
> [!NOTE]
>  サポート資格情報の仕様は、WS\-SecurityPolicy 仕様の一部です。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 「[Web サービスのセキュリティ仕様](http://go.microsoft.com/fwlink/?LinkId=88537)」を参照してください。  
  
## トークンのサポート  
 簡単に説明すると、メッセージ セキュリティを使用した場合は、常に*プライマリ資格情報* \(たとえば、X.509 証明書、Kerberos チケット\) によってメッセージがセキュリティで保護されます。  
  
 仕様で定義されているとおり、セキュリティ バインディングは、*トークン*を使用してメッセージ交換をセキュリティで保護します。  *トークン*は、セキュリティ資格情報を表したものです。  
  
 セキュリティ バインディングは、セキュリティ バインディング ポリシーで特定されたプライマリ トークンを使用して、署名を作成します。  この署名を*メッセージ署名*と呼びます。  
  
 メッセージ署名に関連付けられたトークンによって提供されるクレームを増やすために、追加のトークンを指定できます。  
  
## 保証、署名、および暗号化  
 サポート資格情報は、メッセージ内部で送信された*サポート トークン*になります。  WS\-SecurityPolicy 仕様では、次の表に示すように、サポート トークンをメッセージに追加する方法が 4 つ定義されています。  
  
|目的|説明|  
|--------|--------|  
|符号付き|サポート トークンはセキュリティ ヘッダーに追加され、メッセージ署名によって署名されます。|  
|保証|*保証トークン*は、メッセージ署名を行います。|  
|署名および保証|署名付き保証トークンは、メッセージ署名から生成された `ds:Signature` 要素全体を署名し、それ自体がこのメッセージ署名によって署名されます。つまり、両方のトークン \(メッセージ署名に使用されるトークンと署名付き保証トークン\) がお互いに署名します。|  
|署名および暗号化|暗号化された署名付きサポート トークンは、`wsse:SecurityHeader` に表示されたときに暗号化されている署名付きサポート トークンです。|  
  
## サポート資格情報のプログラミング  
 サポート トークンを使用するサービスを作成するには、[\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を作成する必要があります   \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).\)  
  
 カスタム バインディングを作成する最初の手順は、次の 3 種類のいずれかのセキュリティ バインディング要素を作成することです。  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 すべてのクラスは、次の 4 つの関連プロパティを備えた <xref:System.ServiceModel.Channels.SecurityBindingElement> から継承します。  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### スコープ  
 サポート資格情報には、次の 2 つのスコープがあります。  
  
-   *エンドポイント サポート トークン*は、エンドポイントのすべての操作をサポートします。  つまり、サポート トークンによって表される資格情報は、エンドポイントの任意の操作が呼び出されたときにいつでも使用できます。  
  
-   *操作サポート トークン*は、エンドポイントの特定の操作だけをサポートします。  
  
 プロパティ名に示されているように、サポート資格情報は必須またはオプションのどちらかになることができます。  つまり、サポート資格情報は必須ではありませんが、存在する場合は使用され、存在しない場合も認証は失敗しません。  
  
## 手順  
  
#### サポート資格情報を備えたカスタム バインディングを作成するには  
  
1.  セキュリティ バインド要素を作成します。  次の例では、`UserNameForCertificate` 認証モードで <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> を作成します。  <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> メソッドを使用します。  
  
2.  サポート パラメーターを対応するプロパティ \(`Endorsing`、`Signed`、`SignedEncrypted`、または `SignedEndorsed`\) によって返される型のコレクションに追加します。  <xref:System.ServiceModel.Security.Tokens> 名前空間に存在する型には、<xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> など、一般的に使用される型があります。  
  
## 例  
  
### 説明  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを作成し、<xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> クラスのインスタンスを、Endorsing プロパティによって返されるコレクションに追加する例を次に示します。  
  
### コード  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## 参照  
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)