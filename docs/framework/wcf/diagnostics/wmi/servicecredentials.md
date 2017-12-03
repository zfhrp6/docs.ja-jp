---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceCredentials クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 ServiceCredentials クラスには、次のプロパティがあります。  
  
### <a name="clientcertificate"></a>ClientCertificate  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのための、クライアント証明認証および提供設定です。  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのための、現在発行されているトークンの認証設定です。  
  
### <a name="peer"></a>Peer  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 現在のセキュリティで保護された通信の設定を指定します。  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスに関連付けられている証明書です。  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのユーザー名/パスワードの設定です。  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスの Windows 認証の設定です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceCredentials>
