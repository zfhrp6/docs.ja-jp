---
title: "ワークフロー サービス登録ツール (WFServicesReg.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ワークフロー サービス登録ツール (WFServicesReg.exe)
ワークフロー サービス登録ツール \(WFServicesReg.exe\) は、Windows Workflow Foundation \(WF\) サービスの構成要素の追加、削除、または修復に使用できるスタンドアロン ツールです。  
  
## 構文  
  
```  
  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## 解説  
 このツールは、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] のインストール場所である %windir%\\Microsoft.NET\\Framework\\v3.5、または %windir%\\Microsoft.NET\\Framework64\\v3.5 \(64 ビット コンピューターの場合\) にあります。  
  
 次の表は、ワークフロー サービス登録ツール \(WFServicesReg.exe\) で使用できるオプションです。  
  
|オプション|説明|  
|-----------|--------|  
|`/c`|Windows ワークフロー サービスを構成します。インストールおよび修復を行う場合に使用します。|  
|`/r`|Windows ワークフロー サービスの構成を削除します。|  
|`/v`|構成または削除に関する詳細情報を印刷します。|  
|`/m`|MSI ログ形式を有効にします。|  
|`/i`|アプリケーションの実行時にウィンドウを最小化します。|  
  
## 登録  
 このツールは Web.config ファイルを調べ、次の項目を登録します。  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 参照アセンブリ  
  
-   .xoml ファイルのビルド プロバイダー  
  
-   .xoml ファイルおよび .rules ファイルの HTTP ハンドラー  
  
 このツールは Machine.config ファイルを調べ、次の拡張機能を登録します。  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 さらに、次のクライアント メタデータ インポーターも登録します。  
  
-   policyImporters  
  
-   wsdlImporters  
  
 このツールでは、IIS メタベース内の .xoml および .rules のスクリプトマップおよびハンドラーの登録も行われます。  
  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] コンピューターと [!INCLUDE[wxp](../../../includes/wxp-md.md)] コンピューター \(IIS 5.1 および [!INCLUDE[iis601](../../../includes/iis601-md.md)]\) では、.xoml スクリプトマップと .rules スクリプトマップのセットが 1 つ登録されます。  
  
 64 ビット コンピューターでは、`Enable32BitAppOnWin64` スイッチが有効な場合は WOW モードのスクリプトマップが登録され、`Enable32BitAppOnWin64` スイッチが無効な場合はネイティブの 64 ビット スクリプトマップが登録されます。  
  
 [!INCLUDE[wv](../../../includes/wv-md.md)] コンピューターと Windows Server 2008 \(IIS 7.0 以上\) コンピューターでは、.xoml ハンドラーと .rules ハンドラーのセットが 2 つ登録されます。そのうち 1 つは統合モード用で、もう 1 つはクラシック モード用です。  
  
 64 ビット コンピューターでは、`Enable32BitAppOnWin64` スイッチの状態にかかわらず、統合モード用、WOW クラシック モード用、およびネイティブ 64 ビット クラシック モード用の 3 セットのハンドラーが登録されます。  
  
> [!NOTE]
>  ServiceModelreg.exe とは異なり、WFServicesReg.exe では、特定の Web サイトのスクリプトマップまたはハンドラーの追加、削除、修復を行うことはできません。この問題の回避策については、「スクリプトマップの修復」セクションを参照してください。  
  
## 使用シナリオ  
  
### .NET Framework 3.5 インストール後の IIS のインストール  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] コンピューターでは、IIS をインストールする前に [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] がインストールされます。IIS メタベースを使用できないため、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] のインストールは、.xoml スクリプトマップと .rules スクリプトマップをインストールせずに正常に終了します。  
  
 IIS をインストールした後、`/c` スイッチを指定して WFServicesReg.exe ツールを使用することで、特定のスクリプトマップをインストールできます。  
  
### スクリプトマップの修復  
  
#### \[Web サイト\] ノードでスクリプトマップが削除される  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] コンピューターでは、\[Web サイト\] ノードから .xoml または .rules が誤って削除されます。これは、`/c` スイッチを指定して WFServicesReg.exe ツールを実行することにより、修復できます。  
  
#### 特定の Web サイトでスクリプトマップが削除される  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] コンピューターでは、\[Web サイト\] ノードではなく、特定の Web サイト \(\[既定の Web サイト\] など\) から .xoml または .rules が誤って削除されます。  
  
 特定の Web サイトの削除されたハンドラーを修復するには、"WFServicesReg.exe \/r" を実行して、すべての Web サイトからハンドラーを削除した後、"WFServicesReg.exe \/c" を実行して、すべての Web サイトについて適切なハンドラーを作成します。  
  
### IIS モードの切り替え後のハンドラーの構成  
 IIS が共有構成モードであり、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] がインストールされている場合、IIS メタベースは共有された場所で構成されます。IIS を非共有構成モードに切り替えると、ローカル メタベースには必要なハンドラーが格納されません。ローカル メタベースを正しく構成するには、共有メタベースをローカル メタベースにインポートするか、"WFServicesReg.exe \/c" を実行してローカル メタベースを構成してください。