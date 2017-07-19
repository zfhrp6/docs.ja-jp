---
title: "ServiceModel 登録ツール (ServiceModelReg.exe) | Microsoft Docs"
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
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# ServiceModel 登録ツール (ServiceModelReg.exe)
このコマンド ライン ツールは、単一コンピューター上で WCF および WF コンポーネントの登録を管理するための機能を提供します。WCF および WF コンポーネントはインストール時に構成されるため、通常の状況ではこのツールを使用する必要はありません。しかし、サービスのアクティブ化に関する問題が発生する場合は、このツールを使用してコンポーネントを登録できます。  
  
## 構文  
  
```  
  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## 解説  
 ツールは次の場所にあります。  
  
 %SystemRoot%\\Microsoft.Net\\Framework\\v3.0\\Windows Communication Foundation\\  
  
> [!NOTE]
>  [!INCLUDE[wv](../../../includes/wv-md.md)] で ServiceModel 登録ツールを実行している場合は、**\[Windows の機能\]** ダイアログ ボックスに、**\[Microsoft .NET Framework 3.0\]** の下にある **\[Windows Communication Foundation HTTP Activation\]** オプションが有効であることが反映されない場合があります。**\[Windows の機能\]** ダイアログ ボックスには、**\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックして、「**OptionalFeatures**」と入力することでアクセスできます。  
  
 次の表は、ServiceModelReg.exe で使用できるオプションを示します。  
  
|オプション|説明|  
|-----------|--------|  
|`-ia`|WCF および WF のすべてのコンポーネントをインストールします。|  
|`-ua`|WCF および WF のすべてのコンポーネントをアンインストールします。|  
|`-r`|WCF および WF のすべてのコンポーネントを修復します。|  
|`-i`|\-c で指定された WCF および WF のコンポーネントをインストールします。|  
|`-u`|\-c で指定された WCF および WF のコンポーネントをアンインストールします。|  
|`-c`|コンポーネントをインストールまたはアンインストールします。<br /><br /> -   httpnamespace \- HTTP 名前空間の予約<br />-   tcpportsharing –TCP ポート共有サービス<br />-   tcpactivation \- TCP アクティベーション サービス \(.NET 4 クライアント プロファイルでは非サポート\)<br />-   namedpipeactivation \- 名前付きパイプ アクティベーション サービス \(.NET 4 クライアント プロファイルでは非サポート\)<br />-   msmqactivation \- MSMQ アクティベーション サービス \(.NET 4 クライアント プロファイルでは非サポート\)<br />-   etw \- ETW イベント トレース マニフェスト \(Windows Vista またはそれ以降\)|  
|`-q`|Quiet モード \(エラー ログのみ表示\)|  
|`-v`|Verbose モード|  
|`-nologo`|著作権やバナー メッセージを表示しません。|  
|`-?`|ヘルプ テキストを表示します。|  
  
## FileLoadException エラーの修正  
 コンピューターに以前のバージョンの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] をインストールしている場合は、ServiceModelReg ツールを実行して新しいインストールを登録するときに、`FileLoadFoundException` エラーが発生することがあります。旧バージョンのインストールから手動でファイルを削除しても、machine.config 設定が元のままである限り、このエラーが発生する可能性があります。  
  
 エラー メッセージは、次のようになります。  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 System.ServiceModel Version 2.0.0.0 アセンブリが旧 CTP \(Customer Technology Preview\) リリースによってインストールされていたというエラー メッセージに注目する必要があります。最新バージョンの System.ServiceModel アセンブリは、2.0.0.0 ではなく 3.0.0.0 です。したがって、旧 CTP リリースの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] がインストールされたままで、完全にはアンインストールされていないコンピューターに正式の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] リリースをインストールすると、この問題が発生します。  
  
 ServiceModelReg.exe は、旧バージョンのエントリをクリーンアップすることも、新しいバージョンのエントリを登録することもできません。唯一の回避策は、machine.config を手動で編集することです。このファイルは次の場所にあります。  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を 64 ビット コンピューターで実行している場合は、次の場所にある同じファイルも編集する必要があります。  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 "System.ServiceModel, Version\=2.0.0.0" を参照しているこのファイル内の XML ノードを見つけ、それらのノードと子ノードを削除します。ファイルを保存し ServiceModelReg.exe を再実行すると、この問題は解決します。  
  
## 例  
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