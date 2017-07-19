---
title: "&lt;NetFx40_LegacySecurityPolicy&gt; 要素 | Microsoft Docs"
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
  - "<NetFx40_LegacySecurityPolicy> 要素"
  - "NetFx40_LegacySecurityPolicy 要素"
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;NetFx40_LegacySecurityPolicy&gt; 要素
ランタイムがレガシ コード アクセス セキュリティ \(CAS: Code Access Security\) ポリシーを使用するかどうかを指定します。  
  
## 構文  
  
```  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがレガシ CAS ポリシーを使用するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ランタイムはレガシ CAS ポリシーを使用しません。  これは、既定の設定です。|  
|`true`|ランタイムはレガシ CAS ポリシーを使用します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 .NET Framework Version 3.5 以前のバージョンでは、CAS ポリシーが常に有効になります。  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] では、CAS ポリシーを明示的に有効にする必要があります。  
  
 CAS ポリシーはバージョンに固有です。  旧バージョンの .NET Framework に存在するカスタム CAS ポリシーは、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] では再度指定する必要があります。  
  
 `<NetFx40_LegacySecurityPolicy>` 要素を [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] アセンブリに適用しても、[透過的セキュリティ コード](../../../../../docs/framework/misc/security-transparent-code.md)には影響しません。透過性規則は引き続き適用されます。  
  
> [!IMPORTANT]
>  `<NetFx40_LegacySecurityPolicy>` 要素を適用すると、[グローバル アセンブリ キャッシュ](../../../../../docs/framework/app-domains/gac.md)にインストールされていない、[ネイティブ イメージ ジェネレーター \(Ngen.exe\)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) で作成されたネイティブ イメージのアセンブリでパフォーマンスが大幅に低下する可能性があります。  このパフォーマンスの低下が発生するのは、属性が適用されたときに、ランタイムがアセンブリをネイティブ イメージとして読み込むことができず、結果的に Just\-In\-Time アセンブリとして読み込まれるためです。  
  
> [!NOTE]
>  Visual Studio プロジェクトのプロジェクト設定で、対象となる .NET Framework のバージョンとして、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] より前のバージョンを指定する場合は、そのバージョン用に指定したすべてのカスタム CAS ポリシーを含む CAS ポリシーが有効になります。  ただし、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] の新しい型およびメンバーは使用できません。  また [アプリケーション構成ファイル](../../../../../docs/framework/configure-apps/index.md)でスタートアップ設定スキーマの [\<supportedRuntime\> 要素](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) を使用して .NET Framework の旧バージョンを指定できます。  
  
> [!NOTE]
>  構成ファイルの構文では、大文字と小文字が区別されます。  構文と例の各セクションで提供されている構文を使用する必要があります。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## 使用例  
 アプリケーションのレガシ CAS ポリシーを有効にする方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)