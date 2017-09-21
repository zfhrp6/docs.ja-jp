---
title: "プロキシの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
caps.latest.revision: 14
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2576050310c9b1926ee413e4fb1bbcf0c4bf4be
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="proxy-configuration"></a>プロキシの構成
プロキシ サーバーは、リソースに対するクライアント要求を処理します。 プロキシは、要求されたリソースをキャッシュから返したり、リソースが存在するサーバーに要求を転送したりできます。 プロキシは、リモート サーバーに送信された要求の数を減らすことで、ネットワークのパフォーマンスを向上できます。 プロキシを使用して、リソースへのアクセスを制限することもできます。  
  
## <a name="adaptive-proxies"></a>アダプティブ プロキシ  
 .NET Framework には、アダプティブと静的という 2 種類のプロキシがあります。 アダプティブ プロキシは、ネットワーク構成を変更するときに、その設定を調整します。 たとえば、ラップトップ ユーザーがダイヤルアップ ネットワーク接続を起動する場合、アダプティブ プロキシはこの変更を認識し、新しい構成スクリプトを検出して実行し、その設定を適切に調整します。  
  
 アダプティブ プロキシは、構成スクリプトによって構成されます (「[自動プロキシ検出](../../../docs/framework/network-programming/automatic-proxy-detection.md)」を参照)。 スクリプトは、一連のアプリケーション プロトコルと、各プロトコル用のプロキシを生成します。  
  
 いくつかのオプションは、構成スクリプトの実行方法を制御します。 以下を指定できます。  
  
-   構成スクリプトがダウンロードおよび実行される頻度。  
  
-   スクリプトをダウンロードするまで待機する時間。  
  
-   プロキシにアクセスするためにシステムで使用する資格情報。  
  
-   構成スクリプトをダウンロードするためにシステムで使用する資格情報。  
  
 ネットワーク環境での変更により、システムで新しい一連のプロキシを使用することが必要となる場合があります。 ネットワーク接続がダウンしたか、新しいネットワーク接続が開始された場合、システムは新しい環境で構成スクリプトの適切なソースを検出し、新しいスクリプトを実行する必要があります。  
  
 次の表に、アダプティブ プロキシの構成オプションを示します。  
  
|属性、プロパティ、または構成ファイルの設定|説明|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|スクリプトをダウンロードする間の経過時間 (秒単位)。|  
|`scriptDownloadTimeout`|スクリプトをダウンロードするまでの待機時間 (秒単位)。|  
|`useDefaultCredentials` または <xref:System.Net.WebProxy.UseDefaultCredentials>|プロキシにアクセスするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。|  
|`useDefaultCredentialForScriptDownload`|構成スクリプトをダウンロードするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。|  
|`usesystemdefaults`|静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。 この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。<br /><br /> この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。 アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。|  
  
 一般的なアダプティブ プロキシの構成例を次に示します。  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>静的プロキシ  
 静的プロキシは、通常、アプリケーションによって明示的に構成されるか、アプリケーションまたはシステムによって構成ファイルが呼び出されたときに構成されます。 静的プロキシは、企業ネットワークに接続されているデスクトップ コンピューターなど、トポロジがあまり変更されないネットワークで役立ちます。  
  
 いくつかのオプションで静的プロキシの動作を制御します。 以下を指定できます。  
  
-   プロキシのアドレス。  
  
-   ローカル アドレスに対してプロキシをバイパスするかかどうか。  
  
-   一連のアドレスに対してプロキシをバイパスするかかどうか。  
  
 次の表に、静的プロキシの構成オプションを示します。  
  
|属性、プロパティ、または構成ファイルの設定|説明|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` または <xref:System.Net.WebProxy.Address>|使用するプロキシのアドレス。|  
|`bypassonlocal` または <xref:System.Net.WebProxy.BypassProxyOnLocal>|ローカル アドレスに対してプロキシをバイパスするかどうかを制御します。|  
|`bypasslist` または <xref:System.Net.WebProxy.BypassArrayList>|正規表現を使用して、プロキシをバイパスするアドレスのセットを記述します。|  
|`usesystemdefaults`|静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。 この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。 .NET Framework 2.0 でこの値を"true"に設定した場合、Internet Explorer のプロキシ設定は構成ファイル内の他のプロキシ設定でオーバーライドされません。 .NET Framework 1.1 では、構成ファイル内の他のプロキシ設定で Internet Explorer のプロキシ設定をオーバーライドできます。<br /><br /> この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。 アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。|  
  
 一般的な静的プロキシの構成例を次に示します。  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.WebProxy>   
 <xref:System.Net.GlobalProxySelection>   
 [自動プロキシ検出](../../../docs/framework/network-programming/automatic-proxy-detection.md)

