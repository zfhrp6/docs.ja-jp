---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e21377b28adb7668108064b770c2c5e0f9fee8f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;要素
ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
< NetFx45_CultureAwareComparerGetHashCode_LongStrings >  
  
## <a name="syntax"></a>構文  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ハッシュ コードを計算するときに、共通言語ランタイムが固定メモリを割り当てるかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当ててハッシュ コードを計算します。 既定値です。|  
|1|共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに固定メモリを割り当ててハッシュ コードを計算します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 既定では、共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当て、メソッドが非常に長い文字列 (数メガバイト以上) のハッシュ コードを計算しようとすると <xref:System.ArgumentException> 例外がスローされることがあります。 この要素をアプリケーション構成ファイルに追加し、`enabled` 属性を 1 に設定すると、<xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドでハッシュ コードの計算時に固定メモリを割り当てる別のアルゴリズムを使用することを指定できます。  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` 要素は [!INCLUDE[win8](../../../../../includes/win8-md.md)] 以降のバージョンでは使用されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
