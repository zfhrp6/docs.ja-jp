---
title: "&lt;shadowCopyVerifyByTimestamp&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<shadowCopyTimeStampVerification> 要素"
  - "shadowCopyTimeStampVerification 要素"
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;shadowCopyVerifyByTimestamp&gt; 要素
シャドウ コピーの動作を、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] で導入された既定の起動動作にするか、旧バージョンの .NET Framework の起動動作に戻すかを指定します。  
  
## 構文  
  
```  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> アセンブリをシャドウ コピーする前にそのアセンブリが更新されているかどうかを確認するため、起動時に、シャドウ コピーを使用するアプリケーション ドメインでアセンブリのタイム スタンプを比較するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|true|起動時、シャドウ コピー ディレクトリに前回コピーされたときから更新されているアセンブリのみをコピーします。  これは [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] の既定値です。|  
|false|以前のバージョンの .NET Framework の起動動作に戻します。この場合、起動時にすべてのファイルがコピーされます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降では、アセンブリがシャドウ コピーされるのは、アセンブリがシャドウ コピー ディレクトリに前回コピーされたときから変更されていることがタイム スタンプからわかる場合だけです。  この方法では、シャドウ コピーを使用するアプリケーションの多くで起動時間が速くなります。詳細については、「[アセンブリのシャドウ コピー](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)」を参照してください。  アセンブリが更新される割合や頻度が高いアプリケーションでは、この動作の変更による利点がないこともあります。  この場合、.NET Framework の以前のバージョンの動作を復元するには、この要素を使用します。  
  
## 使用例  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] のシャドウ コピーの既定の起動動作を無効にし、以前のバージョンの .NET Framework の起動動作に戻す方法を、次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリのシャドウ コピー](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)