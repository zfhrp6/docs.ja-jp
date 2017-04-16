---
title: ".NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, トラブルシューティング (インストールのブロックの)"
  - "ブロックされた .NET Framework のインストール, トラブルシューティング"
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
caps.latest.revision: 57
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 39
---
# .NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング
.NET Framework 4.5、4.5.1、4.5.2、4.6、または 4.6.1 の [Web またはオフライン インストーラー](../../../docs/framework/install/guide-for-developers.md)を実行すると、.NET Framework のインストールを妨げたり、ブロックしたりするような問題が発生することがあります。 次の表に、インストールをブロックすることが考えられる問題と、トラブルシューティング情報へのリンクを示します。  
  
 この表で、4.5.*x* は .NET Framework 4.5、そのポイント リリースである 4.5.1、4.5.2、4.6、または 4.6.1 を指します。  
  
|ブロッキング メッセージ|詳細情報または問題解決のための参照先|  
|------------------|------------------------|  
|Microsoft .NET Framework をアンインストールすると、一部のアプリケーションが機能しなくなる可能性があります。|一般に、コンピューターにインストールされている .NET Framework のバージョンはアンインストールしないでください。使用するアプリケーションが .NET Framework の特定のバージョンに依存している可能性があるからです。 詳細については、*概要ガイド*の「[ユーザーにとっての .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)」を参照してください。|  
|.NET Framework 4.5*.x*\/4.6*.x* \(*言語*\) には、.NET Framework 4.5*.x*\/4.6*.x* が必要です。 ダウンロード センターから .NET Framework 4.5*.x*\/4.6*.x* をインストールしてセットアップを再実行します。|言語パックをインストールする前に、指定された .NET Framework リリースの英語バージョンをインストールする必要があります。 詳細については、インストール ガイドの [言語パックのインストール](../../../docs/framework/install/guide-for-developers.md#standalone_language_packs) に関するセクションを参照してください。|  
|.NET Framework 4.5*.x*\/4.6*.x* をインストールできません。 このプログラムと互換性がないアプリケーションがコンピューター上に存在します。<br /><br /> または<br /><br /> このプログラムと互換性がないアプリケーションがコンピューター上に存在します。|このメッセージは、通常 .NET Framework のプレビューまたは RC バージョンがインストールされているために表示されます。 プレビューまたは RC バージョンをアンインストールし、セットアップを再実行します。|  
|このパッケージを使用して .NET Framework 4.5*.x*\/4.6*.x* をアンインストールすることはできません。 コンピューターから .NET Framework 4.5*.x*\/4.6*.x* をアンインストールするには、**コントロール パネル**に移動して、**\[プログラムと機能\]**、**\[インストールされた更新プログラムを表示\]**、Microsoft Windows 更新プログラム \(KB2828152\) の順に選択し、**\[アンインストール\]** を選択します。|インストールしているパッケージによって、.NET Framework のプレビューまたは RC リリースはアンインストールされません。<br /><br /> コントロール パネルからプレビューまたは RC リリースをアンインストールします。|  
|.NET Framework 4.5*.x*\/4.6*.x* をアンインストールできません。 このプログラムに依存するアプリケーションがコンピューター上に存在します。|一般に、コンピューターから .NET Framework のバージョンをアンインストールしないでください。使用するアプリケーションが .NET Framework の特定のバージョンに依存している可能性があるからです。 詳細については、*概要ガイド*の「[ユーザーにとっての .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)」を参照してください。|  
|再頒布可能な .NET Framework 4.5*.x*\/4.6*.x* は、このオペレーティング システムには適用されません。 Microsoft ダウンロード センターから使用しているオペレーティング システム用の .NET Framework 4.5*.x*\/4.6*.x* をダウンロードしてください。|サポートされていないプラットフォームに [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、4.6、または 4.6.1 をインストールしようとしている可能性があります。または、サポートされているすべてのオペレーティング システム用のコンポーネントが含まれていないインストール パッケージを選択しました。 オフライン インストーラー \([4.5.1 用](http://go.microsoft.com/fwlink/p/?LinkId=309493)、[4.5.2 用](http://go.microsoft.com/fwlink/p/?LinkId=397706)、[4.6 用](http://go.microsoft.com/fwlink/p/?LinkId=528233)、または [4.6.1 用](http://go.microsoft.com/fwlink/p/?LinkId=671744)\) を使用してインストールを再実行します。 サポートされているオペレーティング システムの詳細については、「[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)」および「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
|現在、コンピューターでは Windows Server 2008 オペレーティング システムの Server Core インストールが実行されています。 .NET Framework 4.5.*x* には、新しいリリースのオペレーティング システムが必要です。 Windows Server 2008 R2 SP1 以上をインストールし、.NET Framework 4.5.*x* セットアップを再実行してください。|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] および 4.5.2 は、Windows Server 2008 R2 SP1 以降の Server Core ロールでサポートされています。 「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
|特権が不十分なため、このコンピューターのすべてのユーザーが使用できるようにセットアップを完了できません。 管理者としてログオンし、**セットアップ**を再度実行してください。|.NET Framework をインストールするには、そのコンピューターの管理者である必要があります。|  
|前のインストールを完了するためにコンピューターの再起動が必要であるため、セットアップを続行できません。 コンピューターを再起動し、セットアップを再度実行してください。|インストールを完了するために、再起動が必要な場合があります。 手順に従って、コンピューターを再起動し、セットアップを再実行します。|  
|.NET Framework 4.5*.x*\/4.6*.x* \(ENU\) 以降の更新プログラムがコンピューターに既にインストールされています。|アクションは必要ありません。|  
|.NET Framework Setup cannot be run in Program Compatibility Mode. \(プログラム互換性モードで .NET Framework セットアップを実行できません。\)|この記事で後述する「[プログラムの互換性問題](#compat)」セクションを参照してください。|  
|.NET Framework 4.5*.x*\/4.6*.x* は、コンポーネント ストアが破損しているためにインストールされませんでした。|詳細については、「[DISM またはシステム更新準備ツールを使用して Windows Update のエラーを修正する](https://support.microsoft.com/en-us/kb/947821)」を参照してください。|  
|Setup cannot run because the Windows Installer Service is not available on this computer. \(このコンピューターには利用できる Windows インストーラー サービスがないため、セットアップは実行できません。\)|Microsoft サポート オンラインの「[プログラムをインストールまたは更新するときの Windows インストーラー サービス エラー](http://go.microsoft.com/fwlink/p/?LinkId=248684)」を参照してください。|  
|Setup may not run properly because the Windows Update Service is not available on this computer. \(このコンピューターには利用できる Windows Update サービスがありません。セットアップは正しく実行されない可能性があります。\)|管理者によって、コンピューターが Microsoft Windows Update ではなく Windows Server Update Services \(WSUS\) を使用するように設定されています。 詳細については、「[Windows 8 または Windows Server 2012 で NET Framework 3.5 をインストールしようとするとエラー コードが表示される](http://support.microsoft.com/kb/2734782)」のエラー コード 0x800F0906 に関するセクションを参照してください。<br /><br /> Microsoft サポート オンラインの「[最新版の Windows Update エージェントの入手方法](http://go.microsoft.com/fwlink/p/?LinkId=248437)」も参照してください。|  
|Setup may not run properly because the Background Intelligent Transfer Service \(BITS\) is not available on this computer. \(このコンピューターには利用できる Background Intelligent Transfer Service \(BITS\) がありません。セットアップは正しく実行されない可能性があります。\)|Microsoft サポート オンラインの「[Windows Vista ベースのコンピューターでバックグラウンド インテリジェント転送サービス \(BITS\) のクラッシュを防止する更新プログラム](http://go.microsoft.com/fwlink/p/?LinkId=248680)」を参照してください。|  
|.NET Framework 4.5.*.x*\/4.6 は、すでにこのオペレーティング システムの一部です。 再頒布可能な .NET Framework 4.5*.x*\/4.6 をインストールする必要はありません。|アクションなし。 サポートされているオペレーティング システム用の「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
|.NET Framework 4.5*.x*\/4.6*.x* は、このオペレーティング システムではサポートされていません。|サポートされているオペレーティング システム用の「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。<br /><br /> Windows 7 での .NET Framework のインストールに失敗した場合、通常このメッセージは Windows 7 SP1 がインストールされていないことを示します。 Windows 7 システムでは、.NET Framework には Windows 7 SP1 が必要です。 Windows 7 を使用していて Service Pack 1 をインストールしていない場合、.NET Framework をインストールする前に、Service Pack 1 をインストールする必要があります。|  
|Your computer is currently running a Server Core installation of Windows Server 2008 operating system. \(現在、コンピューターでは Windows Server 2008 オペレーティング システムの Server Core インストールが実行されています。\) .NET Framework 4.5.*x* には、オペレーティング システムまたは Server Core 2008 R2 SP1 の完全なリリースが必要です。 Windows Server 2008 SP2、Windows Server 2008 R2 SP1、Server Core 2008 R2 SP1 のいずれかの完全バージョンをインストールして、.NET Framework 4.5.*x* セットアップを再実行してください。|.NET Framework は、Windows Server 2008 R2 SP1 以降の Server Core ロールでサポートされています。 「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
|.NET Framework 4.5.*x* は既にこのオペレーティング システムの一部として組み込まれていますが、現在は無効になっています \([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] のみ\)。|Windows Web サイトの「[Windows の機能を有効化または無効化する](http://go.microsoft.com/fwlink/p/?LinkId=248438)」を参照してください。|  
|このセットアップ プログラムは x86 コンピューターのみを対象としています。 x64 コンピューターまたは IA64 コンピューターにはインストールできません。|MSDN ライブラリの「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
|このセットアップ プログラムは x64 コンピューターまたは x86 コンピューターのみを対象としています。 IA64 コンピューターにはインストールできません。|MSDN ライブラリの「[システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。|  
  
<a name="compat"></a>   
### プログラムの互換性問題  
 .NET Framework 4.5 またはそのポイント リリースのインストールを Windows プログラム互換性モードで実行すると、1603 エラー コードで失敗するか、ブロックされます。**プログラム互換性アシスタント**には、.NET Framework が正しくインストールされていない可能性が示され、推奨設定を使用して再インストールするよう求められます \(プログラム互換性モード\)。 プログラム互換性モードは、以前の .NET Framework セットアップの実行が失敗するか取り消されたときにプログラム互換性アシスタントによって設定されている可能性もあります。  
  
 プログラム互換性モードで .NET Framework インストーラーを実行できません。 このブロッキング問題を解決するには、レジストリ エディターでシステム全体での互換性モードの設定が無効になっていることを確認する必要があります。  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** を選択します。  
  
2.  **\[ファイル名を指定して実行\]** ダイアログ ボックスで、「`regedit`」と入力し、**\[OK\]** をクリックします。  
  
3.  レジストリ エディターで、次のサブキーを参照します。  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Compatibility Assistant\\Persisted  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Layers  
  
4.  名前の列で、インストールしているバージョンに応じて [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、4.5.1、4.5.2、4.6、または 4.6.1 のダウンロード名を検索し、これらのエントリを削除します。 ダウンロード名については、「[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)」の記事を参照してください。  
  
5.  バージョン 4.5、4.5.1、4.5.2、4.6、または 4.6.1 の .NET Framework インストーラーを再実行します。  
  
## 参照  
 [インストール ガイド](../../../docs/framework/install/guide-for-developers.md)