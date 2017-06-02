---
title: "&lt;relativeBindForResources&gt; 要素 | Microsoft Docs"
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
  - "<relativeBindForResources> 要素"
  - "RelativeBindForResources 要素"
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;relativeBindForResources&gt; 要素
サテライト アセンブリのプローブを最適化します。  
  
## 構文  
  
```vb  
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> 共通言語ランタイムはサテライト アセンブリのプローブを最適化するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ランタイムでは、サテライト アセンブリのプローブを最適化しません。  これが既定値です。|  
|`true`|ランタイムでは、サテライト アセンブリのプローブを最適化します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 一般に、リソース マネージャーは [リソースのパッケージ化と配置](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) のトピックで説明されているように、リソースの場合は、プローブします。  これは、リソース マネージャーがリソースのローカライズ バージョンのプローブと、サテライト アセンブリをアプリケーション コード ベースのカルチャ固有のフォルダーのグローバル アセンブリ キャッシュ、外観、クエリ Window インストーラーを表示することもできます。<xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを発生させることを意味します。  `<relativeBindForResources>` 要素は、リソース マネージャーによってサテライト アセンブリのプローブ方法を最適化します。  これは、次の状況下でリソースのプローブとパフォーマンスが向上する場合:  
  
-   サテライト アセンブリがコード アセンブリと同じ場所に配置されます。  つまり、コードのアセンブリがグローバル アセンブリ キャッシュにインストールされている場合、サテライト アセンブリは、そこにインストールする必要があります。  コードのアセンブリがアプリケーション コード ベースにインストールされている場合、サテライト アセンブリは、コード ベースのカルチャ固有のフォルダーにインストールする必要があります。  
  
-   Windows インストーラーでのサテライト アセンブリのオンデマンド インストールにほとんど使用されず、使用しない場合。  
  
-   アプリケーション コードが <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを処理しない場合。  
  
 `true` へ `<relativeBindForResources>` 要素の `enabled` 属性を設定すると、次のようにサテライト アセンブリのリソース マネージャーのプローブを最適化します:  
  
-   これはサテライト アセンブリのプローブに親コード アセンブリの場所が使用されます。  
  
-   これはサテライト アセンブリのクエリ Window インストーラー。  
  
-   これは <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを発生させません。  
  
## 参照  
 [リソースのパッケージ化と配置](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)