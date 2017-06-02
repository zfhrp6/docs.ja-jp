---
title: "COM+ サービス モデル構成ツール (ComSvcConfig.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF, COM+ 統合"
  - "Windows Communication Foundation, COM+ 統合"
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# COM+ サービス モデル構成ツール (ComSvcConfig.exe)
COM\+ サービス モデル構成コマンド ライン ツール \(ComSvcConfig.exe\) を使用すると、COM\+ インターフェイスを Web サービスとして公開するように構成できます。  
  
## 構文  
  
```  
  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## 解説  
  
> [!NOTE]
>  ComSvcConfig.exe を使用するには、ローカル コンピューターの管理者である必要があります。  
  
 ツールは次の場所にあります。  
  
 %SystemRoot%\\Microsoft.Net\\Framework\\v3.0\\Windows Communication Foundation\\  
  
 ComSvcConfig.exe の詳細については、「[方法 : COM\+ サービス モデル構成ツールを使用する](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)」を参照してください。  
  
 次の表は、ComSvcConfig.exe で使用できるモードを示します。  
  
|オプション|説明|  
|-----------|--------|  
|`install`|サービス モデル統合に COM\+ インターフェイスの構成をインストールします。<br /><br /> 短縮形 : `/i`。|  
|`uninstall`|サービス モデル統合から COM\+ インターフェイスの構成をアンインストールします。<br /><br /> 短縮形 : `/u`。|  
|`list`|サービス モデル統合に構成されるインターフェイスを持つ COM\+ アプリケーションとコンポーネントの情報を一覧表示します。<br /><br /> 短縮形 : `/l`。|  
  
 次の表は、ComSvcConfig.exe で使用できるフラグを示します。  
  
|オプション|説明|  
|-----------|--------|  
|`/application:<` *ApplicationID*  `&#124;`  *ApplicationName* `>`|構成する COM\+ アプリケーションを指定します。<br /><br /> 短縮形 : `/a`。|  
|`/contract:<` *ClassID*  `&#124;`  *ProgID*  `&#124; *,` *InterfaceID*  `&#124;`  *InterfaceName*  `&#124; *` `>`|サービスのコントラクトとして構成される COM\+ コンポーネントとインターフェイスを指定します。<br /><br /> 短縮形 : `/c`。<br /><br /> コンポーネント名とインターフェイス名を指定する場合はワイルドカード文字 \(\*\) を使用できますが、望まないインターフェイスも公開されることがあるため、ワイルドカード文字を使用しないことをお勧めします。|  
|`/hosting:<` *complus*  `&#124;`  *was* `>`|COM\+ ホスト モードと Web ホスト モードのどちらを使用するかを指定します。<br /><br /> 短縮形 : `/h`。<br /><br /> COM\+ ホスト モードを使用するには、COM \+ アプリケーションの明示的なアクティブ化が必要です。Web ホスト モードを使用すると、COM\+ アプリケーションを必要なときに自動的にアクティブ化できます。COM\+ アプリケーションがライブラリ アプリケーションの場合は、インターネット インフォメーション サービス \(IIS\) のプロセスで実行します。COM\+ アプリケーションがサーバー アプリケーションの場合は、Dllhost.exe のプロセスで実行します。|  
|`/webSite:<` *WebsiteName* `>`|Web ホスト モードを使用する場合は、ホストする Web サイトを指定します \(`/hosting` フラグを参照\)。<br /><br /> 短縮形 : `/w`。<br /><br /> Web サイトを指定しない場合は、既定の Web サイトが使用されます。|  
|`/webDirectory:<` *WebDirectoryName* `>`|Web ホストを使用する場合は、ホストする仮想ディレクトリを指定します \(`/hosting` フラグを参照\)。<br /><br /> 短縮形 : `/d`。|  
|`/mex`|サービスからコントラクト定義を取得するクライアントをサポートするには、既定のサービス構成に Metadata Exchange \(MEX\) サービス エンドポイントを追加します。<br /><br /> 短縮形 : `/x`。|  
|`/id`|アプリケーション、コンポーネント、およびインターフェイス情報を ID として表示します。<br /><br /> 短縮形 : `/k`。|  
|`/nologo`|ComSvcConfig.exe がロゴを表示しないようにします。<br /><br /> 短縮形 : `/n`。|  
|`/verbose`|発生するエラーに加えて、すべての警告または情報テキストを出力します。<br /><br /> 短縮形 : `/v`。|  
|`/help`|使用方法を示すメッセージを表示します。<br /><br /> 短縮形 : `/?`。|  
|`/partial`|指定されたインターフェイスが、公開できる 1 つ以上のメソッド署名を含む場合にサービス構成を生成します。サービスの初期化時に、互換性のあるメソッドはサービス コントラクトで操作として表示され、互換性のないメソッドはサービス コントラクトから除外されます。<br /><br /> このフラグが指定されていない場合は、指定されたインターフェイスが互換性のないメソッドを 1 つ以上含むとツールはサービス構成を生成しません。|  
  
## 例  
  
### 説明  
 次の例は、COM\+ ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに \(OnlineStore COM\+ アプリケーションの\) `ItemOrders.IFinancial` コンポーネントの `IFinances` インターフェイスを追加します。発生するエラーに加えて、すべての警告が出力されます。  
  
### コード  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### 説明  
 次の例は、Web ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに \(OnlineWarehouse COM\+ アプリケーションの\) `ItemInventory.Warehouse` コンポーネントの `IStockLevels` インターフェイスを追加します。Web サービスは、IIS の OnlineWarehouse 仮想ディレクトリで Web ホストされます。  
  
### コード  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### 説明  
 次の例は、Web サービスとして公開されるインターフェイスのセットから \(OnlineStore COM\+ アプリケーションの\) `ItemOrders.Financial` コンポーネントの `IFinances` インターフェイスを削除します。  
  
### コード  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### 説明  
 次の例は、ローカル マシン上の OnlineStore COM\+ アプリケーションの現在公開されている COM\+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。  
  
### コード  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## 参照  
 [方法 : COM\+ サービス モデル構成ツールを使用する](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)