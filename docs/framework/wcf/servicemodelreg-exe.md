---
title: "ServiceModel 登録ツール (ServiceModelReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7032fd6005d5eccf27e0ca34cd89c050260d6e4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>ServiceModel 登録ツール (ServiceModelReg.exe)
このコマンド ライン ツールは、単一コンピューター上で WCF および WF コンポーネントの登録を管理するための機能を提供します。 WCF および WF コンポーネントはインストール時に構成されるため、通常の状況ではこのツールを使用する必要はありません。 しかし、サービスのアクティブ化に関する問題が発生する場合は、このツールを使用してコンポーネントを登録できます。  
  
## <a name="syntax"></a>構文  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>コメント  
 ツールは次の場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  ServiceModel 登録ツールを実行するときに[!INCLUDE[wv](../../../includes/wv-md.md)]、 **Windows の機能の**ダイアログことが反映されない、 **Windows Communication Foundation HTTP Activation** 下のオプション**Microsoft .NET Framework 3.0**がオンになっています。 **Windows の機能の**ダイアログをクリックしてアクセスできる**開始**、順にクリックして**実行**」と入力し、 **OptionalFeatures**です。  
  
 次の表は、ServiceModelReg.exe で使用できるオプションを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|`-ia`|WCF および WF のすべてのコンポーネントをインストールします。|  
|`-ua`|WCF および WF のすべてのコンポーネントをアンインストールします。|  
|`-r`|WCF および WF のすべてのコンポーネントを修復します。|  
|`-i`|-c で指定された WCF および WF のコンポーネントをインストールします。|  
|`-u`|-c で指定された WCF および WF のコンポーネントをアンインストールします。|  
|`-c`|コンポーネントをインストールまたはアンインストールします。<br /><br /> -httpnamespace – HTTP Namespace 予約<br />-tcpportsharing – TCP ポート共有サービス<br />-tcpactivation – TCP のアクティブ化サービス (.NET 4 クライアント プロファイルでサポートされていません)<br />-namedpipeactivation-名前付きパイプのアクティブ化サービス (.NET 4 クライアント プロファイルでサポートされていません<br />(.NET 4 クライアント プロファイルでサポートされていません - msmqactivation – MSMQ アクティブ化サービス<br />-etw – ETW イベントの追跡マニフェスト (Windows Vista またはそれ以降)|  
|`-q`|Quiet モード (エラー ログのみ表示)|  
|`-v`|Verbose モード|  
|`-nologo`|著作権やバナー メッセージを表示しません。|  
|`-?`|ヘルプ テキストを表示します。|  
  
## <a name="fixing-the-fileloadexception-error"></a>FileLoadException エラーの修正  
 コンピューターに以前のバージョンの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] をインストールしている場合は、ServiceModelReg ツールを実行して新しいインストールを登録するときに、`FileLoadFoundException` エラーが発生することがあります。 旧バージョンのインストールから手動でファイルを削除しても、machine.config 設定が元のままである限り、このエラーが発生する可能性があります。  
  
 エラー メッセージは、次のようになります。  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel Version 2.0.0.0 アセンブリが旧 CTP (Customer Technology Preview) リリースによってインストールされていたというエラー メッセージに注目する必要があります。 最新バージョンの System.ServiceModel アセンブリは、2.0.0.0 ではなく 3.0.0.0 です。 したがって、旧 CTP リリースの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] がインストールされたままで、完全にはアンインストールされていないコンピューターに正式の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] リリースをインストールすると、この問題が発生します。  
  
 ServiceModelReg.exe は、旧バージョンのエントリをクリーンアップすることも、新しいバージョンのエントリを登録することもできません。 唯一の回避策は、machine.config を手動で編集することです。このファイルは次の場所にあります。  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を 64 ビット コンピューターで実行している場合は、次の場所にある同じファイルも編集する必要があります。  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 このファイルを参照する XML ノードを見つけ"'system.servicemodel, Version 2.0.0.0 を ="、および子ノードを削除します。 ファイルを保存し ServiceModelReg.exe を再実行すると、この問題は解決します。  
  
## <a name="examples"></a>例  
 次の例に、ServiceModelReg.exe ツールの最も一般的なオプションの使用方法を示します。  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
