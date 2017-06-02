---
title: "&lt;bypassTrustedAppStrongNames&gt; 要素 | Microsoft Docs"
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
  - "<bypassTrustedAppStrongNames> 要素"
  - "bypassTrustedAppStrongNames 要素"
  - "厳密な名前のバイパス機能"
  - "厳密な名前を付けたアセンブリ, 読み込み (信頼されたアプリケーション ドメインへの)"
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &lt;bypassTrustedAppStrongNames&gt; 要素
完全に信頼されている <xref:System.AppDomain> に読み込まれた、完全信頼アセンブリの厳密な名前の検証をバイパスするかどうかを指定します。  
  
## 構文  
  
```  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> 完全信頼アセンブリの厳密な名前の検証を回避するバイパス機能を有効にするかどうかを指定します。  この機能を有効にすると、アセンブリを読み込むときに、厳密な名前が正しいかどうかの検証は行われません。  既定値は、`true` です。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`true`|完全に信頼されている <xref:System.AppDomain> にアセンブリを読み込むとき、完全信頼アセンブリの厳密な名前の署名は検証されません。  これは、既定の設定です。|  
|`false`|完全に信頼されている <xref:System.AppDomain> にアセンブリを読み込むとき、完全信頼アセンブリの厳密な名前の署名が検証されます。  厳密な名前の署名は、署名が正しいかどうかだけが検証されます。別の厳密な名前と一致するかどうかの比較は行われません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 厳密な名前のバイパス機能により、完全信頼アセンブリの厳密な名前の署名の検証によるオーバーヘッドを回避することができます。  
  
 バイパス機能は、厳密な名前を使用して署名されたすべてのアセンブリと、次のような特性を持つすべてのアセンブリに適用されます。  
  
-   <xref:System.Security.Policy.StrongName> 証拠のない \(たとえば、`MyComputer` ゾーンの証拠が付与されている\)、完全に信頼されているアセンブリ  
  
-   完全に信頼されている <xref:System.AppDomain> に読み込まれたアセンブリ  
  
-   <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティで指定された場所から読み込まれたアセンブリ  
  
-   遅延署名されていないアセンブリ  
  
> [!NOTE]
>  レジストリ キーを使用して、コンピューター上のすべてのアプリケーションに対してバイパス機能が無効になっている場合、この構成ファイルの設定は無効です。  詳細については、「[方法 : 厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)」を参照してください。  
  
## 使用例  
 次の例は、完全信頼アセンブリの厳密な名前の署名の検証動作を指定する方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [方法 : 厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)