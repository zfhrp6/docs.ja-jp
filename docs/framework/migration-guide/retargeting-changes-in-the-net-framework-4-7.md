---
title: ".NET Framework 4.7 における再ターゲットの変更点 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes,.NET Framework
- retargeting changes,.NET Framework 4.7
- application compatibility
ms.assetid: d98bf1e3-0017-4933-8e7b-191ac3542fcc
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2881049ee490bf0abdd8b2f0651ca3703ccae76a
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-47"></a>.NET Framework 4.7 における再ターゲットの変更点

まれに、変更を再ターゲットすると .NET Framework 4.7 を対象として再コンパイルされるアプリに影響する場合があります。 これらは、以前のバージョンの .NET Framework を対象とするバイナリには影響を与えませんが、Version 4.7 で実行されるバイナリには影響します。 .NET Framework 4.7 には、次の領域の変更の再ターゲットが含まれます。  

-   [コア](#Core)  
-   [ASP.NET](#asp) 
-   [Windows Communication Foundation (WCF)](#WCF)  
-   [Windows Presentation Foundation (WPF)](#WPF)
 
 次の表の [スコープ] 列には、各変更の重要度を指定します。  
  
-   メジャー。 多数のアプリに影響するか、またはコードに大幅な変更が必要な、重大な変更。 変更の再ターゲットはこのカテゴリに分類されないことに注意してください。  
  
-   マイナー。 少数のアプリに影響するか、またはコードにわずかな変更が必要な、変更。  
  
-   エッジ。 一般的ではない特定のシナリオでアプリに影響を与える変更。  
  
-   透過。 アプリの開発者やユーザーには大きな影響を及ぼさない変更。 アプリはこの変更のために変更を加える必要はありません。  
  
## <a name="a-namecore--core"></a><a name="Core" /> コア

| 特性 | 変更 | 影響 | スコープ |
|----|----|----|----|
|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> | .NET Framework 4.6.2 以前のバージョンを対象とするアプリケーションは、HWND の値が存在するメモリ内の特定の場所に、<xref:System.IntPtr> になるこのプロパティに割り当てられた値を受け取ります。<br/></br>.NET Framework 4.7 を対象とするアプリ以降では、Windows フォーム アプリケーションは、次のようなコードを使用して、このプロパティの値を設定できます。 <br/><br/>` cspParameters.ParentWindowHandle = form.Handle; ` | この変更に不都合な動作を見つけたアプリは、新しい動作を無効にできます。 同様に、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.7 で実行されているアプリは、新しい動作を有効にできます。 詳細については、「[Mitigation: CspParameters.ParentWindowHandle Expects an HWND](../../../docs/framework/migration-guide/mitigation-cspparameters-parentwindowhandle-expects-an-hwnd.md)」 (軽減策: CspParameters.ParentWindowHandle で HWND を受け取る) を参照してください。 | Minor |
| <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> でのシリアル化 | .NET Framework 4.7 を対象とするアプリ以降では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> での制御文字のシリアル化が、ECMAScript V6 および V8 に準拠するようになりました。 | この変更は、ECMAScript 標準に準拠し、ほとんど影響はありません。 影響がある場合は、互換性スイッチを以前の動作を復元するために利用できます。 詳細については、「[軽減策: DataContractJsonSerializer での制御文字のシリアル化](../../../docs/framework/migration-guide/mitigation-serialization-control-characters.md)」を参照してください。  | エッジ |

## <a name="a-nameasp--aspnet"></a><a name="asp" /> ASP.NET

| 特性  |変更  |影響 | スコープ | 
---------|---------|---------|-----|
セッションあたりの同時実行される要求のスロットル | .NET Framework 4.6.2 以前では、ASP.NET は同じ <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> で順番に要求を実行し、既定では、ASP.NET は常にクッキーを使用して <xref:System.Web.SessionState.HttpSessionState.SessionID%2A> を発行します。 ページの読み込みに時間がかかる場合、ブラウザーの <kbd>F5</kbd> キーを押すと、サーバー パフォーマンスを大幅に低下させます。<br/><br/>.NET Framework 4.7 以降では、カウンターはキューに置かれた要求を追跡し、特定の制限を超えるときに要求を終了します。 既定値は 50 です。 制限に達すると、警告がイベント ログに記録され、HTTP 500 応答は IIS ログに記録される可能性があります。|この変更によって、全体のサーバー パフォーマンスを向上させることができます。<br/><br/>以前の動作を復元するには、次の設定を web.config ファイルに追加して、新しい動作を無効にできます。<br/><br/>`<appSettings>`<br/>&nbsp;&nbsp;&nbsp;`<add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>`<br/>`</appSettings>` | エッジ |

## <a name="a-namewcf--windows-communication-foundation"></a><a name="WCF" /> Windows Communication Foundation

| 特性  |変更  |影響 | スコープ | 
---------|---------|---------|-----|
| WCF メッセージ セキュリティ | .NET Framework 4.7 以降で実行されているアプリは、アプリケーションの構成設定によって WCF メッセージ セキュリティに TLS 1.1 および TLS 1.2 を使用できます。 これはオプトイン機能です。既定では、WCF メッセージ セキュリティでの TLS 1.1 および TLS 1.2 のサポートは無効です。 | WCF メッセージ セキュリティの既定の動作は、変更されていません。 <br/><br/> TLS 1.1 および TLS 1.2 サポートを有効にするには、次の構成設定を `app.config` または `web.config` ファイルの[ランタイム](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加します。  <br/><br/>`<runtime>` <br/> &nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;`<br/>&nbsp;&nbsp;&nbsp;`Switch.System.Net.DontEnableSchUseStrongCrypto=false" />`<br/>`</runtime>` | エッジ |         

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)  

| 特性 | 変更 | 影響 | スコープ |
|---|---|---|---|
| <xref:System.Windows.Controls.Grid> コントロールの *-column へのディスク領域の割り当て | .NET Framework 4.7 を対象とするアプリ以降では、WPF は <xref:System.Windows.Controls.Grid> コントロールが \*-columns.md に領域を割り当てるために使用するアルゴリズムを置き換えます。 | .NET Framework 4.7 以降の .NET Framework のバージョンを対象とするアプリケーションでは、多くの場合、この変更は \*-columns に割り当てられた実際の幅に影響します。 この変更が必要でない場合は、エントリをアプリケーション構成ファイルに追加して、以前のアルゴリズムを引き続き適用することができます。 詳細については、「[Mitigation: Grid Control's Space Allocation to Star-columns](../../../docs/framework/migration-guide/mitigation-grid-control.md)」 (軽減策: グリッド コントロールの *-column へのディスク領域の割り当て) を参照してください。 | Minor |
| <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> | .NET Framework 4.6.2 以前のバージョンを対象とするアプリケーションの場合、<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom%2A> メソッドの例外処理コードのエラーでは、目的の例外 ([DirectoryNotFoundException](assetId:///T:System.IO.DirectoryNotFoundException) または [FileNotFoundException](assetId:///T:System.IO.FileNotFoundException) など) ではなく、[NullReferenceException](assetId:///T:System.NullReferenceException) がスローされます。<br/><br/>.NET Framework 4.7 を対象とするアプリ以降では、適切な例外がスローされます。  | .NET Framework 4.7 を対象にしていて、[NullReferenceException](assetId:///T:System.NullReferenceException) の処理に依存するアプリケーションでは、`app.config` ファイルの[ランタイム](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、前の動作を復元できます。 <br/><br/>`<runtime>`<br/>&nbsp;&nbsp;&nbsp;`<AppContextSwitchOverrides value="Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true"/>`<br/>`</runtime>`| エッジ | 
| `WM_POINTER` ベースのタッチ/スタイラスのスタックのオプトイン サポート | .NET Framework 4.7 を対象とするアプリ以降では、WPF はオプションの WM_POINTER ベース タッチのサポートを追加します。  | これは、Windows 10 Creators Update 以降の Windows システムで利用できるオプトイン機能です。 ポインター ベースのタッチ/スタイラスのサポートを明示的に有効にしない WPF アプリは、影響を受けません。 詳細については、「[軽減策: ポインター ベースのタッチおよびスタイラスのサポート](../Topic/Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md)」を参照してください。 | エッジ |
| [PrintQueue](assetId:///T:System.Printing.PrintQueue) クラス | .NET Framework 4.7 以降では、[PrintQueue](assetId:///T:System.Printing.PrintQueue) を使用する WPF の印刷 API は、現在は使用されていない XPS 印刷 API ではなく、既定では、Windows Print Document Package API を呼び出します。<br/><br/>以前の印刷スタックは、以前の Windows バージョンで動作したように、引き続き動作します。 | ユーザーも開発者も、動作または API の使用の変化を目にすることはありません。 <br/><br/>Windows 10 Creators Update で以前のスタックを使用するには、`HKEY_CURRENT_USER\Software\Microsoft.NETFramework\Windows Presentation Foundation\Printing` レジストリ キーの `UseXpsOMPrinting` `REG_DWORD` 値を 1 に設定します。 | エッジ | 
## <a name="see-also"></a>関連項目
[.NET Framework 4.7 のアプリケーションの互換性](Application%20Compatibility%20in%20the%20.NET%20Framework%204.7.md)

