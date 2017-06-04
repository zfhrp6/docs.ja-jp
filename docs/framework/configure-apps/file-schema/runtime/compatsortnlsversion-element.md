---
title: "&lt;CompatSortNLSVersion&gt; 要素 | Microsoft Docs"
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
  - "<CompatSortNLSVersion> 要素"
  - "CompatSortNLSVersion 要素"
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;CompatSortNLSVersion&gt; 要素
文字列比較の実行時に、ランタイムがレガシ並べ替え順序を使用するように指定します。  
  
## 構文  
  
```  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`enabled`|必須の属性です。<br /><br /> 並べ替え順序が使用されるロケール ID を指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|4096|代替の並べ替え順序を表すロケール ID。  この場合、4096 は、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] およびそれ以前のバージョンの並べ替え順序を表します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] で <xref:System.Globalization.CompareInfo?displayProperty=fullName> クラスによって実行される文字列の比較、並べ替え、および大文字と小文字の区別の処理は、Unicode 5.1 規格に準拠しているため、<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=fullName> や <xref:System.String.LastIndexOf%28System.String%29?displayProperty=fullName> などの文字列比較メソッドの結果は、以前のバージョンの .NET Framework とは異なる場合があります。  アプリケーションがレガシ動作に依存している場合は、`<CompatSortNLSVersion>` 要素をアプリケーションの構成ファイルに含めることで、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] およびそれ以前のバージョンで使用されていた文字列の比較および並べ替えの規則を復元できます。  
  
> [!IMPORTANT]
>  文字列の比較および並べ替えのレガシ規則を復元する場合は、ローカル システムで sort00001000.dll ダイナミック リンク ライブラリも使用できるようにする必要があります。  
  
 アプリケーション ドメインを作成するときに、文字列 "NetFx40\_Legacy20SortingBehavior" を <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> メソッドに渡すことで、文字列の比較および並べ替えのレガシ規則を特定のアプリケーション ドメインで使用することもできます。  
  
## 使用例  
 次の例では、2 つの <xref:System.String> オブジェクトをインスタンス化して、<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=fullName> メソッドを呼び出し、現在のカルチャの規則を使用してそれらのオブジェクトを比較する方法を示します。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] で例を実行すると、次のように出力されます。  
  
```  
sta follows a in the sort order.  
```  
  
 これは、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] で例を実行したときに表示される出力とはまったく異なります。  
  
```  
sta equals a in the sort order.  
```  
  
 ただし、例のディレクトリに次の構成ファイルを追加し、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] で例を実行すると、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] で例を実行した場合と同じ出力が生成されます。  
  
```  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)