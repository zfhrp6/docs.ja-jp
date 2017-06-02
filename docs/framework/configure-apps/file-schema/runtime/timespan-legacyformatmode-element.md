---
title: "&lt;TimeSpan_LegacyFormatMode&gt; 要素 | Microsoft Docs"
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
  - "<TimeSpan_LegacyFormatMode> 要素"
  - "TimeSpan_LegacyFormatMode 要素"
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;TimeSpan_LegacyFormatMode&gt; 要素
<xref:System.TimeSpan?displayProperty=fullName> 値による書式設定操作のレガシ動作をランタイムで維持するかどうかを決定します。  
  
## 構文  
  
```  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> <xref:System.TimeSpan?displayProperty=fullName> 値による書式設定のレガシ動作をランタイムで使用するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|書式設定のレガシ動作はランタイムで復元されません。|  
|`true`|書式設定のレガシ動作がランタイムで復元されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降の <xref:System.TimeSpan?displayProperty=fullName> 構造体は、<xref:System.IFormattable> インターフェイスを実装し、標準およびカスタム書式指定文字列を使用した書式設定操作をサポートするようになっています。  解析メソッドでサポート対象外の書式指定子または書式指定文字列が検出されると、<xref:System.FormatException> がスローされます。  
  
 以前のバージョンの .NET Framework では、<xref:System.TimeSpan> 構造体は、<xref:System.IFormattable> を実装せず、書式指定文字列をサポートしていませんでした。  ただし、開発者の多くは、<xref:System.TimeSpan> が一連の書式指定文字列をサポートしていると誤って認識し、<xref:System.String.Format%2A?displayProperty=fullName> などのメソッドでの[複合書式指定の操作](../../../../../docs/standard/base-types/composite-formatting.md)に書式指定文字列を使用していました。  通常、型が <xref:System.IFormattable> を実装し、書式指定文字列をサポートしている場合、サポート対象外の書式指定文字列を使用して書式指定メソッドを呼び出すと、<xref:System.FormatException> がスローされます。  ただし、<xref:System.TimeSpan> は <xref:System.IFormattable> を実装しなかったため、ランタイムでは書式指定文字列が無視され、代わりに <xref:System.TimeSpan.ToString?displayProperty=fullName> メソッドが呼び出されていました。  つまり、書式設定操作で書式指定文字列を使用しても効果はありませんでしたが、<xref:System.FormatException> も発生しませんでした。  
  
 レガシ コードによって複合書式指定メソッドと無効な書式指定文字列が渡され、そのコードを再コンパイルできない場合、`<TimeSpan_LegacyFormatMode>` 要素を使用して <xref:System.TimeSpan> のレガシ動作を復元できます。  この要素の `enabled` 属性を `true` に設定すると、複合書式指定メソッドにより <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName> ではなく、<xref:System.TimeSpan.ToString?displayProperty=fullName> が呼び出され、<xref:System.FormatException> はスローされません。  
  
## 使用例  
 次の例では、<xref:System.TimeSpan> オブジェクトをインスタンス化し、サポート対象外の標準書式指定文字列を使用して <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=fullName> メソッドでそのインスタンスの書式設定を試みています。  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] またはそれ以前のバージョンで例を実行すると、次のように出力されます。  
  
```  
12:30:45  
```  
  
 これは、出力と [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降のバージョンの例を実行すると大きく異なる:  
  
```  
Invalid Format  
```  
  
 ただし、例のディレクトリに次の構成ファイルを追加し、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降のバージョンの例を実行すると、出力は [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]で例を実行したで生成されたデータと同じです。  
  
```  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)