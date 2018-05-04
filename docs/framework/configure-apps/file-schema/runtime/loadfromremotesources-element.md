---
title: '&lt;loadFromRemoteSources&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d442f71a0e2fc7deacd9aaa02cfba7b66f2349
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt;要素
リモート ソースからのアセンブリに対して、完全な信頼を付与するかどうかを指定します。  
  
> [!NOTE]
>  場合は、Visual Studio プロジェクトのエラー一覧またはビルド エラーのエラー メッセージのため、このトピックにダイレクトされたを参照してください。[する方法: Visual Studio で Web からアセンブリを使用して](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070)です。  
  
 \<configuration>  
\<ランタイム >  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>構文  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> リモート ソースから読み込まれたアセンブリに対して、完全な信頼を付与する必要があるかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|リモート ソースからアプリケーションに完全な信頼を付与しないでください。 既定値です。|  
|`true`|リモート ソースからアプリケーションへの完全な信頼を付与します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework バージョン 3.5 以前のバージョンで、リモートの場所からアセンブリが読み込まれている場合、アセンブリが実行が読み込まれたゾーンに依存していた許可セットでは部分的に信頼されます。 たとえば、web サイトからアセンブリが読み込まれている場合は、インターネット ゾーンに読み込まれましたし、インターネット アクセス許可セットを許可します。 つまり、プロセスは、インターネットのサンド ボックス内で実行されます。 そのアセンブリを実行しようとする場合、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]と以降のバージョンでは、例外がスローされます; する必要がありますか、明示的にサンド ボックスの作成、アセンブリの (を参照してください[する方法: 実行部分信頼コードをサンド ボックスで](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))、または完全な信頼で実行します。  
  
 `<loadFromRemoteSources>`で信頼されている、.NET Framework の以前のバージョンで部分的に信頼されたを実行するアセンブリが完全に実行されることを指定した要素により、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]以降のバージョン。 既定では、リモート アセンブリに機能しません、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]およびそれ以降。 リモートのアセンブリを実行するか、完全信頼として実行か作成してください、サンド ボックス化された<xref:System.AppDomain>これを実行します。  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]、ローカル ネットワーク共有上のアセンブリは、既定で完全な信頼として実行される; を有効にする必要はありません、`<loadFromRemoteSources>`要素。  
  
> [!NOTE]
>  アプリケーションが web サイトからコピーされた場合としてマークされている Windows で web アプリケーションでは、ローカル コンピューター上にある場合でもです。 その指定を変更するには、ファイルのプロパティを変更することで、または使用することができます、`<loadFromRemoteSources>`要素をアセンブリを付与する完全な信頼。 代わりに、使用することができます、<xref:System.Reflection.Assembly.UnsafeLoadFrom%2A>オペレーティング システムは、web から読み込まれたものとしてフラグが設定をローカル アセンブリを読み込みます。  
  
 `enabled`はコード アクセス セキュリティ (CAS) が無効になっている場合にのみ、この要素の属性です。 既定では、CAS ポリシーが無効になって、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]以降のバージョン。 設定した場合`enabled`に`true`、リモート アプリケーションには、完全信頼が与えられます。  
  
 場合`<loadFromRemoteSources>``enabled`に設定されていない`true`、次の条件下で、例外がスローされます。  
  
-   現在のドメインのサンド ボックス化動作の動作とは異なります、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]です。 これには、無効になり、CAS ポリシーとセキュリティで保護されたしないで現在のドメインが必要です。  
  
-   読み込まれるアセンブリではない、`MyComputer`ゾーンです。  
  
> [!NOTE]
>  取得することがあります、 <xref:System.IO.FileLoadException> Windows Virtual PC アプリケーションで、ホスト コンピュータ上のリンク フォルダーからファイルをロードしようとするとします。 このエラーは、経由でリンクされているフォルダーからファイルをロードしようとしたときにも発生する可能性があります[リモート デスクトップ サービス](http://go.microsoft.com/fwlink/?LinkId=182775)(ターミナル サービス)。 例外を避けるためには、次のように設定します。`enabled`に`true`です。  
  
 設定、`<loadFromRemoteSources>`要素を`true`により、この例外はスローされません。 これにより、ことをせず、サンド ボックスに、共通言語ランタイムのセキュリティを読み込まれたアセンブリを指定して、として実行を許可することができます完全な信頼。  
  
> [!IMPORTANT]
>  アセンブリが完全信頼で実行する必要がありますされない場合は、この構成要素を設定しないでください。 代わりに、作成、セキュリティで保護された<xref:System.AppDomain>アセンブリの読み込み先となります。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、通常は、アプリケーション構成ファイルで使用しますが、コンテキストに応じてその他の構成ファイルで使用できます。 詳細については、記事を参照してください。[詳細暗黙的な使用の CAS ポリシー: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET セキュリティ ブログ。  
  
## <a name="example"></a>例  
 次の例では、リモート ソースからアプリケーションに完全な信頼を付与する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [CAS ポリシーの複数の暗黙的な用途: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [方法 : サンドボックスで部分信頼コードを実行する](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
