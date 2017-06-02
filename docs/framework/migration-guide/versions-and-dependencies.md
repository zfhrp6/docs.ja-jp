---
title: ".NET Framework のバージョンおよび依存関係 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
caps.latest.revision: 122
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fe9ab371ab8d3eee3778412e446b7aa30b42476b
ms.openlocfilehash: ec15e14b299b5bed46d8d35a8c60e5f73a1d5237
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework のバージョンおよび依存関係
.NET Framework の各バージョンには、共通言語ランタイム (CLR)、基底クラス ライブラリ、およびその他のマネージ ライブラリが含まれています。 このトピックでは、.NET Framework の各バージョンの主要な機能について説明し、基になっている CLR のバージョンおよび関連する開発環境に関する情報と、Windows オペレーティング システムでインストールされる .NET Framework のバージョンを示します。  
  
> [!NOTE]
>  .NET Framework のダウンロードとインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
 次の表に、.NET Framework のバージョン履歴を要約し、各バージョンと Visual Studio、Windows、および Windows Server との関係を示します。 Visual Studio ではマルチターゲット機能が提供されているため、記載されている .NET Framework のバージョンに限定される必要はありません。  
  
 新しい各バージョンの .NET Framework には、1 つ前のバージョンの機能が含まれると共に、新機能が追加されています。 CLR は独自のバージョン番号で識別されます。 .NET Framework のバージョン番号はリリースごとにインクリメントされますが、CLR のバージョンは必ずしもインクリメントされるわけではありません。 たとえば、.NET Framework 4、4.5、およびそれ以降のリリースには CLR 4 が含まれますが、.NET Framework 2.0、3.0、3.5 には CLR 2.0 が含まれます。 (CLR の Version 3 はありません)。  
  
 サポートされるオペレーティング システムの全一覧については、[システム要件](../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。 ダウンロードについては、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。 コンピューターにインストールされている .NET Framework のバージョンを確認する方法については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。  
  
 次の表の "**このバージョンを含む/インストール可能な Windows**" 列および "**このバージョンを含む/インストール可能な Windows Server**" 列に ✓マークが付いているオペレーティング システム バージョンにインストールされている .NET Framework のバージョンを、[コントロール パネルで有効にする](../../../docs/framework/install/dotnet-35-windows-10.md) (Windows の場合) かサーバー マネージャーで有効にする (Windows Server の場合) 必要があります。  
  
|.NET Framework のバージョン|CLR バージョン|フィーチャー|Visual Studio バージョンに含まれる|✓ このバージョンを含む製品<br />+ インストール可能<br />Windows|✓ このバージョンを含む製品<br />+ インストール可能<br />Windows Server|インストールされた .NET バージョンを確認するには|  
|----------------------------|-----------------|--------------|---------------------------------------|----------------------------------------------------|-----------------------------------------------------------|-----------------------------------------| 
|.NET 4.7|4|- オペレーティング システムによって提供されるレベルの TLS サポートに対応。<br/> - TLS1.1 または TLS1.2 の既定のメッセージ セキュリティ設定を構成する機能。 <br /> - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> の信頼性の向上。 <br /> - WCF アプリケーションでのシリアル化と逆シリアル化の信頼性の向上。 <br /> - ASP.NET オブジェクト キャッシュの拡張機能。 <br /> - WPF アプリケーション用の Windows Ink Services Platform (WISP) に代わる `WM_POINTER` Windows メッセージに基づくタッチ/スタイラス スタックのサポート。 <br /> - Windows Print Document Package API を使用した WPF アプリケーションでの印刷。<br /> - 拡張された高 DPI およびマルチ モニターによる Windows 10 Creators Update で実行される Windows フォーム アプリケーションのサポート。 | | ✓ 10 Creators Update <br/> <br/> + 10 Anniversary Update <br/> + 8.1 <br/> +7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |`Release` DWORD を使用:<br/><br/> - 460798 (Windows 10 Creators Update) <br/> - 460805 (その他すべての OS バージョン) <br/><br/> ([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照) |  
|.NET 4.6.2|4|- 暗号化の機能強化。FIS 186-3 DSA を含む X509 証明書のサポート、保存されたキーの対称暗号化のサポート、SHA-2 のハッシュの <xref:System.Security.Cryptography.Xml.SignedXml> サポートが含まれます。また、ECDiffieHellman キー派生ルーチンへの入力がわかりやすくなりました。<br />- Windows Presentation Foundation (WPF) アプリでのソフト キーボードのサポートおよびモニターごとの DPI。<br />- TLS 1.1 プロトコルと TLS 1.2 プロトコルでの ClickOnce のサポート。<br />- Windows フォームおよび WPF アプリの UWP アプリへの変換のサポート。||✓  10 Anniversary Update<br /><br /> + 8.1<br />+ 7|✓ 2016<br /><br /> + 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|`Release` DWORD を使用:<br /><br /> - 394802 (Windows 10 Anniversary Update)<br />- 394806 (その他すべての OS バージョン)<br /><br /> ([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
|.NET 4.6.1|4|- ECDSA を含む X509 証明書のサポート<br />- ADO.NET のハードウェア保護キーに対する Always Encrypted のサポート<br />- WPF におけるスペル チェック機能の向上<br />-   [その他...](../../../docs/framework/whats-new/index.md)||✓  10 の 11 月の更新プログラム<br /><br /> + 10<br />+ 8.1<br />+ 8<br />+ 7|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|`Release` DWORD を使用:<br /><br /> - 394254 (Windows 10 November Update)<br />- 394271 (その他すべての OS バージョン)<br /><br /> ([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
|.NET 4.6|4|- .NET ネイティブによるコンパイル<br />- ASP.NET Core 5<br />- イベント トレーシング機能の強化<br />- ページのエンコーディングのサポート<br />-   [その他...](../../../docs/framework/whats-new/index.md)|2015。ただし、一部の .NET ライブラリは、[NuGet](https://www.nuget.org/) から入手できます。 詳細については、「[.NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)」を参照してください。|✓ 10<br />+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD を使用:<br /><br /> - 393295 (Windows 10)<br />- 393297 (その他すべての OS バージョン)<br /><br /> ([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
|4.5.2|4|- トランザクション システムと ASP.NET 用の API の新規追加<br />- Windows フォーム コントロールでのシステム DPI のサイズ変更<br />- プロファイリングの機能強化<br />- ETW およびストレス ログの改善<br />-   [その他...](../../../docs/framework/whats-new/index.md)|-|+ 8.1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD を使用: 379893<br />([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
.5.1|4|- Windows Phone ストア アプリのサポート<br />- 自動バインド リダイレクト<br />- パフォーマンスとデバッグの改善<br />-   [その他...](../../../docs/framework/whats-new/index.md)|2013|✓ 8.1<br />+ 8<br />+ 7<br />+ Vista|✓ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD を使用:<br /><br /> - 378675 (Windows 8.1)<br />- 378758 (その他)<br /><br /> ([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
|4.5|4|- Windows ストア アプリのサポート<br />- WPF、WCF、WF、ASP.NET の更新<br />-   [その他...](../../../docs/framework/whats-new/index.md)|2012|✓ 8<br />+ 7<br />+ Vista|✓ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|`Release` DWORD を使用: 378389<br />([手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照)|  
|4|4|- 基底クラス ライブラリの拡張<br />- ポータブル クラス ライブラリによるクロスプラットフォームでの開発<br />- MEF、DLR、コード コントラクト<br />-   [その他...](http://msdn.microsoft.com/library/ms171868\(v=vs.100\).aspx)|2010|+ 7<br />+ Vista|+ 2008 R2 SP1<br />+ 2008 SP2<br />+ 2003|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
|3.5|2.0|- AJAX 対応の Web サイト<br />- LINQ<br />- 動的データ<br />-   [その他...](http://msdn.microsoft.com/library/ms171868\(v=vs.90\).aspx)|2008|✓ 10✓ 8.1*<br />✓ 8\*<br />✓ 7<br />+ Vista|✓ 2008 R2 SP1*<br />+ 2012 R2<br />+ 2012<br />+ 2008 SP2<br />+ 2003|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
|3.0|2.0|- WPF、WCF、WF、CardSpace|-|✓ Vista|✓ 2008 R2 SP1*<br />✓ 2008 SP2\*<br />+ 2003|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
|2.0|2.0|- ジェネリック<br />- ASP.NET の機能追加<br />-   [その他...](http://msdn.microsoft.com/library/t357fb32\(v=vs.80\).aspx)|2005|-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
|1.1|1.1|- ASP.NET と ADO.NET の更新<br />- side-by-side 実行<br />-   [その他...](http://msdn.microsoft.com/library/9wtde3k4\(v=vs.80\).aspx)|2003|-|✓ 2003|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
|1.0|1.0|.NET Framework の最初のバージョン。|Visual Studio .NET|-|-|[手順](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)に関するページを参照|  
  
 一般に、コンピューターにインストールされている .NET Framework のバージョンはアンインストールしないでください。使用するアプリケーションが特定のバージョンに依存しており、バージョンが削除されると破損する可能性があるからです。 1 台のコンピューターに複数バージョンの .NET Framework を同時に読み込むことができます。 これは、以前のバージョンをアンインストールすることなく、.NET Framework をインストールできることを意味します。 詳細については、[概要](../../../docs/framework/get-started/index.md)に関するページを参照してください。  
  
## <a name="targeting-and-running-net-framework-apps-for-version-45-and-later"></a>.NET Framework 4.5 以降のバージョンをターゲットにして実行する  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] はコンピューターの [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を置き換えるインプレース更新であり、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 4.5.2、4.6、4.6.1、4.6.2、4.7 は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] のインプレース更新です。つまり、同じバージョンのランタイムを使用しますが、アセンブリのバージョンが更新され、新しい型とメンバーが含まれます。 これらの更新プログラムのいずれかをインストールした後、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] アプリ、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] アプリ、または [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] アプリは再コンパイルせずに実行を継続します。 ただし、逆はできません。 .NET Framework の新しいバージョンをターゲットとするアプリを .NET Framework の以前のバージョンで実行することは推奨されていません。 たとえば、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] をターゲットとするアプリを [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で実行することは推奨されていません。 次のガイドラインが適用されます。  
  
-   Visual Studio で、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] をプロジェクトのターゲット フレームワークとして選択して (これにより <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=fullName> プロパティが設定されます)、プロジェクトを [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] アセンブリまたは実行可能ファイルとしてコンパイルできます。 このアセンブリまたは実行可能ファイルは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、4.5.1、4.5.2、4.6、4.6.1、4.6.2、または 4.7 がインストールされているコンピューターで使用できます。  
  
-   Visual Studio で、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] をプロジェクトのターゲット フレームワークとして選択して (これにより <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=fullName> プロパティが設定されます)、プロジェクトを [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] アセンブリまたは実行可能ファイルとしてコンパイルできます。 このアセンブリまたは実行可能ファイルは [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] かそれ以降のバージョンの .NET Framework がインストールされているコンピューターでのみ実行する必要があります。 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象とする実行可能ファイルは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] など、初期バージョンの .NET Framework のみがインストールされたコンピューターでは実行がブロックされ、ユーザーに [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] のインストールを求めるメッセージが表示されます。 また、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] アセンブリは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] など、初期バージョンの .NET Framework を対象とするアプリから呼び出さないでください。  
  
     ここで使用されている [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] と [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は単なる例にすぎません。 この原則は、実行されているシステムにインストールされているものより新しい .NET Framework のバージョンをターゲットにするアプリに適用されます。  
  
 .NET Framework の変更により、アプリケーション コードの変更が必要な場合があります。既存のアプリケーションを [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] またはそれ以降のバージョンで実行する前に、[アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)に関するページを参照してください。 現行バージョンのインストールについては、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。 .NET Framework のサポートの詳細については、Microsoft サポート オンラインの [Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/?LinkId=196607)に関するページを参照してください。  
  
## <a name="targeting-and-running-apps-for-older-versions"></a>以前のバージョンのアプリの対象化と実行  
 .NET Framework 2.0、3.0 および 3.5 は、同じバージョンの CLR (CLR 2.0) でビルドされています。 これらのバージョンは 1 つのインストールの連続したレイヤーを表します。 各バージョンは、以前のバージョンの上にインクリメンタル方式でビルドされます。 コンピューターでバージョン 2.0、3.0、および 3.5 を side-by-side で実行することはできません。 バージョン 3.5 をインストールすると、2.0 と 3.0 のレイヤーが自動的に取得され、バージョン 2.0、3.0、および 3.5 を対象としてビルドされたアプリケーションはすべて、バージョン 3.5 で実行できます。 ただし、.NET Framework 4 でこのレイヤーのアプローチは終了しています。 NET Framework 4 以降では、インプロセスの side-by-side ホスティングを使用して、1 つのプロセスで複数のバージョンの CLR を実行できます。 詳細については、「[アセンブリと side-by-side 実行](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)」を参照してください。  
  
 さらに、アプリケーションがバージョン 2.0、3.0、または 3.5 を対象とする場合、ユーザーがアプリケーションを実行する前に、[!INCLUDE[win8](../../../includes/win8-md.md)] または [!INCLUDE[win81](../../../includes/win81-md.md)] のコンピューター上で .NET Framework 3.5 を有効にするように求められる場合があります。 詳細については、[Windows 10、Windows 8.1、Windows 8 への .NET Framework 3.5 のインストール](../../../docs/framework/install/dotnet-35-windows-10.md)に関するページを参照してください。  
  
## <a name="next-steps"></a>次のステップ  
  
-   .NET Framework を初めて使用する場合は、[概要](../../../docs/framework/get-started/overview.md)に関するページを参照して、主な概念と機能の概要を確認してください。  
  
-   [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] とポイント リリースでの新機能と機能強化については、「[.NET Framework の新機能](../../../docs/framework/whats-new/index.md)」を参照してください。  
  
-   .NET Framework 4 から [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] およびそのポイント リリースへのアプリの移行の詳細については、[移行ガイド](../../../docs/framework/migration-guide/index.md)に関するページを参照してください。  
  
-   コンピューターにどのバージョンまたは更新プログラムがインストールされているかを判別する方法については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」と「[方法: インストールされている .NET Framework の更新プログラムを確認する](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

[バージョンの互換性](../../../docs/framework/migration-guide/version-compatibility.md)   
[Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/?LinkId=196607)   
[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)

