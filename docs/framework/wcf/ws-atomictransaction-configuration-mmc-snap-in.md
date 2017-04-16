---
title: "WS-AtomicTransaction 構成 MMC スナップイン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# WS-AtomicTransaction 構成 MMC スナップイン
WS\-AtomicTransaction 構成 MMC スナップインは、WS\-AtomicTransaction 設定の一部をローカル マシンとリモート マシンの両方で構成するために使用されます。  
  
## 解説  
 [!INCLUDE[wxp](../../../includes/wxp-md.md)] または [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] を実行している場合に、MMC スナップインにアクセスするには、**\[コントロール パネル\]、\[管理ツール\]、\[コンポーネント サービス\]** の順にクリックし、**\[マイ コンピューター\]** を右クリックして、**\[プロパティ\]** をクリックします。これは MSDTC を構成する場合と同じ場所です。構成で使用できるオプションは、**\[WS\-AT\]** タブにグループ化されています。  
  
 Windows Vista または [!INCLUDE[lserver](../../../includes/lserver-md.md)] を実行している場合に、MMC スナップインにアクセスするには、**\[スタート\]** ボタンをクリックし、**\[検索\]** ボックスに「`dcomcnfg.exe`」と入力します。MMC が開いている場合は、**\[マイ コンピューター\]、\[分散トランザクション コーディネーター\]** ノードの順にクリックし、\[ローカル DTC\] ノードを右クリックして、**\[プロパティ\]** をクリックします。構成で使用できるオプションは、**\[WS\-AT\]** タブにグループ化されています。  
  
 前の手順は、ローカル マシンを構成するためのスナップインを起動するために使用します。[!INCLUDE[wxp](../../../includes/wxp-md.md)] または [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] を実行している場合、リモート コンピューターを構成するには、**\[コントロール パネル\]、\[管理ツール\]、\[コンポーネント サービス\]** の順にクリックし、リモート コンピューターの名前にアクセスします。Windows Vista または [!INCLUDE[lserver](../../../includes/lserver-md.md)] を実行している場合は、前の Vista と [!INCLUDE[lserver](../../../includes/lserver-md.md)] 向けの手順に従います。ただし、リモート コンピューターのノードの **\[分散トランザクション コーディネーター\]\\\[ローカル DTC\]** ノードを使用します。  
  
 ツールのユーザー インターフェイスを使用するには、WsatUI.dll ファイルを登録する必要があります。このファイルのパスは次のとおりです。  
  
 **%PROGRAMFILES%\\Microsoft SDKs\\Windows\\v6.0\\Bin\\WsatUI.dll**  
  
 登録するには、次のコマンドを実行します。  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 このツールを使用すると、WS\-AtomicTransaction の基本設定を変更できます。たとえば、WS\-AtomicTransaction プロトコル サポートの有効\/無効の切り替え、WS\-AT で使用する HTTP ポートの構成、SSL 証明書の HTTP ポートへのバインド、証明書のサブジェクト名指定による証明書の構成、トレース モードの選択とタイムアウトの既定および上限の設定を行うことができます。  
  
 WS\-AtomicTransaction サポートをローカル マシン上にのみ構成する必要がある場合は、このツールのコマンド ライン バージョンを使用できます。コマンド ライン ツール[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[WS\-AtomicTransaction 構成ユーティリティ \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)」を参照してください。  
  
 MMC スナップインとコマンド ライン ツールはいずれも、すべての WS\-AT 設定を構成できるわけではありません。これらの設定は、レジストリを直接変更することによってのみ編集できます。これらのレジストリ設定[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[WS\-AtomicTransaction サポートの構成](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)」を参照してください。  
  
### ユーザー インターフェイスの説明  
 **Enable WS\-Atomic Transaction Network Support** :  
  
 このチェック ボックスをオンまたはオフに切り替えると、このスナップインのすべての GUI コンポーネントが有効または無効になります。  
  
 このチェック ボックスをオンにする前に、受信か送信の通信、またはその両方で \[ネットワーク DTC アクセス\] が有効であることを確認する必要があります。この値は、MSDTC スナップインの **\[セキュリティ\]** タブで確認できます。  
  
#### Network グループ ボックス  
 Network グループでは、HTTPS ポートや追加のセキュリティ設定 \(SSL 暗号化など\) を指定できます。DTC ネットワーク トランザクションが有効でない場合、このグループは無効 \(灰色表示\) です。  
  
 **HTTPS Port**  
  
 これは WS\-AT に使用される HTTPS ポートの値です。有効なポートを表す値は、1 ～ 65535 の範囲内であることが必要です。HTTP ポートを変更すると、HTTP サービス構成が変更されます。つまり、前に使用していた WS\-AT サービス アドレスが解放され、新しいポートに基づいて新しい WS\-AT サービス アドレスが登録されます。さらに、新しく選択したポートは、現在選択している SSL 証明書で暗号化されます。  
  
> [!NOTE]
>  このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。このツールを実行する前にファイアウォールが無効な場合、ファイアウォールに関する追加の構成はありません。  
  
 WS\-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。WS\-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS\-AT の動作を続行します。  
  
 **エンドポイント証明書**  
  
 **\[Select\]** ボタンをクリックすると、ローカル マシン上で現在有効な証明書が一覧表示されます。ユーザーは、SSL 暗号化に使用できる証明書を選択できます。証明書には、秘密キーが必要です。秘密キーがない場合は、エラー メッセージが表示されます。  
  
> [!NOTE]
>  選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。  
  
 **Authorized Accounts**  
  
 **\[Select\]** ボタンをクリックすると、Windows アクセス制御リスト エディターが呼び出されます。このエディターでは、WS\-AtomicTransaction に参加できるユーザーまたはグループを指定できます。指定するには、**\[Participate\]** アクセス許可グループの **\[Allow\]** または **\[Deny\]** ボックスをオンにします。  
  
 **Authorized Certificates**  
  
 **\[Select\]** ボタンをクリックすると、ローカル マシン上で現在有効な証明書が一覧表示されます。WS\-AtomicTransaction への参加が許可される証明書 ID を選択できます。  
  
#### Timeout グループ ボックス  
 **\[Timeout\]** グループ ボックスでは、WS\-AtomicTransaction の既定のタイムアウトと最大のタイムアウトを指定できます。送信のタイムアウトの有効値は 1 ～ 3600 の範囲です。受信のタイムアウトの有効値は 0 ～ 3600 の範囲です。  
  
#### グループ ボックスのトレースとログ記録  
 **\[Tracing and Logging\]** グループ ボックスでは、トレースとログ記録の必要なレベルを構成できます。  
  
 **\[Options\]** ボタンをクリックすると、追加の設定を指定できるページが呼び出されます。  
  
 **\[Trace Level\]** コンボ ボックスでは、<xref:System.Diagnostics.TraceLevel> 列挙体から有効値を選択できます。また、チェック ボックスを使用して、アクティビティ トレースやアクティビティ伝達を実行するかどうかを指定したり、個人を特定する情報を収集するかどうかを指定することもできます。  
  
 **\[Logging Session\]** グループ ボックスでログ セッションを指定することもできます。  
  
> [!NOTE]
>  別のトレース コンシューマーが WS\-AT トレース プロバイダーを使用している場合は、トレース イベントの新しいログ セッションを作成できません。このときにログ記録を構成しようとすると、エラー メッセージ "プロバイダーを有効にできませんでした。エラー コード: 1" が表示されます。  
  
 トレースとログ記録[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[管理と診断](../../../docs/framework/wcf/diagnostics/index.md)」を参照してください。  
  
## 参照  
 [WS\-AtomicTransaction サポートの構成](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)   
 [WS\-AtomicTransaction 構成ユーティリティ \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)   
 [管理と診断](../../../docs/framework/wcf/diagnostics/index.md)