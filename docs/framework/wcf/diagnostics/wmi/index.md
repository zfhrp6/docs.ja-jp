---
title: 診断用の WMI (Windows Management Instrumentation) の使用
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8fd88edd711513d1b143029d8088401c9945d13
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>診断用の WMI (Windows Management Instrumentation) の使用
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI (Windows Management Instrumentation) プロバイダーを介して実行時のサービスの検査データを公開します。  
  
## <a name="enabling-wmi"></a>WMI の有効化  
 WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] WMI SDK を参照してください[Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx)です。 WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。  
  
 WMI プロバイダーは、WBEM と互換性のあるインターフェイスを通して実行時にインストルメンテーションを公開するコンポーネントです。 これは、属性と値のペアを持つ WMI オブジェクトのセットで構成されます。 ペアには多くの単純型を指定できます。 管理ツールは、実行時にインターフェイスを介してサービスに接続できます。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、アドレス、バインディング、動作、リスナーなどのサービスの属性を公開します。  
  
 組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにできます。 これには、`wmiProviderEnabled`の属性、 [\<診断 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)で、 [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションで、次の例のように構成します。  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 この構成エントリには、WMI インターフェイスが開示されます。 管理アプリケーションはこのインターフェイスを通して接続し、アプリケーションの Management Instrumentation にアクセスできるようになります。  
  
## <a name="accessing-wmi-data"></a>WMI データへのアクセス  
 WMI データには、複数の異なる方法でアクセスできます。 マイクロソフトでは、WMI Api を提供するスクリプト、Visual Basic アプリケーションの場合、C++ アプリケーション、および[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]です。 詳細については、次を参照してください。 [WMI を使用した](http://go.microsoft.com/fwlink/?LinkId=95183)です。  
  
> [!CAUTION]
>  .NET Framework 提供のメソッドを使用し、プログラムで WMI データにアクセスする場合、そのようなメソッドは接続確立時に例外をスローする場合があることを認識しておく必要があります。 接続は、<xref:System.Management.ManagementObject> インスタンスの構築中に確立されませんが、実際のデータ交換が含まれた最初の要求時に確立されます。 したがって、`try..catch` ブロックを使用して例外をキャッチする必要があります。  
  
 トレース レベルやメッセージ ログ レベルだけでなく、WMI の `System.ServiceModel` トレース ソースのメッセージ ログ オプションも変更できます。 アクセスすることによってこれ行う、 [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)ブール型プロパティを公開するインスタンス: `LogMessagesAtServiceLevel`、 `LogMessagesAtTransportLevel`、 `LogMalformedMessages`、および`TraceLevel`です。 そのため、メッセージ ログ用のトレース リスナーを構成していても、これらのオプションを構成で `false` に設定している場合は、後でアプリケーションを実行しているときに `true` に変更できます。 これで、メッセージ ログが実行時に有効になります。 同様に、構成ファイルでメッセージ ログを有効にしている場合は、実行時に WMI を使用して無効にできます。  
  
 構成ファイルで、メッセージ ログのメッセージ ログ トレース リスナーまたはトレースの `System.ServiceModel` トレース リスナーが指定されていない場合、WMI が変更を受け入れても変更は有効になりません。 各リスナーを正しく設定の詳細については、次を参照してください。[メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)と[トレースの構成](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)です。 構成で設定された他のすべてのトレース ソースのトレース レベルは、アプリケーションが開始されると有効になり変更できません。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、スクリプト用に `GetOperationCounterInstanceName` メソッドを公開します。 このメソッドに操作名を指定した場合、このメソッドはパフォーマンス カウンターのインスタンス名を返します。 ただし、このメソッドは入力を検証しません。 したがって、正しくない操作名を指定した場合、正しくないカウンター名が返されます。  
  
 接続先サービスの `OutgoingChannel` クライアントが `Service` メソッド内に作成されていない場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インスタンスの `Service` プロパティは、別のサービスに接続するのに、そのサービスにより開かれたチャネルをカウントしません。  
  
 **注意**WMI でのみサポート、<xref:System.TimeSpan>最大 3 つの 10 進数のポイントの値します。 たとえば、サービスでプロパティの 1 つを <xref:System.TimeSpan.MaxValue> に設定した場合、WMI ではその値を小数点以下 3 桁より下を切り捨て表示します。  
  
## <a name="security"></a>セキュリティ  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI プロバイダーは環境内のサービスの検索を許しているため、環境へのアクセスの許可については十分に注意する必要があります。 既定の "管理者のみ" のアクセスを緩めた場合、信頼性の低いパーティに環境内の機密性のあるデータへのアクセスを許可する場合があります。 特にリモート WMI アクセスに対するアクセス許可を緩めた場合、大量の攻撃を受ける可能性があります。 過剰の WMI 要求により大量の処理が発生した場合、パフォーマンスが低下する可能性があります。  
  
 さらに、MOF ファイルに対するアクセス許可を緩めた場合、信頼性の低いパーティが WMI の動作を操作して WMI スキーマに読み込まれるオブジェクトを変更することができます。 たとえば、フィールドを削除して、重要データを管理者から隠したり、例外を設定しないかまたは例外の原因とならないフィールドを追加したりすることができます。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI プロバイダーの既定では、"メソッドの実行"、"プロバイダーによる書き込み"、"アカウントの有効化" 権限が管理者に付与され、"アカウントの有効化" 権限が ASP.NET、ローカル サービス、ネットワーク サービスに付与されます。 特に、[!INCLUDE[wv](../../../../../includes/wv-md.md)] 以外のプラットフォームでは、ASP.NET アカウントは WMI ServiceModel 名前空間に対して読み取りアクセスが可能です。 特定のユーザー グループに対してこれらの権限を付与したくない場合は、WMI プロバイダーを非アクティブにするか (既定では無効に設定されています)、特定のユーザー グループのアクセスを無効にする必要があります。  
  
 また、構成を使用して WMI を有効にする場合、ユーザー権限が不十分のため WMI が有効にならない場合があります。 ただし、このエラーを記録するイベントはイベント ログに書き込まれません。  
  
 ユーザー権限のレベルを変更するには、次の手順に従います。  
  
1.  [スタート] ボタンしし、実行し、入力**compmgmt.msc**です。  
  
2.  右クリック**サービスとアプリケーション] の [WMI コントロール**を選択する**プロパティ**です。  
  
3.  選択、**セキュリティ** タブに移動し、 **Root/servicemodel**名前空間。 クリックして、**セキュリティ**ボタンをクリックします。  
  
4.  特定のグループまたはアクセスを制御し、使用するユーザーを選択、**許可**または**Deny**をアクセス許可を構成するのには、チェック ボックスをオンします。  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>追加ユーザーへの WCF WMI 登録権限の付与  
 WCF は管理データを WMI に公開します。 これには、「分離プロバイダー」とも呼ばれる、インプロセス WMI プロバイダーをホストします。 管理データを公開するには、このプロバイダーを登録するアカウントに適切な権限が必要です。 Windows では、権限を持つアカウントの少数のセットのみが、既定で分離プロバイダーを登録できます。 ユーザーは通常、既定のセットではないアカウントで実行している WCF サービスから WMI データを公開するので、これは問題です。  
  
 このアクセスを提供するために、管理者は、次の権限を追加のアカウントに次の順序で付与する必要があります。  
  
1.  WCF WMI 名前空間へのアクセス権限  
  
2.  WCF 分離 WMI プロバイダーの登録権限  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>WMI 名前空間へのアクセス権限を付与するには  
  
1.  次の PowerShell スクリプトを実行します。  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     この PowerShell スクリプトは、組み込みのユーザー グループの"ルート/servicemodel"WMI 名前空間へのアクセスを付与するのにセキュリティ記述子定義言語 (SDDL) を使用します。 次の ACL が指定されます。  
  
    -   組み込みの管理者 (BA) – 既にアクセス権を持っています。  
  
    -   ネットワーク サービス (NS) - 既にアクセス権を持っています。  
  
    -   ローカル システム (LS) - 既にアクセス権を持っています。  
  
    -   組み込みのユーザー – アクセス権を付与するグループ。  
  
#### <a name="to-grant-provider-registration-access"></a>プロバイダーに登録アクセス権を付与するには  
  
1.  次の PowerShell スクリプトを実行します。  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>任意のユーザーまたはグループへのアクセス権の付与  
 このセクションの例では、すべてのローカル ユーザーに WMI プロバイダー登録権限を付与します。 組み込まれていないユーザーまたはグループにアクセス権を付与する場合は、そのユーザーまたはグループのセキュリティ識別子 (SID) を取得する必要があります。 任意のユーザーの SID を取得する簡単な方法はありません。 1 つの方法としては、目的のユーザーとしてログオンし、次のシェル コマンドを発行します。  
  
```  
Whoami /user  
```  
  
 これにより、現在のユーザーの SID が提供されますが、この方法を使用して任意のユーザーで SID を取得することはできません。 SID を取得する別の方法が使用するには、 [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467)ツールから、[管理タスク用の Windows 2000 リソース キット ツール](http://go.microsoft.com/fwlink/?LinkId=178660)です。 このツールは、2 人のユーザー (ローカルまたはドメイン) の SID を比較し、副作用として、2 つの SID をコマンド ラインに出力します。 詳細については、次を参照してください。 [Well Known Sid](http://go.microsoft.com/fwlink/?LinkId=186468)です。  
  
## <a name="accessing-remote-wmi-object-instances"></a>リモート WMI オブジェクトのインスタンスへのアクセス  
 リモート コンピューターの [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI インスタンスにアクセスする必要がある場合、アクセスに使用するツールのパケットのプライバシーを有効にする必要があります。 次のセクションでは、WMI CIM Studio、Windows Management Instrumentation テスト、および .NET SDK 2.0 を使用してこれらを実現する方法を説明します。  
  
### <a name="wmi-cim-studio"></a>WMI CIM Studio  
 インストールした場合[WMI 管理ツール](http://go.microsoft.com/fwlink/?LinkId=95185)インスタンスにアクセスする WMI WMI CIM Studio を使用することができます。 このツールは次のフォルダーにあります。  
  
 **%windir%\Program Files\WMI ツール\\**  
  
1.  **名前空間への接続:** ウィンドウで、「 **root \servicemodel**  をクリック**ok です。**  
  
2.  **WMI CIM Studio Login**ウィンドウで、をクリックして、**オプション >>** ボタンをクリックしてウィンドウを展開します。 選択**パケットのプライバシー**の**認証レベル**、 をクリック**OK**です。  
  
### <a name="windows-management-instrumentation-tester"></a>Windows Management Instrumentation テスト  
 このツールは Windows によりインストールされます。 これを実行するように入力してコマンド コンソールを起動して**cmd.exe**で、**開始/実行** ダイアログ ボックスをクリック**OK**です。 次に、入力**wbemtest.exe**コマンド ウィンドウでします。 Windows Management Instrumentation テスト ツールが起動します。  
  
1.  クリックして、**接続**ウィンドウの右上隅のボタンをクリックします。  
  
2.  新しいウィンドウで、入力**root \servicemodel**の**Namespace**フィールド、および select**パケット プライバシー**の**認証レベル**です。 **[接続]** をクリックします。  
  
### <a name="using-managed-code"></a>マネージ コードの使用  
 <xref:System.Management> 名前空間が提供するクラスを使用して、リモートの WMI インスタンスにプログラムでアクセスすることもできます。 これを実行する方法を次のコード例に示します。  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
