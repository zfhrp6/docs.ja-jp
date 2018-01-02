---
title: "&lt;httpListener&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt;要素 (ネットワーク設定)
によって使用されるパラメーターをカスタマイズ、<xref:System.Net.HttpListener>クラスです。  
  
 \<configuration>  
\<system.net >  
\<設定 >  
\<httpListener >  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>型  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|unescapeRequestUrl|どうかを示すブール値、<xref:System.Net.HttpListener>インスタンスは、変換された URI ではなく生のエスケープ解除された URI を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
 **UnescapeRequestUrl**場合に属性が示す<xref:System.Net.HttpListener>変換された URI でパーセント エンコード値を変換し、その他の正規化手順は実行ではなく生のエスケープ解除された URI を使用します。  
  
 ときに、<xref:System.Net.HttpListener>インスタンスを介して要求を受け取ると、`http.sys`サービスによって提供される URI 文字列のインスタンス作成`http.sys`、として公開して、<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>プロパティです。  
  
 `http.sys`サービスは 2 つの要求の URI 文字列を公開します。  
  
-   生の URI  
  
-   変換された URI  
  
 生の URI は、<xref:System.Uri?displayProperty=nameWithType>の HTTP 要求の要求行で提供されます。  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 によって提供される生の URI `http.sys` 、上記で説明した要求は「/path/」です。 これは、ネットワーク経由で送信された HTTP 動詞の後に、文字列を表します。  
  
 `http.sys`サービスが HTTP 要求の行で指定された URI を使用して、要求で提供される情報から変換された URI を作成しに、元のサーバー要求を決定するホスト ヘッダーを転送する必要があります。 これは、一連の登録済み URI プレフィックスの要求からの情報を比較することによって行います。 HTTP サーバー SDK のドキュメントでは、この変換された URI を HTTP_COOKED_URL 構造と呼びます。  
  
 登録されている URI プレフィックスを持つ要求を比較できるようにするには、するために、要求に正規化をいくつか行う必要があります。 変換された URI 上のサンプルではようになります。  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`を組み合わせたものをサービス、<xref:System.Uri.Host%2A?displayProperty=nameWithType>変換された URI を作成する要求行の文字列とプロパティの値。 さらに、`http.sys`と<xref:System.Uri?displayProperty=nameWithType>クラスは次も実行します。  
  
-   エスケープを解除すべてパーセント エンコードされた値。  
  
-   Utf-16 文字表記に非 ASCII 文字をパーセント エンコードに変換します。 Unicode 文字 (Unicode エンコーディング %uxxxx 形式を使用して) だけでなく utf-8 と ANSI や DBCS 文字はサポートされていることに注意してください。  
  
-   パスの圧縮など、他の正規化の手順を実行します。  
  
 要求には、パーセントでエンコードされた値に使用されるエンコーディングに関する情報が含まれていない、ためには、パーセント エンコード値を解析するだけ、正しいエンコーディングを決定することはできません。  
  
 したがって`http.sys`プロセスを変更するための 2 つのレジストリ キーを提供します。  
  
|レジストリ キー|既定値|説明|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|0 の場合、 `http.sys` UTF で 8 でエンコードされた Url のみを受け入れます。<br /><br /> 0 以外の場合`http.sys`も要求で ANSI でエンコードされたまたは DBCS でエンコードされた Url を受け取ります。|  
|FavorUTF8|1|0 以外の場合`http.sys`し、変換に失敗したし、EnableNonUTF8 が 0 でない場合に utf-8 として URL を先にデコードすると常に、Http.sys を ANSI または DBCS としてデコードしようとします。<br /><br /> 0 の場合 (そして EnableNonUTF8 0 ではない)、`http.sys`場合は、その ANSI または DBCS; としてデコードする試行が成功しない、utf-8 の変換を試みます。|  
  
 ときに<xref:System.Net.HttpListener>要求を受信して変換された URI を使用して`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。  
  
 Uri の文字と数字以外の文字をサポートする必要があります。 例としては次の URI は、顧客の顧客情報の取得に使用される「1/3812」番号します。  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Uri (%2f) で、パーセント エンコードのスラッシュを注意してください。 これは、ここでは、スラッシュ文字を表し、データはパス区切り記号ではないため、必要に応じて。  
  
 Uri のコンス トラクターに文字列を渡すことは、次の URI になります。  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 分割して、パスのセグメントに、次の要素の結果になります。  
  
 `Customer('1`  
  
 `3812')`  
  
 これは、要求の送信元の目的ではありません。  
  
 場合、 **unescapeRequestUrl**属性に設定されている**false**、<xref:System.Net.HttpListener>要求を受信から変換された URI ではなく生の URI を使用して、 `http.sys` への入力として<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。  
  
 既定値、 **unescapeRequestUrl**属性は**true**です。  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>プロパティを使用しての現在の値を取得すること、 **unescapeRequestUrl**該当する構成ファイルからの属性です。  
  
## <a name="example"></a>例  
 次の例は、構成する方法を示します、<xref:System.Net.HttpListener>から変換された URI ではなく生の URI を使用する要求を受信時`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||
|-|-|  
|名前空間|System.Net|  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>参照  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
