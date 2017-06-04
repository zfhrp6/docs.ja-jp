---
title: "&lt;httpWebRequest&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<httpWebRequest> 要素"
  - "httpWebRequest 要素"
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# &lt;httpWebRequest&gt; 要素 (ネットワーク設定)
Web 要求パラメーターをカスタマイズします。  
  
## 構文  
  
```  
  
      <httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`maximumResponseHeadersLength`|応答ヘッダーの最大長を KB で指定します。  既定値は 64 です。  \-1 の値は、応答ヘッダーにサイズ制限が設定されていないことを示しています。|  
|`maximumErrorResponseLength`|エラー応答の最大長を KB で指定します。  既定値は 64 です。  \-1 の値は、エラー応答にサイズ制限が設定されていないことを示しています。|  
|`maximumUnauthorizedUploadLength`|未承認エラー コードに応答してアップロードする最大長をバイトで指定します。  既定値は \-1 です。  値 \-1 は、アップロード情報にサイズ制限が適用されないことを示します。|  
|`useUnsafeHeaderParsing`|安全でないヘッダー解析が有効であるかどうかを指定します。  既定値は `false` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## 解説  
 既定では、.NET Framework は URI 解析に対して RFC 2616 を厳密に適用します。  一部のサーバーの応答では、禁止されたフィールドに制御文字が含まれる場合があり、<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> メソッドが <xref:System.Net.WebException> をスローする原因となります。  **useUnsafeHeaderParsing** が **true** に設定されている場合、<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> はスローしませんが、アプリケーションはいくつかのフォームの URI 解析攻撃を受けやすくなります。  最良のソリューションは、応答に制御文字が含まれないように、サーバーを変更することです。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 次のコード例は、通常の最大ヘッダー長より大きい値を指定する方法を示しています。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)