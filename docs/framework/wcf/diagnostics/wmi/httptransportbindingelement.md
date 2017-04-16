---
title: "HttpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HttpTransportBindingElement
HttpTransportBindingElement  
  
## 構文  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## メソッド  
 HttpTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 HttpTransportBindingElement クラスには、次のプロパティがあります。  
  
### AllowCookies  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。  
  
### AuthenticationScheme  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP リスナーにより処理されているクライアント要求の認証に使用する認証方式です。  
  
### BypassProxyOnLocal  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 プロキシをローカル アドレスで無視するかどうかを示す値です。  
  
### HostNameComparisonMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。  
  
### KeepAliveEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 有効な場合は、HTTP 接続がアクティビティ レベルとは無関係に維持されます。  
  
### MaxBufferSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 バッファー プールの最大サイズ。  
  
### ProxyAddress  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP 要求に使用するプロキシのアドレスを格納する URI です。  
  
### ProxyAuthenticationScheme  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP プロキシにより処理されているクライアント要求の認証に使用する認証方式です。  
  
### Realm  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 認証レルム。  
  
### TransferMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージが要求や応答をバッファーするか、ストリーミングするかを指定する値です。  
  
### UnsafeConnectionNtlmAuthentication  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 サーバー上で安全ではない接続共有を有効にするかどうかを示す値です。  
  
### UseDefaultWebProxy  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを示す値です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>