---
title: '&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;要素
PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。  
  
 \<configuration>  
\<ランタイム >  
\<forcePerformanceCounterUniqueSharedMemoryReads >  
  
## <a name="syntax"></a>構文  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> PerfCounter.dll がカテゴリ別の共有メモリまたは使用するグローバル メモリからパフォーマンス カウンター データを読み込むかどうかを決定する CategoryOptions レジストリ設定を使用するかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|PerfCounter.dll が、CategoryOptions を使用しないレジストリ設定ではこれが既定値です。|  
|`true`|PerfCounter.dll は CategoryOptions レジストリ設定を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 前に .NET Framework のバージョンでは、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、読み込まれた PerfCounter.dll のバージョンが、プロセスに読み込まれたランタイムに対応します。 コンピューターが両方の .NET Framework version 1.1 を持っているかどうか、[!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)]インストールされている、.NET Framework 1.1 アプリケーションは PerfCounter.dll の .NET Framework 1.1 バージョンを読み込むとします。 以降で、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]PerfCounter.dll の最新のインストールされているバージョンが読み込まれます。 つまり、.NET Framework 1.1 アプリケーションが読み込むこと、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]バージョン PerfCounter.dll の場合、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]コンピューターにインストールします。  
  
 以降で、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]PerfCounter.dll がカテゴリ別の共有メモリまたはグローバル共有メモリから読み取る必要があります、かどうかを確認するには、各プロバイダーの CategoryOptions レジストリ エントリをチェックするパフォーマンス カウンターを使用するときにします。 .NET Framework 1.1 PerfCounter.dll 読み取れないレジストリのエントリがカテゴリ別の共有メモリです。 認識されません。これは、常に、グローバル共有メモリから読み取ります。  
  
 旧バージョンとの互換性のため、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] .NET Framework 1.1 アプリケーションで実行されるときに PerfCounter.dll が CategoryOptions レジストリ エントリを確認しません。 .NET Framework 1.1 PerfCounter.dll と同じように、グローバル共有メモリは単に使用します。 ただし、指示することで、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]を有効にすると、レジストリ設定を確認する PerfCounter.dll、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素。  
  
> [!NOTE]
>  有効にすると、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素とは限りませんが、カテゴリ別の共有メモリが使用されます。 設定が有効な`true`CategoryOptions レジストリ設定を参照する PerfCounter.dll でのみ発生します。 CategoryOptions の既定の設定がカテゴリ別の共有メモリを使用するにはただし、グローバル共有メモリを使用することを示すために CategoryOptions を変更できます。  
  
 CategoryOptions 設定を格納するレジストリ キーは hkey_local_machine \system\currentcontrolset\services\\< categoryName\>\Performance です。 既定では、CategoryOptions は 3 に設定、PerfCounter.dll に指示するカテゴリに固有の共有メモリを使用します。 CategoryOptions が 0 に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。 作成中のインスタンスの名前が再利用されるインスタンスと同一である場合にのみ、インスタンス データを再利用されます。 すべてのバージョンは、カテゴリに書き込むことができます。 CategoryOptions が 1 に設定されている場合、グローバル共有メモリを使用するが、カテゴリ名が再利用される、カテゴリと同じ長さである場合は、インスタンス データを再利用されることができます。  
  
 0 と 1 の設定は、メモリ リークとパフォーマンス カウンターのメモリの不足する可能性があります。  
  
## <a name="example"></a>例  
 次の例では、PerfCounter.dll がカテゴリ別の共有メモリを使用する必要があるかどうかを決定する CategoryOptions レジストリ エントリを参照することを指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
