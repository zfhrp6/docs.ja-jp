---
title: '&lt;applicationPool&gt;要素 (Web 設定)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2eafc6b5ad1446fd07518f877a8ec001ad8dbd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt;要素 (Web 設定)
ASP.NET アプリケーションが統合モードで実行されているときに、プロセス全体の動作を管理する ASP.NET によって使用される構成設定を指定[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以降のバージョン。  
  
> [!IMPORTANT]
>  ASP.NET アプリケーションがホストされている場合のみ機能サポートこの要素と機能[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]またはそれ以降のバージョン。  
  
 \<configuration>  
\<system.web > 要素 (Web 設定)  
\<applicationPool > 要素 (Web 設定)  
  
## <a name="syntax"></a>構文  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|ASP.NET では、CPU ごとの同時要求の数を指定します。|  
|`maxConcurrentThreadsPerCPU`|アプリケーション プールの cpu ごと実行できる同時スレッドの数を指定します。 これにより、CPU ごとの要求を処理するために使用するマネージ スレッドの数を制限するため、ASP.NET の同時実行を制御する別の方法です。 既定では、この設定は、0 で、エントリの CLR スレッド プールでは、作成できるスレッドの数も制限されていますが、ASP.NET は CPU ごとに作成できるスレッドの数が制限されませんは。|  
|`requestQueueLimit`|1 つのプロセスで ASP.NET のキューにすることが要求の最大数を指定します。 2 つまたは複数の ASP.NET アプリケーションは、単一のアプリケーション プールで実行すると、アプリケーション プール内の任意のアプリケーションへの要求の累積的なセットは、この設定の対象です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET がホスト アプリケーションと対話する方法についてを説明します。|  
  
## <a name="remarks"></a>コメント  
 実行すると[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]統合モードで以降のバージョンがこの要素を組み合わせて、アプリケーションが IIS アプリケーション プールでホストされている場合に、ASP.NET がスレッドとキューの要求を管理する方法を設定できますか。 IIS 6 を実行するかを実行する[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]クラシック モードで、または ISAPI モードには、これらの設定は無視されます。  
  
 `applicationPool`設定は、.NET Framework の特定のバージョンで実行されるすべてのアプリケーション プールに適用します。 Aspnet.config ファイルでは、設定が含まれています。 バージョン 2.0 および .NET framework 4.0 には、このファイルのバージョンがあります。 (バージョン 3.0 および 3.5、.NET Framework のファイルを共有 aspnet.config バージョン 2.0。)  
  
> [!IMPORTANT]
>  実行する場合[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]で[!INCLUDE[win7](../../../../../includes/win7-md.md)]、すべてのアプリケーション プールの個別の aspnet.config ファイルを構成することができます。 これにより、各アプリケーション プールのスレッドのパフォーマンスを調整できます。  
  
 `maxConcurrentRequestsPerCPU`設定、「5000」の既定の設定、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]が実際には、CPU ごとの 5000 以上の要求がない限り、要求の調整をオフに効果的が ASP.NET によって制御されます。 既定の設定は、CPU あたりの同時実行を自動的に管理する CLR のスレッド プールの代わりに依存します。 広く利用非同期要求の処理、またはネットワーク I/O でブロックされている多くの実行時間の長い要求のあるアプリケーションにメリットが増加した既定の制限を[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]です。 設定`maxConcurrentRequestsPerCPU`ASP.NET 要求を処理するマネージ スレッドの使用を解除します。 0 にします。 IIS アプリケーション プールでアプリケーションを実行すると、要求が IIS I/O のスレッドで維持され、IIS のスレッドの設定によって同時実行を調整するため。  
  
 `requestQueueLimit`設定と同じように機能、`requestQueueLimit`の属性、 [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d)要素は、ASP.NET アプリケーションの Web.config ファイルに設定します。 ただし、 `requestQueueLimit` aspnet.config ファイルで設定よりも優先、 `requestQueueLimit` Web.config ファイルで設定します。 つまり、両方の属性が設定されている場合 (既定では、これが true)、 `requestQueueLimit` aspnet.config ファイルで設定が優先されます。  
  
## <a name="example"></a>例  
 次の例では、次のような状況で aspnet.config ファイルで ASP.NET プロセス全体の動作を構成する方法を示します。  
  
-   アプリケーションがホストされている、[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]アプリケーション プール。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 統合モードで実行されています。  
  
-   アプリケーションを使用して、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]以降のバージョン。  
  
 値の例では、既定値です。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>関連項目  
 [\<system.web> 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
