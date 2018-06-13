---
title: WS-AtomicTransaction 構成 MMC スナップイン
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 6613d25cb87209116a7a49a4951953c9a83dfa4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507900"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction 構成 MMC スナップイン
WS-AtomicTransaction 構成 MMC スナップインは、WS-AtomicTransaction 設定の一部をローカル マシンとリモート マシンの両方で構成するために使用されます。  
  
## <a name="remarks"></a>コメント  
 実行している場合[!INCLUDE[wxp](../../../includes/wxp-md.md)]または[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]、MMC スナップインでご覧に移動して**コントロール パネル]、[管理ツール]、[コンポーネント サービス/** を右クリック、**マイ コンピューター**と選択すると**プロパティ**です。 これは MSDTC を構成する場合と同じ場所です。 構成できるオプションは、グループ化されて、 **WS-AT**タブです。  
  
 Windows Vista を実行している場合または[!INCLUDE[lserver](../../../includes/lserver-md.md)]、MMC スナップインでにあります をクリックして、**開始**ボタンをクリックし、入力`dcomcnfg.exe`で、**検索**ボックス。 MMC が開いているときに移動、**マイ Computer\Distributed トランザクション コーディネーター DTC**ノードを右クリックし、**プロパティ**です。 構成できるオプションは、グループ化されて、 **WS-AT**タブです。  
  
 前の手順は、ローカル マシンを構成するためのスナップインを起動するために使用します。 リモート コンピューターを構成する場合でリモート コンピューターの名前を見つける必要があります**コントロール パネル]、[管理ツール]、[コンポーネント サービス/** を実行している場合は、同様の手順を実行および[!INCLUDE[wxp](../../../includes/wxp-md.md)]または[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]です。 Windows Vista を実行している場合または[!INCLUDE[lserver](../../../includes/lserver-md.md)]、vista の場合は、前の手順に従って、[!INCLUDE[lserver](../../../includes/lserver-md.md)]が使用して、**分散トランザクション コーディネーター DTC**リモート コンピューターのノードの下のノードです。  
  
 ツールのユーザー インターフェイスを使用するには、WsatUI.dll ファイルを登録する必要があります。このファイルのパスは次のとおりです。  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 登録するには、次のコマンドを実行します。  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 このツールを使用すると、WS-AtomicTransaction の基本設定を変更できます。 たとえば、WS-AtomicTransaction プロトコル サポートの有効/無効の切り替え、WS-AT で使用する HTTP ポートの構成、SSL 証明書の HTTP ポートへのバインド、証明書のサブジェクト名指定による証明書の構成、トレース モードの選択とタイムアウトの既定および上限の設定を行うことができます。  
  
 WS-AtomicTransaction サポートをローカル マシン上にのみ構成する必要がある場合は、このツールのコマンド ライン バージョンを使用できます。 コマンド ライン ツールの詳細については、次を参照してください。、 [Ws-atomictransaction 構成ユーティリティ (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)トピックです。  
  
 MMC スナップインとコマンド ライン ツールはいずれも、すべての WS-AT 設定を構成できるわけではありません。 これらの設定は、レジストリを直接変更することによってのみ編集できます。 これらのレジストリ設定の詳細については、次を参照してください。 [Ws-atomic Transaction サポートの構成](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)です。  
  
### <a name="user-interface-description"></a>ユーザー インターフェイスの説明  
 **Ws-atomic Transaction ネットワーク サポートを有効にする**:  
  
 このチェック ボックスをオンまたはオフに切り替えると、このスナップインのすべての GUI コンポーネントが有効または無効になります。  
  
 このチェック ボックスをオンにする前に、受信か送信の通信、またはその両方で [ネットワーク DTC アクセス] が有効であることを確認する必要があります。 この値を検証することができます、**セキュリティ**MSDTC スナップインのタブ。  
  
#### <a name="network-group-box"></a>Network グループ ボックス  
 Network グループでは、HTTPS ポートや追加のセキュリティ設定 (SSL 暗号化など) を指定できます。 DTC ネットワーク トランザクションが有効でない場合、このグループは無効 (灰色表示) です。  
  
 **HTTPS ポート**  
  
 これは WS-AT に使用される HTTPS ポートの値です。 有効なポートを表す値は、1 ～ 65535 の範囲内であることが必要です。 HTTP ポートを変更すると、HTTP サービス構成が変更されます。つまり、前に使用していた WS-AT サービス アドレスが解放され、新しいポートに基づいて新しい WS-AT サービス アドレスが登録されます。 さらに、新しく選択したポートは、現在選択している SSL 証明書で暗号化されます。  
  
> [!NOTE]
>  このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。 このツールを実行する前にファイアウォールが無効な場合、ファイアウォールに関する追加の構成はありません。  
  
 WS-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。 WS-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS-AT の動作を続行します。  
  
 **エンドポイントの証明書**  
  
 クリックすると、**選択**ボタンには、ユーザーが SSL 暗号化のために使用する証明書を選択できるように、ローカル コンピューターで証明書が現在使用可能な一覧が表示されます。 証明書には、秘密キーが必要です。 秘密キーがない場合は、エラー メッセージが表示されます。  
  
> [!NOTE]
>  選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。  
  
 **承認されたアカウント**  
  
 クリックすると、**選択**ボタンで位置で指定できます、ユーザーまたはグループを含めることができる ws-atomictransaction をチェックして、Windows アクセス制御リスト エディターが呼び出され、**許可**または**Deny**ボックスに、**参加**アクセス許可グループ。  
  
 **承認された証明書**  
  
 クリックすると、**選択**ボタンは、LocalMachine で現在使用可能な証明書の一覧を表示します。 WS-AtomicTransaction への参加が許可される証明書 ID を選択できます。  
  
#### <a name="timeout-group-box"></a>Timeout グループ ボックス  
 **タイムアウト**グループ ボックスでは、Ws-atomic transaction の既定値および最大のタイムアウトを指定することができます。 送信のタイムアウトの有効値は 1 ～ 3600 の範囲です。 受信のタイムアウトの有効値は 0 ～ 3600 の範囲です。  
  
#### <a name="tracing-and-logging-group-box"></a>グループ ボックスのトレースとログ記録  
 **トレースとログ記録**グループ ボックスでは、必要なトレースとログ記録レベルを構成することができます。  
  
 クリックすると、**オプション**ボタンは、追加の設定を指定するページを呼び出します。  
  
 **トレース レベル**コンビネーション ボックスでは、任意の有効な値から選択することができます、<xref:System.Diagnostics.TraceLevel>列挙します。 また、チェック ボックスを使用して、アクティビティ トレースやアクティビティ伝達を実行するかどうかを指定したり、個人を特定する情報を収集するかどうかを指定することもできます。  
  
 ログ セッションを指定することも、**ログ セッション**グループ ボックス。  
  
> [!NOTE]
>  別のトレース コンシューマーが WS-AT トレース プロバイダーを使用している場合は、トレース イベントの新しいログ セッションを作成できません。 このときにログ記録を構成しようとすると、エラー メッセージ "プロバイダーを有効にできませんでした。 エラー コード: 1" が表示されます。  
  
 トレースとログ記録の詳細については、次を参照してください。[管理と診断](../../../docs/framework/wcf/diagnostics/index.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WS-AtomicTransaction サポートの構成](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)  
 [WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [管理と診断](../../../docs/framework/wcf/diagnostics/index.md)
