---
title: '&lt;TimeSpan_LegacyFormatMode&gt;要素'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0faf2876680ef5ec3fc7373cae9f81eb091f47a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753971"
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;TimeSpan_LegacyFormatMode&gt;要素
ランタイムが書式設定の操作での従来の動作を保持するかどうかを判断<xref:System.TimeSpan?displayProperty=nameWithType>値。  
  
 \<configuration>  
\<ランタイム >  
< TimeSpan_LegacyFormatMode >  
  
## <a name="syntax"></a>構文  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムと従来の書式設定動作を使用しているかどうかを示す<xref:System.TimeSpan?displayProperty=nameWithType>値。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムは、従来の書式設定動作を復元できません。|  
|`true`|ランタイムは、従来の書式設定動作を復元します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 <xref:System.TimeSpan?displayProperty=nameWithType> implements 構造体、<xref:System.IFormattable>インターフェイスと書式設定の標準およびカスタムの書式指定文字列の操作をサポートしています。 解析方法には、サポートされていない書式指定子または書式指定文字列が検出されると、スロー、<xref:System.FormatException>です。  
  
 .NET Framework の以前のバージョンで、<xref:System.TimeSpan>構造体が実装されていない<xref:System.IFormattable>し、書式指定文字列をサポートしていませんでした。 ただし、多くの開発者誤ってと想定<xref:System.TimeSpan>書式指定文字列のセットをサポートして、使用される[複合書式指定操作](../../../../../docs/standard/base-types/composite-formatting.md)などのメソッドと<xref:System.String.Format%2A?displayProperty=nameWithType>です。 通常は、型が実装する場合<xref:System.IFormattable>書式指定文字列、文字列が通常スローをサポートされていない形式で書式指定メソッドの呼び出しをサポートしていると、<xref:System.FormatException>です。 ただし、ため<xref:System.TimeSpan>実装されていない<xref:System.IFormattable>、ランタイムは、書式指定文字列は無視され、代わりに呼び出されます、<xref:System.TimeSpan.ToString?displayProperty=nameWithType>メソッドです。 これには、書式指定文字列に書式設定操作には影響はありません、その存在しなかったになることを意味する<xref:System.FormatException>です。  
  
 場合はレガシ コードが、複合書式指定メソッドと、無効な形式の文字列を渡すし、そのコードを再コンパイルすることはできませんが、使用することができます、`<TimeSpan_LegacyFormatMode>`要素、従来の復元を<xref:System.TimeSpan>動作します。 設定すると、`enabled`にするには、この要素の属性`true`、複合書式指定メソッドの結果への呼び出しで<xref:System.TimeSpan.ToString?displayProperty=nameWithType>なく<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>、および<xref:System.FormatException>はスローされません。  
  
## <a name="example"></a>例  
 次の例のインスタンスを作成、<xref:System.TimeSpan>オブジェクトを使用して書式試みます、<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>メソッドでサポートされていない標準書式指定文字列を使用します。  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 例を実行すると、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]または以前のバージョンで、次の出力を表示します。  
  
```  
12:30:45  
```  
  
 これとは異なります著しく出力例を実行する場合、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降のバージョン。  
  
```  
Invalid Format  
```  
  
 ただしの例を次の構成ファイルを追加する場合のディレクトリで例を実行し、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降のバージョンが、出力は、例は、実行時に生成されるものと同じまたは[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]です。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
