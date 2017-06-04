---
title: "&lt;appDomainManagerType&gt; 要素 | Microsoft Docs"
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
  - "<appDomainManagerType> 要素"
  - "appDomainManagerType 要素"
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;appDomainManagerType&gt; 要素
既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして機能する型を指定します。  
  
## 構文  
  
```  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`value`|必須の属性です。  プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして機能する型の名前を、名前空間を含めて指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 アプリケーション ドメイン マネージャーの型を指定するには、この要素と [\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) 要素の両方を指定する必要があります。  これらの要素のどちらかが指定されていない場合、もう一方の要素は無視されます。  
  
 既定のアプリケーション ドメインが読み込まれるとき、<xref:System.TypeLoadException> は指定された型が [\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) 要素で指定されたアセンブリにあるスローされます; とプロセスは起動しません。  
  
 既定のアプリケーション ドメインに対するアプリケーション ドメイン マネージャーの型を指定すると、既定のアプリケーション ドメインから作成される他のアプリケーション ドメインにも、そのアプリケーション ドメイン マネージャーの型が継承されます。  新しいアプリケーション ドメインに対して別のアプリケーション ドメイン マネージャーの型を指定するには、<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName> プロパティと <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName> プロパティを使用します。  
  
 アプリケーション ドメイン マネージャーの型を指定する場合は、アプリケーションに完全信頼が必要です \(たとえば、デスクトップ上で実行されるアプリケーションは完全に信頼されています\)。アプリケーションに完全信頼がない場合は、<xref:System.TypeLoadException> がスローされます。  
  
 型と名前空間の形式は、<xref:System.Type.FullName%2A?displayProperty=fullName> プロパティで使用される形式と同じです。  
  
 この構成要素は、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降でのみ使用できます。  
  
## 使用例  
 次の例は、プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーとして、`AdMgrExample` アセンブリ内の `MyMgr` 型を指定する方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName>   
 [\<appDomainManagerAssembly\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [SetAppDomainManagerType メソッド](../Topic/ICLRControl::SetAppDomainManagerType%20Method.md)