---
title: "アプリケーションの起動時間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーションの起動 [WPF]"
  - "パフォーマンス [WPF], 起動時間"
  - "スプラッシュ スクリーン [WPF], 起動時間"
  - "起動時間 [WPF]"
  - "WPF, 起動時間"
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# アプリケーションの起動時間
WPF アプリケーションの起動に必要な時間は、大幅に変動する可能性があります。  このトピックでは、Windows Presentation Foundation \(WPF\) アプリケーションの認識される起動時間と実際の起動時間を短縮する方法について説明します。  
  
## コールド スタートとウォーム スタートについて  
 コールド スタートは、システムの再起動後にアプリケーションを初めて起動するとき、またはアプリケーションを起動して閉じた後、時間をおいて再び起動するときに発生します。  アプリケーションが起動するときに、必要なページ \(コード、静的データ、レジストリなど\) が Windows メモリ マネージャーのスタンバイ リストに存在しない場合、ページ フォールトが発生します。  これらのページをメモリに読み込むには、ディスクにアクセスする必要があります。  
  
 ウォーム スタートは、主要な共通言語ランタイム \(CLR: Common Language Runtime\) コンポーネント用のページのほとんどが、既にメモリに読み込まれているときに発生し、貴重なディスク アクセス時間が節約されます。  このため、マネージ アプリケーションを再度実行すると、初回よりも短い時間で起動します。  
  
