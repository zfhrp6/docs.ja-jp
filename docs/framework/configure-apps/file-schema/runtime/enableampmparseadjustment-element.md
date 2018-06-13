---
title: '&lt;EnableAmPmParseAdjustment&gt;要素'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17f521be31fa4082d9418c7dad734e37994bbb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752820"
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt;要素
日時解析メソッドが 1 日、月、1 時間、および AM/PM 指定子を含む日付文字列を解析するルールの調整済みセットを使用するかどうかを判断します。  
  
 \<configuration>  
 \<ランタイム >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>構文  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 日時解析メソッドで、日、月、1 時間、および AM/PM 指定子のみを含む日付文字列を解析する調整済みの一連の規則を使用するかどうかを指定します。|  
  
### <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|日時解析メソッドを日、月、1 時間、および AM/PM 指定子のみを含む日付文字列を解析するため調整済みの規則の情報を使用しません。|  
|1|日時解析メソッドは、調整済みの規則を使用して、日、月、1 時間、および AM/PM 指定子のみを含む日付文字列を解析するためです。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 `<EnableAmPmParseAdjustment>`要素は、次の方法で数値 1 日と月の後に、1 時間と、AM/PM 指定子 (「4/10 6 AM」) などを含む日付文字列を解析する方法を制御します。  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 その他のパターンが影響を受けません。  
  
 `<EnableAmPmParseAdjustment>`要素も何も起こりません、 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>、 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>、および<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>メソッドです。  
  
> [!IMPORTANT]
>  .NET Core と .NET ネイティブでは、調整済みの午前/午後解析規則は既定で有効にします。  
  
 解析の調整規則が有効でない場合は、文字列の最初の桁は 12 時間形式の時間として解釈されます、AM/PM 指定子を除く文字列の残りの部分は無視されます。 日付と時刻の解析を行ってメソッドによって返されるは、現在の日付と日付の文字列から抽出された、1 日の時間で構成されます。  
  
 解析の調整規則が有効になっている場合は 解析方法として、現在の年に属する月と日を解釈し、時刻を 12 時間形式の時間を解釈します。  
  
 違いを次の表に示します、<xref:System.DateTime>ときの値、<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>メソッドは文字列の解析に使用される"「4/10 6 AM」、`<EnableAmPmParseAdjustment>`要素の`enabled`プロパティが「0」または「1」に設定します。 今日の日付が 2017 年 1 月 5 日があり、特定のカルチャの"G"書式指定文字列でフォーマットされているかのように日付を表示ことが前提とします。  
  
|カルチャ名|有効になっている =「0」|有効になっている「1」を =|  
|------------------|------------------|------------------|  
|en-US|2017 5/1/4時 00分: 00 AM|4/10/2017 年 6時 00分: 00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>関連項目  
 [\<ランタイム > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
