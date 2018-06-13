---
title: '&lt;NetFx40_PInvokeStackResilience&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cfd8c971edd4537de6e073c49f128f86eb8a042
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748998"
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;NetFx40_PInvokeStackResilience&gt;要素
ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージ コードとアンマネージ コード間の遷移が遅くなります。  
  
 \<configuration>  
\<ランタイム >  
< NetFx40_PInvokeStackResilience >  
  
## <a name="syntax"></a>構文  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムは不適切なプラットフォームを検出するかどうかを示す宣言を呼び出すし、スタックを 32 ビット プラットフォーム上で実行時に自動的に修正します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`0`|ランタイムは、高速の相互運用マーシャ リングで導入されたアーキテクチャを使用して、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]が検出されない、および修正プログラムの不適切なプラットフォーム呼び出しの宣言。 既定値です。|  
|`1`|ランタイムは低速の遷移を検出して修正する不適切なプラットフォーム呼び出しの宣言。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 この要素では、高速相互運用マーシャ リング ランタイム回復不適切なプラットフォーム呼び出しの宣言を交換することができます。  
  
 以降で、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]アーキテクチャをマーシャ リングの簡素化された相互運用機能は、マネージ コードからアンマネージ コードへの遷移の大幅なパフォーマンスが向上します。 .NET Framework の以前のバージョンでは、マーシャ リング レイヤーが検出されましたが正しくありませんプラットフォームは、呼び出しの 32 ビット プラットフォーム上で宣言され、スタックを自動的に固定されます。 マーシャ リングの新しいアーキテクチャでは、この手順が排除されます。 この結果、遷移は非常に高速が不適切なプラットフォーム呼び出しの宣言プログラム エラーが発生することができます。  
  
 開発中に正しくない宣言を検出するために簡単に、Visual Studio のデバッグ機能が改善されました。 [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)マネージ デバッグ アシスタント (MDA) は、アタッチされたデバッガーでアプリケーションが実行されているときに、宣言を呼び出す不適切なプラットフォームに通知します。  
  
 コンポーネントを再コンパイルすることはできません、およびことが不適切なプラットフォーム呼び出しの宣言を行うこともできますが、アプリケーションにで使用されているアドレス シナリオを`NetFx40_PInvokeStackResilience`要素。 この要素で、アプリケーション構成ファイルを追加する`enabled="1"`opts 低速の遷移しますが、.NET Framework の以前のバージョンの動作と互換性があるモードにします。 .NET Framework の以前のバージョンに対してコンパイルされたアセンブリでは、この互換モードが自動的に選択されるためし、この要素は必要ありません。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 例を次にマネージ コードに対する不適切な回復を強化を選択するプラットフォーム呼び出しの間の遷移が遅くなりますが、アプリケーションの宣言方法とアンマネージ コードです。  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