## スプラッシュ スクリーンの実装  
 アプリケーションの起動から最初の UI が表示されるまでにかなりの時間がかかることが避けられない場合は、*スプラッシュ スクリーン*を使用することで、認識される起動時間を最適化します。  この方法により、ユーザーがアプリケーションを起動すると、すぐにイメージが表示されます。  アプリケーションが最初の UI を表示する準備が整うと、スプラッシュ スクリーンはフェード アウトします。  [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 以降、<xref:System.Windows.SplashScreen> クラスを使用して、スプラッシュ スクリーンを実装できます。  詳細については、「[スプラッシュ スクリーンを WPF アプリケーションに追加する](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)」を参照してください。  
  
 ネイティブな Win32 グラフィックスを使用することで、独自のスプラッシュ スクリーンを実装することもできます。  独自の実装は、<xref:System.Windows.Application.Run%2A> メソッドが呼び出される前に表示します。  
  
## 起動コードの分析  
 コールド スタートに時間がかかる理由を特定します。  ディスク I\/O が原因である可能性がありますが、常にそうとは限りません。  通常は、ネットワーク、Web サービス、ディスクなどの外部リソースの使用を最小限に抑えてください。  
  
 テストを始める前に、実行中のアプリケーションやサービスが、マネージ コードまたは WPF コードを使用していないことを確認してください。  
  
 再起動したら、直ちに WPF アプリケーションを起動し、表示されるまでの時間を計測します。  この後、同じアプリケーションを複数回起動し \(ウォーム スタート\)、各回の起動時間が初回よりも短ければ、コールド スタートの問題の原因は I\/O であると判断できます。  
  
 アプリケーションのコールド スタートの問題に I\/O が無関係である場合は、アプリケーションが長時間かかる初期化や計算を実行しているか、イベントの完了を待機しているか、起動時に大量の JIT コンパイルを必要としている可能性があります。  以下のセクションでは、これらの状況のいくつかについてさらに詳しく説明します。  
  
## モジュールの読み込みの最適化  
 プロセス エクスプローラー \(Procexp.exe\) や Tlist.exe などのツールを使用して、アプリケーションが読み込むモジュールを調べます。  `Tlist <pid>` コマンドは、プロセスによって読み込まれるすべてのモジュールを表示します。  
  
 たとえば、Web に接続しないにもかかわらず System.Web.dll が読み込まれている場合は、アプリケーション内にこのアセンブリを参照するモジュールが含まれています。  この参照が本当に必要かどうかを検討します。  
  
 アプリケーションに複数のモジュールがある場合は、それらをマージして単一のモジュールにします。  この方法により、CLR によるアセンブリ読み込みのオーバーヘッドが減少します。  アセンブリ数の減少は、CLR が管理する状態も減少することも意味します。  
  
## 初期化処理の延期  
 メイン アプリケーション ウィンドウが表示されるまで初期化コードの実行を延期することを考慮します。  
  
 初期化はクラス コンストラクター内で実行される場合があり、初期化コードが他のクラスを参照している場合は、多数のクラス コンストラクターが次々に実行される可能性があることに注意してください。  
  
## アプリケーションの構成の回避  
 アプリケーションの構成を回避することを考慮します。  たとえば、アプリケーションの構成要件が単純であるときに、非常に短時間で起動する必要がある場合は、起動時間を短縮する方法として、構成の代わりにレジストリ エントリまたは単純な INI ファイルを使用できます。  
  
## GAC の活用  
 アセンブリがグローバル アセンブリ キャッシュ \(GAC: Global Assembly Cache\) にインストールされていない場合、厳密な名前付きアセンブリのハッシュ検証と Ngen イメージ検証 \(コンピューター上のネイティブ イメージを使用できる場合\) が原因で遅延が発生します。  厳密な名前の検証は、GAC にインストールされているアセンブリに対してはスキップされます。  詳細については、「[Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md)」を参照してください。  
  
## Ngen.exe の使用  
 アプリケーションでのネイティブ イメージ ジェネレーター \(Ngen.exe\) の使用を考慮します。  Ngen.exe の使用は、CPU 消費が減少する代わりにディスク アクセスが増えることを意味します。これは、Ngen.exe によって生成されるネイティブ イメージの方が、MSIL イメージよりも容量が大きい場合が多いためです。  
  
 ウォーム スタートの起動時間を短縮するには、アプリケーションで Ngen.exe を常に使用します。これは、アプリケーション コードの JIT コンパイルにかかる CPU コストを回避するためです。  
  
 コールド スタートの場合も、Ngen.exe を使用すると有効なことがあります。  これは、JIT コンパイラ \(mscorjit.dll\) を読み込む必要がないためです。  
  
 Ngen と JIT モジュールを併用すると、最悪の影響が生じる可能性があります。  これは、mscorjit.dll を読み込む必要があることに加え、JIT コンパイラがアプリケーション コードを処理するためにアセンブリのメタデータを読み込む際に、Ngen イメージ内の多数のページにアクセスする必要があるためです。  
  
### Ngen と ClickOnce  
 アプリケーションの配置方法も、読み込み時間に影響する可能性があります。  [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] によるアプリケーションの配置では、Ngen のサポートはありません。  アプリケーションで Ngen.exe を使用する場合は、Windows インストーラーなどの他の配置機構を使用する必要があります。  
  
 詳細については、「[Ngen.exe \(ネイティブ イメージ ジェネレーター\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)」を参照してください。  
  
### ベース変更と DLL アドレスの衝突  
 Ngen.exe を使用する場合は、ネイティブ イメージがメモリに読み込まれる際にベース変更が発生する可能性があることに注意してください。  希望するベース アドレスに DLL を読み込もうとしたときに、そのアドレス範囲が既に割り当て済みであるために DLL を読み込めない場合、Windows ローダーは、その DLL を別のアドレスに読み込みます。これは時間がかかる処理になる可能性があります。  
  
 仮想アドレス ダンプ \(Vadump.exe\) ツールを使用して、すべてのページがプライベートであるモジュールが存在するかどうかを調べることができます。  これに該当する場合、そのモジュールは、別のアドレスにベース変更されている可能性があります。  したがって、それらのページは共有できません。  
  
 ベース アドレスを設定する方法の詳細については、「[Ngen.exe \(ネイティブ イメージ ジェネレーター\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)」を参照してください。  
  
## Authenticode の最適化  
 Authenticode 検証によって起動時間は長くなります。  Authenticode 署名があるアセンブリは、証明機関 \(CA: Certification Authority\) を使用して検証する必要があります。  この検証では、最新の証明書失効リストをダウンロードするためにネットワークに複数回接続する必要があるので、時間がかかる可能性があります。  検証では、信頼できるルートに至るパス上の証明書がすべて有効であることも確認します。  これにより、アセンブリの読み込み中に、数秒間の遅延が発生します。  
  
 CA 証明書をクライアント コンピューターにインストールするか、可能な場合は Authenticode を使用しないことを考慮します。  アプリケーションが発行者の証拠を必要としないことが明らかな場合は、署名を検証する手間をかける必要はありません。  
  
 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 以降、Authenticode 検証のバイパスを可能にする構成オプションが用意されています。  これを行うには、次の設定を app.exe.config ファイルに追加します。  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 詳細については、「[\<generatePublisherEvidence\> 要素](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)」を参照してください。  
  
## Windows Vista でのパフォーマンスの比較  
 Windows Vista のメモリ マネージャーには、SuperFetch というテクノロジが組み込まれています。  SuperFetch は、時間の経過に伴うメモリ使用パターンを分析して、特定のユーザーに適したメモリの内容を決定し、  その内容を常に維持するように動作します。  
  
 これは、Windows XP で使用されているプリフェッチ手法とは異なります。プリフェッチでは、使用パターンを分析せずに、データをメモリにプリロードします。  ユーザーが WPF アプリケーションを Windows Vista で頻繁に使用する場合、時間の経過と共に、アプリケーションのコールド スタートの起動時間が短縮される可能性があります。  
  
## AppDomains の効率的な使用  
 可能な場合はアセンブリをドメイン中立コード領域に読み込み、ネイティブ イメージが存在するのであれば、アプリケーションで作成されるすべての AppDomains でそのネイティブ イメージが使用されるようにします。  
  
 最大限のパフォーマンスを得るには、ドメイン間呼び出しを減らしてドメイン間通信を効率化します。  可能であれば、引数のない呼び出し、または引数がプリミティブ型である呼び出しを使用します。  
  
## NeutralResourcesLanguage 属性の使用  
 <xref:System.Resources.NeutralResourcesLanguageAttribute> を使用して、<xref:System.Resources.ResourceManager> のニュートラル カルチャを指定します。  この方法を使用すると、アセンブリのルックアップの失敗が回避されます。  
  
## シリアル化での BinaryFormatter クラスの使用  
 シリアル化を使用する必要がある場合は、<xref:System.Xml.Serialization.XmlSerializer> クラスの代わりに <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスを使用します。  <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスは、mscorlib.dll アセンブリの基本クラス ライブラリ \(BCL: Base Class Library\) に実装されます。  <xref:System.Xml.Serialization.XmlSerializer> は System.Xml.dll アセンブリに実装されますが、追加の DLL が読み込まれる場合があります。  
  
 <xref:System.Xml.Serialization.XmlSerializer> クラスを使用する必要がある場合は、シリアル化アセンブリを事前に生成することで、パフォーマンスを向上させることができます。  
  
## 起動後に更新プログラムをチェックする ClickOnce の構成  
 アプリケーションで [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] を使用する場合は、アプリケーションの起動後に配置サイトの更新プログラムをチェックするように [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] を構成することで、ネットワーク アクセスを回避します。  
  
 XAML ブラウザー アプリケーション \(XBAP: XAML Browser Application\) モデルを使用する場合、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] は、XBAP が既に [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] のキャッシュに存在する場合でも、配置サイトの更新プログラムのチェックが行われることに注意してください。  詳細については、「[ClickOnce のセキュリティと配置](../Topic/ClickOnce%20Security%20and%20Deployment.md)」を参照してください。  
  
## PresentationFontCache サービスの自動起動の構成  
 再起動後に最初に実行される WPF アプリケーションは PresentationFontCache サービスです。  このサービスは、システム フォントをキャッシュしてフォント アクセスを高速化することで、全体のパフォーマンスを向上させます。  このサービスの起動にはオーバーヘッドが伴うので、一部の制御された環境では、システムの再起動時にこのサービスを自動起動するように構成することを考慮します。  
  
## データ バインディングのプログラムによる設定  
 XAML を使用してメイン ウィンドウの <xref:System.Windows.FrameworkElement.DataContext%2A> を宣言によって設定する代わりに、<xref:System.Windows.Application.OnActivated%2A> メソッドでプログラムによって設定することを考慮します。  
  
## 参照  
 <xref:System.Windows.SplashScreen>   
 <xref:System.AppDomain>   
 <xref:System.Resources.NeutralResourcesLanguageAttribute>   
 <xref:System.Resources.ResourceManager>   
 [スプラッシュ スクリーンを WPF アプリケーションに追加する](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)   
 [Ngen.exe \(ネイティブ イメージ ジェネレーター\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)   
 [\<generatePublisherEvidence\> 要素](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)