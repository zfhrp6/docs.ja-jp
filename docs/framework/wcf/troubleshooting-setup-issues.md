---
title: "セットアップ問題のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# セットアップ問題のトラブルシューティング
ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] セットアップ問題のトラブルシューティングの方法について説明します。  
  
## .NET Framework 3.0 の MSI 修復操作の実行では修復されない一部の Windows Communication Foundation レジストリ キー  
 次のいずれかのレジストリ キーを削除した場合  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelService 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelOperation 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\SMSvcHost 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSDTC Bridge 3.0.0.0  
  
 **\[コントロール パネル\]** の **\[プログラムの追加と削除\]** から起動した .NET Framework 3.0 インストーラーを使用して修復を実行しても、上記のキーは再作成されません。これらのキーを正しく再作成するには、.NET Framework 3.0 をアンインストール後、再インストールする必要があります。  
  
## WMI サービスの破損により .NET Framework 3.0 パッケージのインストール中に Windows Communication Foundation WMI プロバイダーのインストールがブロックされる  
 WMI サービスの破損により、Windows Communication Foundation WMI プロバイダーのインストールがブロックされることがあります。インストール中、Windows Communication Foundation インストーラーは mofcomp.exe コンポーネントを使用して WCF .mof ファイルを登録できません。発生する現象を次に示します。  
  
1.  .NET Framework 3.0 のインストールは正常に完了するのに、WCF WMI プロバイダーが登録されない。  
  
2.  アプリケーション イベント ログに、WCF の WMI プロバイダーの登録、または mofcomp.exe の実行に関する問題を示すエラー イベントが表示される。  
  
3.  ユーザーの %temp% ディレクトリの dd\_wcf\_retCA\* という名前のセットアップ ログ ファイルに、WCF WMI プロバイダーの登録に失敗したことが示される。  
  
4.  イベント ログまたはセットアップ トレース ログ ファイルに、次の例外のいずれかが記録される。  
  
     ServiceModelReg \[11:09:59:046\]: System.ApplicationException : "E:\\WINDOWS\\Microsoft.NET\\Framework\\v3.0\\Windows Communication Foundation\\ServiceModel.mof" で E:\\WINDOWS\\system32\\wbem\\mofcomp.exe を実行している間に予期しない結果 3 が発生しました  
  
     または、  
  
     ServiceModelReg \[07:19:33:843\]: System.TypeInitializationException : 'System.Management.ManagementPath' の型初期化子が例外をスローしました。\-\-\-\> System.Runtime.InteropServices.COMException \(0x80040154\) : CLSID {CF4CC405\-E2C5\-4DDD\-B3CE\-5E7582D8C9FA} を含むコンポーネントの COM クラス ファクトリを取得中に、次のエラーが発生しました: 80040154。  
  
     または、  
  
     ServiceModelReg \[07:19:32:750\]: System.IO.FileNotFoundException : ファイルまたはアセンブリ 'C:\\WINDOWS\\system32\\wbem\\mofcomp.exe'、またはその依存関係の 1 つが読み込めませんでした。指定されたファイルが見つかりません。  
  
     ファイル名 : C:\\WINDOWS\\system32\\wbem\\mofcomp.exe  
  
 上で説明した問題を解決するためには、次の手順を実行する必要があります。  
  
1.  [WMI 診断ユーティリティ バージョン 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) を実行して WMI サービスを修復します。このツールの使い方[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[WMI 診断ユーティリティ](http://go.microsoft.com/fwlink/?LinkId=94686)」を参照してください。  
  
 **\[コントロール パネル\]** にある **\[プログラムの追加と削除\]** アプレットを使用して、.NET Framework 3.0 のインストールを修復するか、.NET Framework 3.0 をアンインストール後に再インストールします。  
  
## .NET Framework 3.5 のインストール後に .NET Framework 3.0 を修復すると、.NET Framework 3.5 によって導入された machine.config 内の構成要素が削除される  
 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] をインストールした後に .NET Framework 3.0 を修復すると、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] によって導入された machine.config 内の構成要素が削除されます。ただし、web.config は元の状態のままになります。この問題に対処するには、ARP 経由でこの作業を行った後に [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を修復するか、`/c` スイッチを指定した [ワークフロー サービス登録ツール \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) を使用します。  
  
 [ワークフロー サービス登録ツール \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) は、%windir%\\Microsoft.NET\\framework\\v3.5\\ または %windir%\\Microsoft.NET\\framework64\\v3.5\\ にあります。  
  
## .NET Framework 3.5 のインストール後に WCF\/WF Webhost に対して IIS を適切に構成する  
 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] のインストールでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に関連する追加の IIS 構成設定の構成に失敗すると、インストール ログにエラーが記録され、インストールが続行されます。WorkflowServices アプリケーションを実行しようとしても、必要な構成設定がないため、実行することはできません。たとえば、xoml やルール サービスの読み込みに失敗する可能性があります。  
  
 この問題に対処するには、`/c` スイッチを指定した [ワークフロー サービス登録ツール \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) を使用して、コンピューター上の IIS スクリプト マップを適切に構成します。[ワークフロー サービス登録ツール \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) は、%windir%\\Microsoft.NET\\framework\\v3.5\\ または %windir%\\Microsoft.NET\\framework64\\v3.5\\ にあります。  
  
## アセンブリ 'System.ServiceModel, Version 3.0.0.0, Culture\=neutral, PublicKeyToken\=b77a5c561934e089' から型 'System.ServiceModel.Activation.HttpModule' を読み込むことができない  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] がインストールされている場合に、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] HTTP Activation を有効にすると、このエラーが発生します。この問題を解決するには、[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] コマンド プロンプト内から次のコマンドを実行します。  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## 参照  
 [セットアップ手順](../../../docs/framework/wcf/samples/set-up-instructions.md)